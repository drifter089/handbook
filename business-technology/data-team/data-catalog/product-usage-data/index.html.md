
---
layout: handbook-page-toc
title: "Product Usage Data"
description: "Product Usage Data provides quantitative measurement of how, when, and where the Customer is using GitLab as a product."
---

## On this page
{:.no_toc}

- TOC
{:toc}

---

## Product Usage Data

Product Usage Data provides quantitative measurement of how, when, and where the Customer is using GitLab as a product and how the utilization metrics can be integrated into CRO organization business processes to accelerate customer adoption and improve customer retention. The Product Usage Data page will provide the information and tools that GitLab team members can use to explore Product Usage Data and develop customer insights.

### Business Use Cases for Customer Product Usage Data:

- Insight into user adoption/onboarding for a customer instance of GitLab
- Monitor trends for increase/decrease in utilization of capabilities within a particular DevOps Stage
- Monitor for drops in active users
- Identify accounts that are far behind on the latest version
- Identify the type of installation used in their deployment
- Visibility into increase/decrease in # of GitLab Runners
- Visibility into GitLab implementation architecture, scaling up/down of infrastructure
- Discussing utilization and adoption patterns with our internal champions to strategize on where to apply energy in terms of new user onboarding and overall value realization for the account

#### Future use cases will also include:

- Tracking of stage adoption by a customer and eventually teams for ROI and maturity. This will also act as insight to progress against the customer success plan objectives.
- Driving digital engagement (i.e., actions and content) based on utilization, customer lifecycle phase and engagement (i.e., time-to-value).


The data solution delivers three [Self-Service Data](/handbook/business-technology/data-team/direction/self-service/) capabilities:

1. Gainsight Users:  The customer's product usage data ingested within Gainsight from Snowflake to create specific workflows, visualize trends, build customer health scorecards, review use case adoption strategies and understand how the data connects. 
1. Dashboard Developer/User: A new Sisense data model containing the complete dimensional model components to build new dashboards and link existing dashboards to Customer Product Adoption Data.
1. SQL Developer: An Enterprise Dimensional Model subject area

From a Data Platform perspective, the solution delivers:

1. Gainsight Data Pump - EDW to Gainsight and Gainsight to EDW
1. An extension to the Enterprise Dimensional Model for Product Usage data
1. Testing and data validation extensions to the Data Pipeline Health dashboard
1. ERDs, dbt models, and related platform components


### Quick Links
<div class="flex-row" markdown="0" style="height:80px">
  <a href="https://about.gitlab.com/handbook/customer-success/product-usage-data/using-product-usage-data-in-gainsight/" class="btn btn-purple" style="width:33%;height:100%;margin:5px;float:left;display:flex;justify-content:center;align-items:center;">Product Usage Data in Gainsight</a>
  <a href="https://about.gitlab.com/handbook/customer-success/tam/gainsight/#access-via-salesforce" class="btn btn-purple" style="width:33%;height:100%;margin:5px;float:left;display:flex;justify-content:center;align-items:center;">Using Gainsight within Customer Success</a>
  <a href="https://app.periscopedata.com/app/gitlab/803470/WIP:-Customer-Product-Adoption-Dashboard" class="btn btn-purple" style="width:33%;height:100%;margin:5px;float:left;display:flex;justify-content:center;align-items:center;">WIP: Customer Product Adoption Dashboard</a>
  <a href="https://forms.gle/9E9GBFhzFViCnB9q7" class="btn btn-purple" style="width:33%;height:100%;margin:5px;float:left;display:flex;justify-content:center;align-items:center;">WIP: Product Usage Data - Knowledge Assessment</a>
  <a href="https://www.youtube.com/watch?v=F4FwRcKb95w&feature=youtu.be" class="btn btn-purple" style="width:33%;height:100%;margin:5px;float:left;display:flex;justify-content:center;align-items:center;">Getting started using Sisense Discovery</a>
   <a href="https://www.youtube.com/watch?v=Fdl6mdlp1-Y&amp;feature=youtu.be" class="btn btn-purple" style="width:33%;height:100%;margin:5px;float:left;display:flex;justify-content:center;align-items:center;">Self Service Walk-through Video</a>
</div>
<br><br><br><br><br><br><br><br><br>

