---
layout: handbook-page-toc
title: "Using Product Usage Data in Gainsight"
description: "Effective ways to apply product data for Sales and Customer Success teams to support their customers' top initiatives and business objectives."
---

## On this page
{:.no_toc .hidden-md .hidden-lg}

- TOC
{:toc .hidden-md .hidden-lg}

{::options parse_block_html="true" /}

---

## Purpose

To guide users in how to use the customer's product usage data within Gainsight, review use case adoption strategies, and understand how the data connects and what to do with data quality concerns.

## Using Product Usage Data in Gainsight 

For video overviews, see:

<!-- blank line -->
<figure class="video_container">
  <iframe src="https://www.youtube.com/embed/5_J9Kfbu5JA" frameborder="0" allowfullscreen="true"> </iframe>
</figure>
<!-- blank line -->

- [Product Usage Data - video overview](https://youtu.be/5_J9Kfbu5JA)
- [Health Measures and Data Quality](https://www.youtube.com/watch?v=XQCGKL4XF_o)

**Note**: for License Usage, see [License Usage Salesforce App](/handbook/sales/field-operations/sales-systems/license-usage-app/) and [License Usage in Gainsight](/handbook/customer-success/tam/gainsight/license-usage/).

For the overall 3-year vision, see [Project Compass #15 Vision](https://gitlab.com/groups/gitlab-com/-/epics/1247). FY22-Q1 will have self-managed only. 

### Quick Links
<div class="flex-row" markdown="0" style="height:80px">
  <a href="https://docs.gitlab.com/ee/development/usage_ping/dictionary.html" class="btn btn-purple" style="width:33%;height:100%;margin:5px;float:left;display:flex;justify-content:center;align-items:center;">Metrics Dictionary</a>
  <a href="https://docs.google.com/document/d/1TvSCT_yj73AS0PuLxPonuF5QHWyM3dqG_i8H1U1cwf0/edit" class="btn btn-purple" style="width:33%;height:100%;margin:5px;float:left;display:flex;justify-content:center;align-items:center;">Product Usage Data: Gainsight Technical Documentation</a>
  <a href="https://app.periscopedata.com/app/gitlab/803470/WIP:-Customer-Product-Adoption-Dashboard" class="btn btn-purple" style="width:33%;height:100%;margin:5px;float:left;display:flex;justify-content:center;align-items:center;">WIP: Customer Product Adoption Dashboard</a>
  <a href="/handbook/product/product-intelligence-guide/" class="btn btn-purple" style="width:33%;height:100%;margin:5px;float:left;display:flex;justify-content:center;align-items:center;">Product Intelligence Overview</a>
  <a href="https://about.gitlab.com/handbook/business-technology/data-team/data-catalog/product-usage-data/" class="btn btn-purple" style="width:33%;height:100%;margin:5px;float:left;display:flex;justify-content:center;align-items:center;">Product Usage Data - Data Team Handbook</a>
</div>
<br><br><br>



## Gainsight Reports and Dashboards

Use the [Product Usage Data Dashboard](https://gitlab.gainsightcloud.com/v1/ui/home#9d75e4c5-d770-4c78-a0d5-d4f568083987) to see the full list of your accounts. Once on the C360, 


| Report Name | Description | Application |
| ------ | ------ | ------ |
| **License Utilization (Seat Link)** | current, high level license utilization statistics | Use this to quickly identify the depth of adoption, if the account is Reporting  |
| **License Utilization Trends (Seat Link)** | Week-over-Week license utilization trend charts | Useful for understanding if and how much the customer is adding or removing licenses |
| **Monthly Distilled Metrics (Usage Ping)** | Contextually-based metrics to graph the adoption percentage of the account (e.g., users who ran a pipeline divided by monthly active users). | Metrics to help the account team understand monthly use case and license usage to assess for expansion or enablement decisions. Toggle through the different reports to see different graphs. |
| **Monthly Use Case Trends (Usage Ping)** | Month-over-Month trend analyses for use cases such as CI or SCM | Monthly data points for use case-specific metrics. To be used to help the account team learn feature and deployment depth and adoption — use this in conjunction with the Monthly Distilled Metrics. Toggle through the reports to analyze the top metrcs on a per use case basis. |
| **Instance Details (Usage Ping)** | List of all instances related to the account with `Instance Type` meta data | Use [Updating Self Managed Instance Type to update the hostname](#updating-self-managed-instance-type) |


## Ways to Use These Metrics

There will be several limitations with the MVC deployment; however, as you come across use cases, please [open an issue](https://gitlab.com/gitlab-com/sales-team/field-operations/customer-success-operations/-/issues) or [request a new metric](#requesting-new-metrics). Here are several potential use cases for utilizing data:

### Understanding The Basics of My Customer's Usage

With data syncing to Gainsight, we can quickly and easily look up an account and see instances (note: this data is currently limited to self-managed customers only) where we are receiving their data. Use this to see all instances related to your account (Production and non-Production) and their activity. NOTE: this only works for instances that are tied to an active subscription. 

* Who is sending us their usage ping data?
* Are they sending Production data?
* Is their activity in line with my expectations? Does the activity found in the product usage data agree with what I know about their usage?


### How Active Is My Customer?

While we can use License Usage (see above) to understand the activated seats vs. licensed seats, [Unique Monthly Active Users (UMAU)](/handbook/product/performance-indicators/#unique-monthly-active-users-umau) can help assess how many of those activated licenses are currently being used. For example, a customer may have 1,000 users "activated" but only 700 of them are logging in. That can highlight a risk.

### Understanding My Customer's GitLab Adoption  

As an MVC, use metrics mapped to use cases SCM (Create), CI (Verify), and DevSecOps (Secure) to understand their adoption. Use the [Use Case Adoption](/product-usage-data/use-case-adoption/) guide for specific definitions around whether a customer has adopted a specific stage. See the [GitLab Adoption Journey](/handbook/customer-success/vision/#high-level-visual-of-gitlab-adoption-journey) for an explanation on the adoption of SCM, CI, and Secure. 

Remember, this is an MVC — please [create an issue to suggest new metrics](#requesting-new-metrics), different ways to evaluate the customer's journey, or other ideas.

| Use Case (Stage)   | Purpose / Adoption Level | Description                                                  |
| ------------------ | ------------------------ | ------------------------------------------------------------ |
| SCM (Create)       | Basic Adoption           | Is my customer using the basic toolset? Most customers should adopt these features pretty quickly into their GitLab journey |
| CI (Verify)        | Product Stickiness       | As part of their continued adoption and customer journey, we want to help our customers adopt CI, as well as helping their central DevOps teams to better understand their organization's adoption of CI. Use these metrics to help determine progress towards adoption |
| DevSecOps (Secure) | Enablement & Expansion   | Finally, for customers using our security features or who are trialing and wanting to [shift left](https://about.gitlab.com/blog/2020/06/23/efficient-devsecops-nine-tips-shift-left/), use these metrics to help identify adoption and track growth |


## TAM Actions

### Updating Self-Managed Instance Type
For your self-managed customers, label your customers' instances as Production, Staging, or Obsolete. Steps:
1. Go to the customer in Gainsight
1. On the left nav panel, click on "Instance Details" (bottom)
1. Click on the ✏️ icon for the instance you want to update
1. For the field "Instance Type" select the proper option

NOTE: Anything labeled as "Unknown" should be treated as a _temporary_ holding title that needs to be updated to Production, Non-Production, or Obsolete.


## Field Definitions

The Product Stage definitions have been extracted from the [Metrics Dictionary](https://docs.gitlab.com/ee/development/usage_ping/dictionary.html). For more information on Stage metrics, please review the dictionary.

Eventually, the metrics list and definitions will be embedded directly in the handbook. As a first iteration, the list of metrics and their definitions are in the [Data Mart - Table Definitions](https://docs.google.com/spreadsheets/d/1EhSXqx6YXcpqHg2TpS0ZN5Rk_d2hhrTPrW5FTbmuZjw/edit#gid=0) spreadsheet.

See our technical documentation for our [instance of Gainsight's Adoption Explorer](https://docs.google.com/document/d/1TvSCT_yj73AS0PuLxPonuF5QHWyM3dqG_i8H1U1cwf0/edit).

## Data

### Data Integrations

Data will be integrated from Snowflake —> Gainsight on a monthly basis. Over time, this will move to bi-weekly and then weekly.

![Product Usage Data Flow Diagram](https://lucid.app/publicSegments/view/cba91861-d0aa-4f96-8848-56a2eec5798b/image.jpeg)

### Data Sources and Application

Below are the various data sources, their definitions, and uses.

### Triaging Data Quality

* Seat Link: Use the [License Usage reporting bad data](https://about.gitlab.com/handbook/customer-success/tam/gainsight/license-usage/#reporting-bad-data) process
* Usage Ping: 
   1. Confirm with CS Operations whether the data quality issue is specific to Gainsight or upstream (post in #gainsight-users)
   1. If the data quality issue is upstream, create a data quality issue in the [Data project](https://gitlab.com/gitlab-data/analytics/-/issues)
      1. Attach to the [data quality epic](https://gitlab.com/groups/gitlab-data/-/epics/216)
      1. Please include screenshots for troubleshooting and _mark issue as confidential_

##### Usage Ping (self-managed)

We utilize Usage Ping to derive self-managed customer usage data. For more details, see [Usage Ping FAQs](/handbook/customer-success/tam/usage-ping-faq/). Any references to "Usage Ping" in Gainsight explicitly refers to self-managed product usage data (licenses + feature use).

##### SaaS (Snowplow))

We are targeting SaaS product usage data in FY22-Q2.

##### Seat Link

Seat Link data encompasses license utilization data for **all** customers, regardless of type (self-managed or SaaS). Limitations:
1. For privacy reasons, we do not collect the hostname (see [blog post](https://about.gitlab.com/blog/2020/03/16/how-were-improving-self-managed-billing/)) or other instance meta data. Instead, the highest reporting instance for a given subscription is displayed
1. Seat Link does **not** have product usage data; it only counts licenses

## Requesting New Metrics 

To request a new metric, please open an issue in the [Product Analytics project](https://gitlab.com/gitlab-org/product-analytics/-/issues/new) and at-mention Product Analytics PM. You can see [Add per project count](https://gitlab.com/gitlab-org/product-analytics/-/issues/425) as an example. However, before you create an issue, please confirm the metric does not already exist in the [Event Dictionary](https://docs.google.com/spreadsheets/d/1VzE8R72Px_Y_LlE3Z05LxUlG_dumWe3vl-HeUo70TPw/edit#gid=618391485&fvid=1422977269). 

Examples of new metrics can include:

* Tracking a new feature
* Looking at feature use in a different context (raw count, activity per user, per project, etc.)
* Expanding an existing metric to track usage at different product tiers (e.g., specifically tracking the feature component used in Core vs. a paid tier)
