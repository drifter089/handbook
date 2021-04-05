---
layout: handbook-page-toc
title: "Data Team Platform"
description: "GitLab Data Team Platform"
---

## On this page
{:.no_toc .hidden-md .hidden-lg}

- TOC
{:toc .toc-list-icons .hidden-md .hidden-lg}

{::options parse_block_html="true" /}

---

## <i class="fas fa-map-marked-alt fa-fw" style="color:rgb(107,79,187); font-size:.85em" aria-hidden="true"></i>Quick Links

- [Sisense (Periscope)](/handbook/business-technology/data-team/platform/periscope)
- [dbt Guide](/handbook/business-technology/data-team/platform/dbt-guide)
- [Enterprise Data Warehouse](/handbook/business-technology/data-team/platform/edw)
- [Data Infrastructure](/handbook/business-technology/data-team/platform/infrastructure)
- [SQL Style Guide](/handbook/business-technology/data-team/platform/sql-style-guide)
- [Python Guide](/handbook/business-technology/data-team/platform/python-guide)
- [Permifrost](/handbook/business-technology/data-team/platform/permifrost)
- [Snowplow](/handbook/business-technology/data-team/platform/snowplow)
- [Data CI Jobs](/handbook/business-technology/data-team/platform/ci-jobs)
- [Sisense Style Guide](/handbook/business-technology/data-team/platform/sisense-style-guide)

## <i class="fas fa-cubes fa-fw" style="color:rgb(252,109,38); font-size:.85em" aria-hidden="true"></i>Our Data Stack

![Enterprise Data Platform](/handbook/business-technology/data-team/platform/enterprise_data_platform.png)

We use GitLab to operate and manage the analytics function.
Everything starts with an issue.
Changes are implemented via merge requests, including changes to our pipelines, extraction, loading, transformations, and parts of our analytics.

| Stage           |              Tool             |
| :-------------- | :---------------------------: |
| Extraction      |  Stitch, Fivetran, and Custom |
| Loading         |  Stitch, Fivetran, and Custom |
| Orchestration   |            Airflow            |
| Storage         |           Snowflake           |
| Transformations |     dbt and Python scripts    |
| Analysis        | Sisense For Cloud Data Teams‎ |

## <i class="fas fa-exchange-alt fa-fw" style="color:rgb(107,79,187); font-size:.85em" aria-hidden="true" id="extract-and-load"></i>Extract and Load