### Data Security Classification

Much of the data within and supporting the Product Usage Data is [Orange](/handbook/engineering/security/data-classification-standard.html#orange) or [Yellow](/handbook/engineering/security/data-classification-standard.html#yellow). This includes ORANGE customer metadata from the account, contact data from Salesforce and Zuora and GitLab's Non public financial information, all of which shouldn't be publicly available. Care should be taken when sharing data from this dashboard to ensure that the detail stays within GitLab as an organization and that appropriate approvals are given for any external sharing. In addition, when working with row or record level customer metadata care should always be taken to avoid saving any data on personal devices or laptops. This data should remain in [Snowflake](/handbook/business-technology/data-team/platform/#data-warehouse) and [Sisense](/handbook/business-technology/data-team/platform/periscope/) and should ideally be shared only through those applications unless otherwise approved.

  
**ORANGE**

- Description: Customer and Personal data at the row or record level.
- Objects:
  - `dim_crm_account`
  - `dim_billing_account`
  - `dim_ip_to_geo`
  - `dim_location`

**YELLOW**

- Description: GitLab Financial data, which includes aggregations or totals.
- Objects:
  - `dim_subscriptions`
  - `prep_recurring_charge`

### Solution Ownership

- Source System Owner:
    - Usage Ping: `@jfarris`
    - Salesforce: `@jbrennan1`
- Source System Subject Matter Expert:
    - Usage Ping: `@jfarris`
    - Gainsight:  `@jbeaumont`
    - Salesforce: `@jbrennan1`
- Data Team Subject Matter Expert: `@rparker` `@snalamaru`

### Key Terms

1. [Customer](https://about.gitlab.com/handbook/sales/sales-term-glossary/#customer)
1. [Usage Ping](https://docs.gitlab.com/ee/development/usage_ping/)
1. [GitLab Self-Managed Subscription](https://docs.gitlab.com/ee/subscriptions/self_managed)
1. [GitLab SaaS subscription](https://docs.gitlab.com/ee/subscriptions/gitlab_com/#gitlab-saas-subscription)
1. [Seat Link](https://docs.gitlab.com/ee/subscriptions/self_managed/#seat-link)
1. [Product Category, Product Tier, Delivery](https://about.gitlab.com/handbook/marketing/strategic-marketing/tiers/#overview)


### Key Metrics, KPIs, and PIs

1. [Data Mart - Metric Definitions](https://docs.google.com/spreadsheets/d/1EhSXqx6YXcpqHg2TpS0ZN5Rk_d2hhrTPrW5FTbmuZjw/edit#gid=0)
1. [Event-based Metrics](https://docs.gitlab.com/ee/development/usage_ping/dictionary.html)
1. [User-based Metrics](https://docs.gitlab.com/ee/development/usage_ping/dictionary.html)
1. [Stage and Group Performance Indicators](https://about.gitlab.com/handbook/product/stage-and-group-performance-indicators/)
1. [ARR](https://about.gitlab.com/handbook/sales/sales-term-glossary/)


### Metric Formats

1. **User-based metrics**: # of users who performed an action/event
   - Last 28 days
   - Last 7 days
     - Example: "# of users who completed a merge request in the last 28 days"
1. **Event-based metrics**: # of [actions performed]
1. **Total counts** # of [events/attributes/users]
   1. Example: "# of runners" or "# of auto_devops_enabled projects"
1. **Indicator Metrics**: Whether an attribute is true or false
   1. Example: "Whether shared runners are enabled or not"
1. **Power user metrics**: # of users who did this action, and this action, and that action


## Self-Service Data Solution

### Self-Service Dashboard Developer

A great way to get started building charts in Sisense is to watch this 10 minute [Data Onboarding Video](https://www.youtube.com/watch?v=F4FwRcKb95w&feature=youtu.be) from Sisense. After you have built your dashboard, you will want to be able to easily find it again. Topics are a great way to organize dashboards in one place and find them easily. You can add a topic by clicking the `add to topics` icon in the top right of the dashboard. A dashboard can be added to more than one topic that it is relevant for. Some topics include Finance, Marketing, Sales, Product, Engineering, and Growth to name a few.

### Self-Service SQL Developer

#### Key Fields and Business Logic

- The Product Usage data sourced from GitLab SaaS and GitLab Self-Managed customer deployments is fed into the Enterprise Data Warehouse on a regular basis to be consumed by Gainsight and Salesforce.
- We utilize Usage Ping to derive self-managed customer usage data. Self-Managed customer product usage data is largely contained in the self-contained Usage Ping packets.
- The SaaS Customer Product Usage Data is rebuilt using source database tables.
- The Seat Link data encompasses license utilization data for all customers, regardless of type (self-managed or SaaS).
- The Aggregated metrics are collected in 7 and 28 day time frames are added into Usage Ping payload under the aggregated_metrics sub-key in the counts_weekly and counts_monthly top level keys.
- Aggregated metrics for all time frame are present in the count top level key, with the aggregate_ prefix added to their name.
- The underlying tables for Gainsight's consumption are built on the set of all Zuora subscriptions that are associated with a Self-Managed rate plans. Seat Link data from Customers DB is combined with high priority Usage Ping metrics to build out the set of facts included in this table.Tthe most recently received and the latest Usage Ping (by created_at date for a given subscription_id) and Seat Link (by dim_subscription_id) payload from each month are reported.


#### Entity Relationship Diagrams

| Diagram/Entity                                                                                              | Grain | Purpose | Keywords |
| ------------------------------------------------------------------------------------------------------------| ----- | ------- | -------- |
| [Product Usage Data ERD](https://lucid.app/lucidchart/232217df-3928-4756-bab5-ff5d9e9f8e1d/view?page=AD~qmCVo1T~c#) |  All of the below | Shows all table structures, including column name, column data type, column constraints, primary key, foreign key, and relationships between tables.| Customer, Usage Ping, Subscription, Seat Link, Self- Managed, SaaS, Product, Delivery, Accounts |


#### Reference SQL

| Snippet Library                                                                                                            | Description |
| -------------------------------------------------------------------------------------------------------------------------- | -------- |
| |  |

## Data Platform Solution

### Gainsight Data Pump

Data is sourced from GitLab SaaS and GitLab Self-Managed customer deployments.

#### EDW to Gainsight Data Pump:

The Data Team has leveraged the native capabilities in Gainsight to read data from the Snowflake Enterprise Data Warehouse. The Data Team has build a read-only mart-level table for Gainsight to access and it will contain all of the data currently available. Over time as the Data Team adds more metrics or customer segments, this table will automatically be refreshed with the additional data. This “interface” is called the `Gainsight Data Pump`.

#### Gainsight to Snowflake Data Pipeline:

The Data Team to develop a new source data pipeline from Gainsight into Snowflake to include new custom objects and data created in Gainsight to increase the usage ping match rate, among other improvements.

The diagram [Product Usage data developemental Streams](https://lucid.app/lucidchart/232217df-3928-4756-bab5-ff5d9e9f8e1d/view?page=UJ-bqxNqcUw2#)
illustrates our development approach for managing the delivery of Self-Managed and SaaS Product Usage to Gainsight.

### Data Lineage

The dbt solution generates a dimensional model that represents the flow of data through each of the tables from Source Models to Gainsight.

- A complete data lineage of the dbt models can be found at [Data Flow Diagram](https://lucid.app/lucidchart/232217df-3928-4756-bab5-ff5d9e9f8e1d/view)


## Trusted Data Solution

See overview at [Trusted Data Framework](https://about.gitlab.com/handbook/business-technology/data-team/platform/#tdf)

Kindly refer the [dbt guide examples](https://about.gitlab.com/handbook/business-technology/data-team/platform/dbt-guide/#trusted-data-framework) for
details and examples on implementing further tests.


### Product Usage Trusted Data Dashboard

A detailed Dashboard showing dbt tests, Source Model freshness, Record Counts, Last Run Dates, Golden records Validation etc.. This reports on latest Enterprise Dimensional model test and runs.

[(WIP) Product Usage Trusted Data Dashboard](https://app.periscopedata.com/app/gitlab/820568/WIP:-Product-Usage-Trusted-Data-Dashboard)


### RAW Source Data Pipeline validations

[Data Pipeline Health Validations](https://app.periscopedata.com/app/gitlab/715938/Data-Pipeline-Health-Dashboard)

