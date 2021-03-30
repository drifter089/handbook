---
layout: handbook-page-toc
title: "WIP Email Marketing Data Mart"
---
## On this page

- TOC
{:toc}

{::options parse_block_html="true" /}

---
## Email Marketing Data Mart

Coming soon

The goal of this page:

* Help you to use the [TD: Email Marketing Data Mart README](https://docs.google.com/spreadsheets/d/1z0-QQbudAYU3pYS5CrdQMoyLxMipbx0rQzKTjx6AEZo/edit#gid=1701629744) to generate email campaigns.
* Help you understand the data models used to create the TD: Email Marketing Data Mart.
* `Coming Soon` Assess your understanding by taking a certification most applicable to your role at GitLab.
* And overall help everyone contribute!

### Quick Links
<div class="flex-row" markdown="0" style="height:80px">
  <a href="https://docs.google.com/spreadsheets/d/1z0-QQbudAYU3pYS5CrdQMoyLxMipbx0rQzKTjx6AEZo/edit#gid=1701629744" class="btn btn-purple" style="width:33%;height:100%;margin:5px;float:left;display:flex;justify-content:center;align-items:center;">README - TD: Email Marketing Database</a>
<a href="https://lucid.app/lucidchart/12ee91c1-7ae5-4e99-96ae-bc51652dfa19/edit?page=kW05tjmZX.Hv#" class="btn btn-purple" style="width:33%;height:100%;margin:5px;float:left;display:flex;justify-content:center;align-items:center;">ERD - TD: Email Marketing Database</a>
</div>
<br><br><br><br><br><br><br><br><br>

<style> #headerformat {
background-color: #6666c4; color: black; padding: 5px; text-align: center;
}
</style>
<h1 id="headerformat">Getting Started </h1>

To get started we want to make sure you understand:

* Key terms that will explain how we account for the metrics
* The data sources behind the database

<style> #headerformat {
background-color: #6666c4; color: black; padding: 5px; text-align: center;
}
</style>
<h1 id="headerformat">Key Terms, Key Fields, and Business Logic </h1>

<details>
<summary markdown='span'>
  Key Terms
</summary>
Dimensions:

* Sales Segment
* Sales Region
* Product Tier
* Product Delivery
* User Role
* Subscription Start and End Dates
* Trial Start and End Dates

</details>

<details>
<summary markdown='span'>
  Key Metrics, KPIs, and PIs
</summary>
Facts:

* Usage Ping
* Days until trial ends

</details>

<details>
<summary markdown='span'>
  Key Fields and Business Logic
</summary>
* The grain of the Email Marketing Data Mart is one row per unique email address. There is a one to many relationship between each email address and different dimensions such as product tier, product delivery, and subscriptions. Therefore, in the Data Mart, we have used aggregation logic to create fields to describe the email addresses. For example, there are fields named `group_owner_of_saas_premium_tier` and `group_owner_of_saas_ultimate_tier` which are boolean fields. It is possible that a group owner could have a TRUE value for both of these fields if they are owners of both a Premium and Ultimate plan. 
</details>

<style> #headerformat {
background-color: #6666c4; color: black; padding: 5px; text-align: center;}
</style>
<h1 id="headerformat">Understanding the Data Sources and Data Models</h1>
<br>

Data Sources:

* Zuora
* Salesforce
* GitLab.com
* Customers DB

Entity Relationship Diagram (ERD):

<div style="width: 640px; height: 480px; margin: 10px; position: relative;"><iframe allowfullscreen frameborder="0" style="width:640px; height:480px" src="https://lucid.app/documents/embeddedchart/12ee91c1-7ae5-4e99-96ae-bc51652dfa19" id="8DUnoPlKNRCA"></iframe></div>


<details>
<summary markdown='span'>
  Data Lineage
</summary>
* The dbt solution generates a dimensional model from RAW source data. The documentation and SQL for <a href = "https://dbt.gitlabdata.com/#!/model/model.gitlab_snowflake.mart_marketing_contact#code">mart_marketing_contact can be found here </a>, and the complete data lineages can be found at <a href = "https://dbt.gitlabdata.com/#!/model/model.gitlab_snowflake.mart_marketing_contact?g_v=1&g_i=%2Bmart_marketing_contact%2B"> dbt mart_marketing_contact lineage chart </a>
</details>

<details>
<summary markdown='span'>
  Example Queries
</summary>
Let's pull some email lists. You can use these queries in both Snowflkae and Sisense.
<br>
```
--Pull ALL owners and individual namespaces for Paid SaaS Plans
SELECT DISTINCT 
  email_address
FROM "PREP"."SENSITIVE"."MART_MARKETING_CONTACT"
WHERE GROUP_OWNER_OF_SAAS_BRONZE_TIER = TRUE
  OR GROUP_OWNER_OF_SAAS_PREMIUM_TIER = TRUE
  OR GROUP_OWNER_OF_SAAS_ULTIMATE_TIER = TRUE
  OR INDIVIDUAL_NAMESPACE_IS_SAAS_BRONZE_TIER
  OR INDIVIDUAL_NAMESPACE_IS_SAAS_PREMIUM_TIER
  OR INDIVIDUAL_NAMESPACE_IS_SAAS_ULTIMATE_TIER
```

</details>
<br>



<style> #headerformat {
background-color: #6666c4; color: black; padding: 5px; text-align: center;
}
</style>
<h1 id="headerformat">Additional Resources </h1>

<details>
<summary markdown='span'>
  Trusted Data Solution
</summary>

Coming Soon

</details>

<details>
<summary markdown='span'>
  EDM Enterprise Dimensional Model Validations
</summary>
The [(WIP) Enterprise Dimensional Model Validation Dashboard](https://app.periscopedata.com/app/gitlab/760445/WIP:-Enterprise-Dimensional-Model-Validation-Dashboard) reports on latest Enterprise Dimensional model test and runs.
</details>

<details>
<summary markdown='span'>
  RAW Source Data Pipeline validations
</summary>
[Data Pipeline Health Validations](https://app.periscopedata.com/app/gitlab/715938/Data-Pipeline-Health-Dashboard)
</details>

<details>
<summary markdown='span'>
  Data Security Classification
</summary>


**ORANGE**

- Description: Customer and Personal data at the row or record level.
- Objects:
  
**YELLOW**

- Description: 
- Objects:
 
</details>

<details>
<summary markdown='span'>
  Solution Ownership
</summary>
* Source System Owner:
  * Salesforce: `@jbrennan1`
  * Zuora:
  * GitLab.com
  * Customers DB
* Source System Subject Matter Expert:
  * Salesforce: `@jbrennan1`
  * Zuora:
  * GitLab.com
  * Customers DB
* Data Team Subject Matter Expert: `@jeanpeguero` `@jjstark` `@iweeks`
</details>