We currently use [Stitch](https://www.stitchdata.com) and [Fivetran](https://fivetran.com/) for most of our data sources. These are off-the-shelf ELT tools that remove the responsibility of building, maintaining, or orchestrating the movement of data from some data sources into our Snowflake data warehouse. We run a full-refresh of all of our Stitch/Fivetran data sources at the same time that we rotate our security credentials (approx every 90 days). Prior to running a full refresh we will drop all of the tables.

For source ownership please see [the Tech Stack Applications sheet (internal only).](https://docs.google.com/spreadsheets/d/1mTNZHsK3TWzQdeFqkITKA0pHADjuurv37XMuHv12hDU/edit#gid=0)

**Key**
- Pipeline: The technology we use to replicate data.
- RF (Replication Frequency): How often we load new and updated data.
- Raw Schema: The schema in the `RAW` database where data is stored.
- Prep Schema: The schema in the `PREP` database where [source models](/handbook/business-technology/data-team/platform/dbt-guide/#source-models) are materialized.
- Audience: The primary users of the data.
- SLO: Service Level Objective. Our SLO is the time between real-time and the analysis displayed in the [data visualization tool](#visualization)
- `x` indicates undefined or not run

| Data Source | Pipeline | Raw Schema | Prep Schema | Audience | RF / SLO|
|------------:|:--------:|:---------:|:--------:|:-------:|:--------:|
| [Airflow](https://airflow.apache.org/) | [Stitch](https://www.stitchdata.com/) | `airflow_stitch` | `airflow` |  Data Team | 9h / 9h |
| [BambooHR](https://www.bamboohr.com/) | [Airflow](https://airflow.gitlabdata.com/home) | `bamboohr` | `sensitive` | People | 12h / 24h |
| Clearbit | x | x | x | x / x |
| [CustomersDot](https://customers.gitlab.com/plans) [ERD](https://gitlab.com/gitlab-org/customers-gitlab-com/-/blob/staging/doc/db_erd.pdf) | [pgp](https://gitlab.com/gitlab-data/analytics/-/tree/master/extract/postgres_pipeline) | `tap_postgres` | `customers` | Product | 24h / x |
| [Gitter](https://gitter.im/) | x | `gitter` | x | x | x |
| GitLab.com | [pgp](https://gitlab.com/gitlab-data/analytics/-/tree/master/extract/postgres_pipeline) | `tap_postgres` | `gitlab_dotcom` | Product, Engineering | 6h / x |
| GitLab Ops DB | [pgp](https://gitlab.com/gitlab-data/analytics/-/tree/master/extract/postgres_pipeline) | `tap_postgres` | `gitlab_ops` | Engineering | 6h / x |
| GitLab Profiler DB | x | x | x | x | x / x |
| [Google Analytics 360](https://marketingplatform.google.com/about/analytics-360/) | [Fivetran](https://fivetran.com/) | `google_analytics_360_fivetran` | `google_analytics_360` | Marketing | 6h / 32h |
| [Google Cloud Billing](https://cloud.google.com/support/billing) | x | `gcp_billing` | `gcp_billing` | Engineering | x / x |
| [Graphite API](https://graphite-api.readthedocs.io/en/latest/) | [Airflow](https://airflow.gitlabdata.com/home) | `engineering_extracts` | x | Engineering | 24h / 48h |
| [Greenhouse](https://www.greenhouse.io/) | [Sheetload](https://gitlab.com/gitlab-data/analytics/tree/master/extract/sheetload) | `greenhouse` | `greenhouse` | People | 24h / 48h |
| [Handbook YAML Files](https://gitlab.com/gitlab-data/analytics/-/tree/master/extract/gitlab_data_yaml) | [Airflow](https://airflow.gitlabdata.com/home) | `gitlab_data_yaml` | `gitlab_data_yaml` | Multiple | 8h / 24h |
| [Handbook MR Data](https://gitlab.com/gitlab-data/analytics/-/blob/master/dags/extract/handbook_mrs_extract.py) | [Airflow](https://airflow.gitlabdata.com/home) | `handbook` | `handbook` | Multiple | 24h / 24h |
| [Handbook Git Log Data](https://gitlab.com/gitlab-data/analytics/-/blob/master/dags/extract/values_page_extract.py) | [Airflow](https://airflow.gitlabdata.com/home) | `handbook` | `handbook` | Multiple | 1w / 1m |
| [LicenseDot](https://license.gitlab.com/) [ERD](https://gitlab.com/gitlab-org/license-gitlab-com/-/blob/master/doc/db_erd.pdf) | [Automatic Process](/handbook/business-technology/data-team/platform/infrastructure/#automated-process-updating-version-db-and-license-db) | `license_db` | `license_db` | Product |  24 h / 48 h |
| [Marketo](https://www.marketo.com/software/marketing-automation/) | [Stitch](https://www.stitchdata.com/) | `marketo_stitch` | x | Marketing | x / x |
| [Netsuite](https://www.netsuite.com/portal/home.shtml) | [Fivetran](https://fivetran.com/) | `netsuite_fivetran` | `netsuite` | Finance | 6h / 24h |
| PMG | x | `pmg` | `pmg` | x | x / x |
| [Qualtrics](https://www.qualtrics.com/) | [Airflow](https://airflow.gitlabdata.com/home) | `qualitrics` | `qualtrics` | Marketing | 12h / 48h |
| [Salesforce](https://www.salesforce.com/) | [Stitch](https://www.stitchdata.com/) | `salesforce_stitch` | `sfdc`| Sales | 1h / 24h |
| [SheetLoad](https://gitlab.com/gitlab-data/analytics/tree/master/extract/sheetload) | [SheetLoad](https://gitlab.com/gitlab-data/analytics/tree/master/extract/sheetload) | `sheetload` | `sheetload` | Multiple | 24h / 48h |
| [Snowplow](https://snowplowanalytics.com/) | [Snowpipe](/handbook/business-technology/data-team/platform/snowplow/index.html#snowpipe) | `snowplow` | `snowplow` | Product | 15m / 24h |
| [Version DB](https://version.gitlab.com/users/sign_in) | [Automatic Process](/handbook/business-technology/data-team/platform/infrastructure/#automated-process-updating-version-db-and-license-db) | `version_db` | `version_db` | Product |  24 h / 48 h |
| [Zendesk](https://www.zendesk.com/) | [Stitch](https://www.stitchdata.com/) | `zendesk_stitch` | `zendesk` | Support | 1h / 24h |
| [Zoom](https://zoom.us/) | [Meltano](https://meltano.com/) | `tap_zoom` | N/A | People | 24h / N/A |
| [Zuora](https://www.zuora.com/) | [Stitch](https://www.stitchdata.com/) | `zuora_stitch` | `zuora` | Finance | 30m / 24h |


### Adding new Data Sources and Fields

Process for adding a new data source:

- Create a new issue in the Analytics project requesting for the data source to be added:
    - Document what tables and fields are required
    - Document the questions that this data will help answer
- Create an issue in the [Security project](https://gitlab.com/gitlab-com/gl-security/security-department-meta/issues/) and cross-link to the Analytics issue.
    - Tag the Security team `gitlab-com/gl-security`

To add new fields to the BambooHR extract:

- Create a new issue in the Analytics project using the BambooHR template
- Gain approval from a Data Team Manager and the Compensation and Benefits Manager
- Once approved, assign to the Compensation and Benefits Manager and a Data Engineer who will verify the extract

### Data Team Access to Data Sources

In order to integrate new data sources into the data warehouse, specific members of the Data team will need admin-level access to data sources, both in the UI and through the API.
We need this admin-level access through the API in order to pull all the data needed to build the appropriately analyses and through the UI to compare the results of prepared analyses to the UI.

Sensitive data sources can be limited to no less than 1 data engineer and 1 data analyst having access to build the require reporting.
In some cases, it may only be 2 data engineers.
We will likely request an additional account for the automated extraction process.

Sensitive data is locked down through the security paradigms listed below;
Sisense will never have access to sensitive data, as Sisense does not have access to any data by default.
Sisense's access is always explicitly granted.

#### DataSiren

To ensure that the data team has a complete picture of where sensitive data is in the data warehouse, as well as make sure Sisense does not have access to sensitive data, a periodic scan of the data warehouse is made using dbt along with the internally-developed library of tools created as [`datasiren`](https://gitlab.com/gitlab-data/datasiren). This scan is currently executed weekly. The fine-grained results are stored in Snowflake in the `PREP.DATASIREN` schema and are not available in Periscope because of sensitivity reasons.  High-level results have been made available in Periscope, including the simple dashboard found [here](https://app.periscopedata.com/app/gitlab/793578/DataSiren).  

### Using SheetLoad

SheetLoad is the process by which a Google Sheets and CSVs from GCS or S3 can be ingested into the data warehouse.

Technical documentation on usage of SheetLoad can be found in the [readme](https://gitlab.com/gitlab-data/analytics/tree/master/extract/sheetload) in the data team project.

If you want to import a Google Sheet or CSV into the warehouse, please [make an issue](https://gitlab.com/gitlab-data/analytics/issues/new?issue%5Bassignee_id%5D=&issue%5Bmilestone_id%5D=) in the data team project using the "CSV or GSheets Data Upload" issue template. This template has detailed instructions depending on the type of data you want to import and what you may want to do with it.

#### Considerations
{: #mind-about-sheetload}

SheetLoad should primarily be used for data whose canonical source is a spreadsheet - i.e. Sales quotas. If there is a source of this data that is not a spreadsheet, you should at least [make an issue for a new data source](https://gitlab.com/gitlab-data/analytics/-/issues/new?issuable_template=New%20Data%20Source) to get the data pulled automatically. However, if the spreadsheet is the SSOT for this data, then SheetLoad is the appropriate mechanism for getting it into the warehouse.

##### Loading into Snowflake

SheetLoad is designed to make the table in the database an exact copy of the sheet from which it is loading. Whenever SheetLoad detects a change in the source sheet, it will drop the database table and recreate it in the image of the updated spreadsheet. This means that if columns are added, changed, etc. it will all be reflected in the database. Changes are detected within 24 hours.

##### Preparing for SheetLoad

Except for where absolutely not possible, it is best that the SheetLoad sheet import from the original Google Sheet directly using the `importrange` function. This allows you to leave the upstream sheet alone while enabling you to format the SheetLoad version to be plain text. Any additional data type conversions or data cleanup can happen in the base dbt models. (This does not apply to the Boneyard.)

Some additional considerations for preparing the data for loading:

* format all numeric columns to have no commas or other symbols - 1000.46 instead of $1,000.46
* use simple headers where possible - `user_name` instead of `GitLab - User Name`
* use blank cells to indicate no data. blank cells are stored as `null` in the database.

##### Modeling

Before regular SheetLoad data can be accessible by Sisense, it has to be modeled via dbt. A minimum of 2 models will be made for the sheet: a [source model](/handbook/business-technology/data-team/platform/dbt-guide/#source-models) and a [staging model](/handbook/business-technology/data-team/platform/dbt-guide/#staging). These will be made by a member of the data team once you've [made an issue](https://gitlab.com/gitlab-data/analytics/issues/new?issue%5Bassignee_id%5D=&issue%5Bmilestone_id%5D=) in the data team project.

##### Boneyard

The `boneyard` schema is where data can be uploaded from a spreadsheet and it will be directly available for querying within Sisense. However, this is for instances where a one-off analysis is needed and/or you need to join this to data already in the warehouse. It is called Boneyard to highlight that this data is relevant only for an **_ad hoc/one off_** use case and will become stale within a relatively short period of time. We will periodically remove stale data from the `boneyard` schema.

##### Certificates

If you are adding Certificates to SheetLoad, refer to the instructions in the [People Group page](/handbook/people-group/learning-and-development/certifications/#step-5-add-to-sheetload)

### Qualtrics Data Push / Qualtrics SheetLoad

The Qualtrics data push process, also known in code as `Qualtrics SheetLoad`, enables emails to be uploaded to Qualtrics from the data warehouse without having to be downloaded onto a team member's machine first.  This process shares its name with SheetLoad because it looks through Google Sheets for files with names starting with `qualtrics_mailing_list`.  For each of the files it finds with an `id` column as the first column, it uploads that file to Snowflake.  The resulting table is then joined with the GitLab user table to retrieve email addresses.  The result is then uploaded to Qualtrics as a new mailing list.

During the process, the Google Sheet is updated to reflect the process' status.  The first column's name is set to `processing` when the process begins, and then is set to `processed` when the mailing list and contacts have been uploaded to Qualtrics.  Changing the column name informs the requester of the process' status, assists in debugging, and ensures that a mailing list is only created once for each spreadsheet.

The end user experience is described on the [UX Qualtrics page](/handbook/engineering/ux/qualtrics/#distributing-your-survey-to-gitlabcom-users).

### Data Pump


```mermaid
graph LR

yml>pumps.yml]

dataModel[(data model)] --> o{{Airflow DAG}}

yml --> o
o --> S3

S3 --> workato{{Workato recipe}} --> target[(Target)]
```

In order to make it easy for anyone to send data from Snowflake to other applications in the GitLab tech stack we have partnered with the Enterprise Applications Integration Engineering team to create this data integration framework, which we are calling Data Pump. The Data Pump [Airflow DAG](https://airflow.gitlabdata.com/tree?dag_id=data_pumps), which runs the pump, is is set to **run once daily at 05:00 UTC**.

### Adding a Data Pump

**Step 1:** Create a data model [using dbt](https://about.gitlab.com/handbook/business-ops/data-team/platform/dbt-guide/#using-dbt) in `/marts/pumps` (or `/marts/pumps_sensitive` if the model contains [RED or ORANGE Data](https://about.gitlab.com/handbook/engineering/security/data-classification-standard.html#data-classification-levels)), following our [SQL](https://about.gitlab.com/handbook/business-ops/data-team/platform/sql-style-guide/) and [dbt](https://about.gitlab.com/handbook/business-ops/data-team/platform/dbt-guide/#style-and-usage-guide) style and documentation standards. Create an MR using dbt model changes template. Once this is merged and appears in Snowflake in `PROD.PUMPS` or `PROD.PUMPS_SENSITIVE` you are ready for steps two and three.

**Step 2:** Add Model to `pumps.yml` using the 'Pump Changes' MR template with the following attributes:
* model - the name of the model in dbt and snowflake
* timestamp_column - the name of the column that should be used to batch the data (or `null` if there is none and the table is small)
* sensitive - `True` if this model contains sensitive data and is in the pumps_sensitive directory and schema
* owner - your (or the business DRI's) gitlab handle

**Step 3:** Create an [integration issue in the integrations project](https://gitlab.com/gitlab-com/business-ops/enterprise-apps/integrations/integrations-work/-/issues/new) using the 'New Data Pump' issue template so that the Integration team can map and integrate the data into the target application.

### Snowplow Infrastructure

Refer to the [Snowplow Infrastructure page](/handbook/business-technology/data-team/platform/snowplow) for more information on our setup.

### Data Source Overviews

- [Customer Success Dashboards](https://drive.google.com/open?id=1FsgvELNmQ0ADEC1hFEKhWNA1OnH-INOJ)
- [Netsuite](https://www.youtube.com/watch?v=u2329sQrWDY)
    - [Netsuite and Campaign Data](https://drive.google.com/open?id=1KUMa8zICI9_jQDqdyN7mGSWSLdw97h5-)
- [Version (pings)](https://drive.google.com/file/d/1S8lNyMdC3oXfCdWhY69Lx-tUVdL9SPFe/view)
    - Note that up until October 2019, the data team referred to the entire **version** data source as "pings". However, usage ping is only one subset of the version data source which is why we now use "version" or "version app" to refer to the version.gitlab.com _data source_ and "usage data" or "usage pings" or "pings" to refer to the [specific usage data feature](https://docs.gitlab.com/ee/user/admin_area/settings/usage_statistics.html) of the version data source.
- [Salesforce](https://youtu.be/KwG3ylzWWWo)
- [Zendesk](https://drive.google.com/open?id=1oExE1ZM5IkXcq1hJIPouxlXSiafhRRua)

## <i class="fas fa-clock fa-fw" style="color:rgb(252,109,38); font-size:.85em" aria-hidden="true"></i>Orchestration

We use Airflow on Kubernetes for our orchestration. Our specific setup/implementation can be found [here](https://gitlab.com/gitlab-data/data-image). Also see the [Data Infrastructure](/handbook/business-technology/data-team/platform/infrastructure/) page for more information.

## <i class="fas fa-database fa-fw" style="color:rgb(107,79,187); font-size:.85em" aria-hidden="true" id="data-warehouse"></i>Data Warehouse

We currently use [Snowflake](https://docs.snowflake.net/manuals/index.html) as our data warehouse. The Enterprise Data Warehouse (EDW) is the single source of truth for GitLab's corporate data, performance analytics, and enterprise-wide data such as Key Performance Indicators. The EDW supports GitLab’s data-driven initiatives by providing all teams a common platform and framework for reporting, dashboarding, and analytics. With the exception of point-to-point application integrations all current and future data projects will be driven from the EDW. As a recipient of data from a variety of GitLab source systems, the EDW will also help inform and drive Data Quality best-practices, measures, and remediation to help ensure all decisions are made using the best data possible.

### Warehouse Access

To gain access to the data warehouse:

- Create an issue in the [access requests project](https://gitlab.com/gitlab-com/team-member-epics/access-requests) documenting the level of access required.
- Do not request a shared account - each account must be tied to a user.
- We loosely follow the paradigm explained in [this blog post](https://blog.fishtownanalytics.com/how-we-configure-snowflake-fc13f1eb36c4) around permissioning users.

### Snowflake Permissions Paradigm

We use [Permifrost](https://gitlab.com/gitlab-data/permifrost/) to help manage permissions for Snowflake.
Our configuration file for our Snowflake instance is stored in [this roles.yml file](https://gitlab.com/gitlab-data/analytics/blob/master/load/snowflake/roles.yml).
Also available is our [handbook page on Permifrost](/handbook/business-technology/data-team/platform/permifrost/).

We follow this general strategy for role management:

- Every user has an associated user role
- Functional roles exist to represent common privilege sets (`analyst_finance`, `data_manager`, `product_manager`)
- Logical groups of data have their own object roles
- Object roles are assigned primarily to functional roles
- Higher privilege roles (`accountadmin`, `securityadmin`, `useradmin`, `sysadmin`) are assigned directly to users
- Service accounts have an identically named role
- Additional roles can be assigned either to the service account role or the service account itself, depending on usage and needs
- Individual privileges can be granted at the granularity of the table & view
- Warehouse usage can be granted to any role as needed, but granting to functional roles is recommended

#### User Roles

Every user will have their own user role that should match their user name.
Object level permissions (database, schemas, tables) in Snowflake can only be granted to roles.
Roles can be granted to users or to other roles.
We strive to have all privileges flow through the user role so that a user only has to use one role to interact with the database.
Exceptions are privileged roles such as `accountadmin`, `securityadmin`, `useradmin`, and `sysadmin`.
These roles grant higher access and should be intentionally selected when using.

#### Functional Roles

Functional roles represent a group of privileges and role grants that typically map to a job family.
The major exception is the analyst roles.
There are several variants of the analyst role which map to different areas of the organization.
These include `analyst_core`, `analyst_finance`, `analyst_people`, and more.
Analysts are assigned to relevant roles and are explicitly granted access to the schemas they need.

Functional roles can be created at any time.
It makes the most sense when there are multiple people who have very similar job families and permissions.

#### Object Roles

Object roles are for managing access to a set of data.
Typically these represent all of the data for a given source.
The `zuora` object role is an example.
This role grants access to the raw Zuora data coming from Stitch, and also to the source models in the `prep.zuora` schema.
When a user needs access to Zuora data, granting the `zuora` role to that user's user role is the easiest solution.
If for some reason access to the object role doesn't make sense, individual privileges can be granted at the granularity of a table.

#### Examples

This is an example role hierarchy for an Data Analyst, Core:

```mermaid
graph LR
    A([User: datwood]) -->|Member of| B[User Role: datwood]
    B -->|Member of| C[Functional Role: analyst_core]
    C -->|Member of| D[Object Role: bamboohr]
    C -->|Member of| H[Object Role: dbt_analytics]
    C -->|Member of| E[Object Role: netsuite]
    C -->|Member of| F[Object Role: zuora]
    G{{Privileges: analytics_sensitive}} -->|Granted to| C
```

This is an example role hierarchy for an Data Engineer and Account Administrator:

```mermaid
graph LR
    A([User: tmurphy]) -->|Member of| B[User Role: tmurphy]
    B -->|Member of| C[Functional Role: engineer]
    C -->|Member of| F[Functional Role: loader]
    C -->|Member of| H[Functional Role: transformer]
    G{{ Privileges: Read/Write Raw}} -->|Granted to| C
    A -->|Member of| D[Privileged Role: sysadmin]
    A -->|Member of| E[Privileged Role: securityadmin]
```

This is an example role hierarchy for a Security Operations Engineer:

```mermaid
graph LR
    A([User: ssichak]) -->|Member of| B[User Role: ssichak]
    A -->|Member of| C[Privileged Role: securityadmin]
```

<div class="panel panel-success">
**Managing Roles for Snowflake**
{: .panel-heading}
<div class="panel-body">

Here are the proper steps for provisioning a new user and user role:

- Make sure we have an issue in the GitLab Data Team project linking the original request with the `Provisioning` label applied
- Login to Snowflake and switch to `securityadmin` role
    - All roles should be under `securityadmin` ownership
- Copy the [`user_provision.sql`](https://gitlab.com/gitlab-data/analytics/-/blob/master/load/snowflake/user_provision.sql) script and replace the email, firstname, and lastname values in the initial block
- If a password is needed, use [Password Generator](https://passwordsgenerator.net/) to create one
    - Send username and password credentials to user with [One Time Secret](https://onetimesecret.com/) or via Slack
- Document in Snowflake roles.yml permifrost config file
    - Add the user and user role you created
    - Assign the user role to new user
    - Assign any additional roles to user
- Ensure the user is assigned the application in Okta
- Ensure the user is assigned to the `okta-snowflake-users` [Google Group](https://groups.google.com/my-groups)

</div>
</div>

### Compute Resources

Compute resources in Snowflake are known as "warehouses".
To better track and monitor our credit consumption, we have created several warehouses depending on who is accessing the warehouse.
The names of the warehouse are appended with their size (`analyst_xs` for extra small)

| warehouse            | purpose                                                                                         | max query (minutes) |
| -------------------- | ----------------------------------------------------------------------------------------------- | ------------------- |
| `admin`              | This is for permission bot and other admin tasks                                                | 10                  |
| `airflow_testing_l`  | For testing Airflow locally                                                                     | 30                  |
| `analyst_*`          | These are for Data Analysts to use when querying the database or modeling data                  | 30                  |
| `engineer_*`         | These are for Data Engineers and the Manager to use when querying the database or modeling data | 30                  |
| `fivetran_warehouse` | This is exclusively for Fivetran to use                                                         | 30                  |
| `gitlab_postgres`    | This is for extraction jobs that pull from GitLab internal Postgres databases                   | 10                  |
| `loading`            | This is for our Extract and Load jobs                                                           | 60                  |
| `merge_request_*`    | These are scoped to GitLab CI for dbt jobs within a merge request                               | 60                  |
| `reporting`          | This is for the BI tool for querying. Note that Sisense enforces a 4 minute timeout.            | 30                  |
| `stitch`             | This is exclusively for Stitch to use                                                           | 30                  |
| `target_snowflake`   | This is for the Meltano team to test their Snowflake loader                                     | 5                   |
| `transforming_*`     | These are for production dbt jobs                                                               | 60                  |

If you're running into query time limits consider using a larger warehouse.

### Data Storage

We use three primary databases: `raw`, `prep`, and `prod`.
The `raw` database is where data is first loaded into Snowflake; the other databases are for data that is ready for analysis (or getting there).

There is a `snowflake` database, which contains information about the entire GitLab instance.
This includes all tables, views, queries, users, etc.

There is a `covid19` database, which is a shared database managed through the Snowflake Data Exchange.

There is a `testing_db` database, which is used for testing Permifrost.

All databases not defined in our [`roles.yml`](https://gitlab.com/gitlab-data/analytics/-/blob/master/load/snowflake/roles.yml) Permifrost file are removed on a weekly basis.

| Database | Viewable in Sisense |
|:-:|:-:|
| raw | No |
| prep | No |
| prod | Yes |

#### Raw

This database is not available to query in Sisense. No dbt models exist for this data. 

- Raw may contain sensitive data, so permissions need to be carefully controlled
- Data is stored in different schemas based on the source
- User access can be controlled by schema and tables

#### Prep

This database is not available to query in Sisense.

- [Source models](/handbook/business-technology/data-team/platform/dbt-guide/#source-models) are built in logical schemas corresponding to the data source (i.e. `sfdc`, `zuora`)
- PREPARATION - this is the default schema where dbt models are built
- SENSITIVE

#### Prod

This database and all schemas and tables in it are queryable by Sisense.

With the exception of `public`, and [`boneyard`](/handbook/business-technology/data-team/#mind-about-sheetload), all schemas are controlled by dbt.
See the [dbt guide](/handbook/business-technology/data-team/platform/dbt-guide) for more information.

#### Folder Structure in Analytics Project

The table below shows a mapping of how models stored within folders in the [`models/`](https://gitlab.com/gitlab-data/analytics/-/tree/master/transform/snowflake-dbt/models) directory in the analytics project will be materialized in the data warehouse. 

The source of truth for this is in the [`dbt_project.yml` configuration file](https://gitlab.com/gitlab-data/analytics/-/blob/master/transform/snowflake-dbt/dbt_project.yml).

| Folder in snowflake-dbt/models/ | db.schema | Details | Queryable in Sisense |
|-|-|-|:-:|
| common/ | prod.common | Top-level folder for facts and dimensions. Do not put models here. | Yes |
| common/prep/ | prep.preparation | Prep models used to create facts/dims. | No |
| common/sensitive/ | prep.sensitive | Facts/dims that contain sensitive data. | No |
| common/curate/ | prod.curate |  | Yes |
| common/prod/ | prod.common | Production fact/dim tables. | Yes |
| common_mapping/ | prod.common_mapping | Contains mapping, bridge, or look-up tables | Yes |
| common_mapping/prep/ | prod.common_mapping | Preparation tables for mapping, bridge, and look-up tables | Yes |
| marts/ | prod.<marts> | Contains mart-level data. | Yes |
| prep/ | prep.preparation | General preparation models for production. | No. |
| legacy/ | prod.legacy | Contains models built in a non-dimensional manner | Yes |
| sources/ | prep.<source> | Contains source models. Schema is based on data source | No |
| workspaces/ | prod.workspace_<workspace> | Contains workspace models that aren't subject to SQL or dbt standards.  | Yes |

#### Static

For data warehouse use cases that require us to store data for our users without updating it automatically with dbt we use the `STATIC` database. This also allows for analysts and other users to create their own data resources (tables, views, temporary tables). There is a sensitive schema for sensitive data within the static database. If your use case for static requires the use or storage of sensitive data please create an issue for the data engineers.

### Timezones

All timestamp data in the warehouse should be stored in UTC. The [default timezone](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone) for a Snowflake sessions is PT, but we have overridden this so that UTC is the default. This means that when `current_timestamp()` is queried, the result is returned in UTC.

[Stitch explicitly converts](https://www.stitchdata.com/docs/data-structure/snowflake-data-loading-behavior#%0A%0A%09%0A%09%09%09%09%09a-column-contains-timestamp-data%0A%0A%09%09%09%09%0A%0A%0A) timestamps to UTC. Fivetran does this as well (confirmed via support chat).

The only exception to this rule is the use of pacific time to create date_id in fact tables, which should always be created by the `get_date_pt_id` dbt macro and labeled with the `_pt_id` suffix.

### Snapshots
{: #snapshots-definition}

We use the term snapshots in multiple places throughout the data team handbook and the term can be confusing depending on the context. Snapshots as defined by the dictionary is "a record of the contents of a storage location or data file at a given time". We strive to use this definition whenever we use the word.

#### dbt

The most common usage is in reference to [dbt snapshots](https://docs.getdbt.com/docs/snapshots). When dbt snapshots is run, it takes the state of the data based on a query specified by the user and updates a table that contains the full history of the state of the data. It has `valid_to` and `valid_from` fields indicating the time period for which that particular snapshot is valid. See the [dbt snapshots](/handbook/business-technology/data-team/platform/dbt-guide/#snapshots) section in our dbt guide for more technical information.

The tables generated and maintained by dbt snapshots are the raw historical snapshot tables. We will build downstream models on top of these raw historical snapshots for further querying. The [snapshots folder](https://gitlab.com/gitlab-data/analytics/tree/master/transform/snowflake-dbt/snapshots) is where we store the dbt models. One common model we may build is one that generate a single entry (i.e. a single snapshot) for a given day; this is useful when there are multiple snapshots taken in a 24 hour period. We also will build models to return the most current snapshot from the raw historical table.

#### Other uses

Our Greenhouse data can be thought of as a snapshot. We get a daily database dump provided by Greenhouse that we load into Snowflake. If we start taking dbt snapshots of these tables then we would be creating historical snapshots of the Greenhouse data.

The extracts we do for some [yaml files](https://gitlab.com/gitlab-data/analytics/tree/master/extract/gitlab_data_yaml) and for BambooHR can also be thought of as snapshots. This extraction works by taking the full file/table and storing it in its own, timestamped row in the warehouse. This means we have historical snapshots for these files/tables but these are not the same kind of snapshot as dbt. We'd have to do additional transformations to get the same `valid_to` and `valid_from` behavior.

#### Language

- Snapshot - The state of data at a specific point in time
- Take a snapshot - Run the job that takes the state of the data currently and stores it. Can be used in the dbt context. Not recommended to reference our yaml extract jobs - these would be "run the extract".
- Historical snapshots - A table that contains data for a given source table at multiple points in time. Most commonly used to reference dbt-generated snapshot tables. Can also be used to reference the yaml extract tables.
- Latest snapshot - The most current state of the data we have stored. For dbt snapshots these are the records that have null for the `valid_to`. For BambooHR and yaml extracts these correspond to the last time the extraction job was run. For Greenhouse raw, this represents the data as it is in the warehouse. Were we to start taking snapshots of the Greenhouse data the speaker would have to clarify if they mean the raw table or the latest record in the historical snapshots table.

### Backups

For an extra layer of robustness, we backup data from the warehouse into GCS (Google Cloud Storage). We execute the jobs using dbt's [`run-operation`](https://docs.getdbt.com/docs/using-operations) capabilities. Currently, we backup all of our snapshots daily and retain them for a period of 1 month. We implemented the basic instructions outlined in [this Calogica blog post](https://calogica.com/sql/snowflake/dbt/2019/09/09/snowflake-backup-s3.html).

## <i class="fas fa-cogs fa-fw" style="color:rgb(252,109,38); font-size:.85em" aria-hidden="true"></i>Transformation

We use [dbt](https://www.getdbt.com/) for all of our transformations.
See our [dbt guide](/handbook/business-technology/data-team/platform/dbt-guide) for more details on why and how we use this tool.

## <i class="fas fa-check-double fa-fw" style="color:rgb(107,79,187); font-size:.85em" aria-hidden="true"></i>Trusted Data Framework
{: #tdf}

Data Customers expect Data Teams to provide data they can trust to make their important decisions. And Data Teams need to be confident in the quality of data they deliver. But this is a hard problem to solve: the [Enterprise Data Platform](/handbook/business-technology/data-team/direction/#a-complete-enterprise-data-platform) is complex and involves multiple stages of data processing and transformation, with tens to hundreds of developers and end-users actively changing and querying data 24 hours a day. The Trusted Data Framework (TDF) supports these quality and trust needs by defining a standard  framework for data testing and monitoring across data processing stages, accessible by technical teams _and business teams_. Implemented as a stand-alone module separate from existing data processing technology, the TDF fulfills the need for an independent data monitoring solution.

- Enable everyone to contribute to trusted data, not just analysts and engineers
- Enable data validations from top to bottom and across all stages of data processing
- Validate data from source system data pipelines
- Validate data transforms into dimensional models
- Validate critical company data
- Deployable independently from central data processing technology

### Key Terms

- Assertion or Test Case - An [individual test](https://en.wikipedia.org/wiki/Test_case#:~:text=In%20software%20engineering%2C%20a%20test,verify%20compliance%20with%20a%20specific) and the smallest unit of a test that can be performed. In TDF the test case is expressed either as a SQL statement or via a YAML configuration within SQL-compilation tool, dbt.
- Data Schema - The tables, columns, views, and other structural elements that make up a data subject area, create using [SQL Data Definition Language](https://en.wikipedia.org/wiki/Data_definition_language#:~:text=In%20the%20context%20of%20SQL,tables%2C%20indexes%2C%20and%20users.) (DDL).
- Golden Data - [Golden data](https://blogs.informatica.com/2015/05/08/golden-record/) is a data constant from a single field or a group of fields important to the business.
- Monitoring - [Tracking the results](https://www.edq.com/glossary/data-monitoring/#:~:text=Data%20monitoring%20is%20the%20process,using%20dashboards%2C%20alerts%20and%20reports.) of tests cases to help ensure data is ready for use.

### Trusted Data Components

The primary elements of the TDF include:

1. [A Virtuous Test Cycle](/handbook/business-technology/data-team/platform/#virtuous-test-cycle) that embeds quality as a normal part of daily data development, ranging from new data solutions to break-fix issue resolution.
1. [Test Cases Expressed As SQL and YAML](/handbook/business-technology/data-team/platform/#test-cases-expressed-as-sql-and-yaml) which can be developed by anyone.
1. The [Trusted Data Schema](/handbook/business-technology/data-team/platform/#trusted-data-schema) saves test results for monitoring and alerting, and long-term analysis towards the path of developing wisdom around business processes and data platform performance.
1. [Schema-to-Golden Record Coverage](/handbook/business-technology/data-team/platform/dbt-guide/#schema-to-golden-data-coverage) to provide broad coverage of the data warehouse domain, ranging from schema to critical "Golden" data.
1. The [Trusted Data Dashboard](/handbook/business-technology/data-team/platform/#trusted-data-dashboard), a _business-friendly_ dashboard to visualize overall test coverage, successes, and failures.
1. The [Test Run](/handbook/business-technology/data-team/platform/#test-run) is when a Test Cases are executed.

#### Virtuous Test Cycle

The TDF embraces business users as _the most important participant_ in establishing trusted data and uses a simple and accessible testing model. With SQL and YAML as a test agent, a broad group of people can contribute test cases. The test format is straightforward with simple PASS/FAIL results and just four test case types. Adoption grows quickly as TDF demonstrates value:

- Data Customers and Business Users learn the testing framework and create tests themselves
- Teams embrace testing as a valuable activity to include _at all times_, not as a last-minute activity
- The Data Team learns to add new tests as part of production-down retrospectives to more rapidly identify issues before they become large problems
- Teams develop operational rythms to continually develop new tests and expand test coverage

Over time, it is not uncommon to develop hundreds of tests cases which are run on a daily basis, continually validating data quality.

#### Test Cases Expressed As SQL and YAML

SQL is the universal language in databases and nearly everyone who works with data has some level of SQL competency. However, not everyone may be familiar with SQL and we don't want that to limit who can contribute. We use [dbt](/handbook/business-technology/data-team/platform/dbt-guide/) to support the TDF which enables the defining of tests via SQL _and_ YAML.

#### Trusted Data Schema

With all tests being run via dbt, storing tests results is simple. We store the results of every test run in the data warehouse. Storing test results enables a variety of valuable features, including:

- data visualization and pattern analysis test results (total tests run by date, PASS/FAIL rate by subject area, and so on)
- measurement of test coverage over a data subject or schema (number of tests by area)
- measurement of system quality improvements over time (an increase in the PASS rate)
- development of an alerting system based on test result

These test results are parsed and are available for querying in Sisense.

The schema we store all test results is: `WORKSPACE_DATA`. <br>
Note: This schema only containts views. 

#### Schema To Golden Record Coverage

The Data Warehouse environment can change quickly and the TDF supports predictability, stability, and quality with test coverage of the areas in the Data Warehouse that are most likely to change:

1. [Schema tests](/handbook/business-technology/data-team/platform/dbt-guide/#schema-tests) to validate the integrity of a schema
1. [Column Value tests](/handbook/business-technology/data-team/platform/dbt-guide/#column-value-tests) to determine if the data value in a column matches pre-defined thresholds or literals
1. [Rowcount tests](/handbook/business-technology/data-team/platform/dbt-guide/#rowcount-tests) to determine if the number of rows in a table over a pre-defined period of time match pre-defined thresholds or literals
1. [Golden Data tests](/handbook/business-technology/data-team/platform/dbt-guide/#golden-data-tests) to determine if pre-defined high-value data exists in a table

The implementation details of these tests are documented in our [dbt guide](/handbook/business-technology/data-team/platform/dbt-guide/#schema-to-golden-data-coverage).

#### Trusted Data Dashboard

The Trusted Data Dashboard in Sisense can be found [here](https://app.periscopedata.com/app/gitlab/756199/Trusted-Data-Dashboard)

#### Test Run

More to come.

## <i class="fas fa-chart-bar fa-fw" style="color:rgb(252,109,38); font-size:.85em" aria-hidden="true"></i>Visualization

We use [Sisense](https://www.periscopedata.com) as our Data Visualization and Business Intelligence tool. To request access, please follow submit an [access request](https://gitlab.com/gitlab-com/team-member-epics/access-requests/-/issues/new?issuable_template=New_Access_Request).

#### Meta Analyses for the Data Team

- [Sisense Usage! 📈](https://app.periscopedata.com/app/gitlab/410320/)
- [Sisense Account Optimization 💪](https://app.periscopedata.com/app/gitlab/410321/)
- [Sisense Account Maintenance 🗑️](https://app.periscopedata.com/app/gitlab/410322/)
- [dbt Event Logging](https://app.periscopedata.com/app/gitlab/420622/)
- [Snowflake Spend ️❄](https://app.periscopedata.com/app/gitlab/443349/)

## <i class="fas fa-user-lock fa-fw" style="color:rgb(107,79,187); font-size:.85em" aria-hidden="true"></i>Security

### Passwords

Per GitLab's password policy, we rotate service accounts that authenticate only via passwords every 90 days. A record of systems changed and where those passwords were updated is kept in [this Google Sheet](https://docs.google.com/spreadsheets/d/17T89cBIDLkMUa3rIw1GxS-QWFL7kjeLj2rCQGZLEpyA/edit?usp=sharing).

We also rotate Snowflake user passwords the first Sunday of every 3rd month of the year (January, April, July, October) via the [Snowflake Password Reset DAG](https://gitlab.com/gitlab-data/analytics/blob/master/dags/general/snowflake_password_reset.py).

### Software User Provisioning

The data team is responsible for provisioning users within the tools managed by the Data Team. This includes tools like Fivetran, Stitch, and Snowflake.

For Snowflake, we have a robust process documented in the [Snowflake Permissions Paradigm](/handbook/business-technology/data-team/platform/#snowflake-permissions-paradigm) section of this page.

For other tools, add users via the UI and in the appropriate [Google Group](https://groups.google.com/my-groups) if one exists.
