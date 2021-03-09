---
layout: handbook-page-toc
title: "Using Product Usage Data in Gainsight"
description: "Effective ways to apply product data for Sales and Customer Success teams to support their customers' top initiatives and business objectives."
---

### Vision

To align to our GitLab values of Efficiency, Results, Transparency, and Iteration, Product Usage Data will be accessible in:

1. Short-term: Our GTM systems (Salesforce, Gainsight, and Marketo) to enable effective outcomes by supporting the customer where _they_ are at in their customer journey
1. Short-term: GitLab accessible dashboards (Sisense) for high level overviews and trend analyses
1. Long-term: The GitLab product to enable customers to self-serve and develop their own analytics — this will be accomplished by the Product Analytics (Product) team's initiatives

### Using Product Usage Data in Gainsight 

**Note**: for License Usage, see [License Usage Salesforce App](/handbook/sales/field-operations/sales-systems/license-usage-app/) and [License Usage in Gainsight](/handbook/customer-success/tam/gainsight/license-usage/).

For the overall 3-year vision, see [Project Compass #15 Vision](https://gitlab.com/groups/gitlab-com/-/epics/1247). FY22-Q1 will have self-managed only. 

### Data Integration

Data will be integrated from Snowflake —> Gainsight on a monthly basis. Over time, this will move to bi-weekly and then weekly.

### Ways to Use These Metrics

There will be several limitations with the MVC deployment; however, as you come across use cases, please [open an issue](https://gitlab.com/gitlab-com/sales-team/field-operations/customer-success-operations/-/issues) or [request a new metric](/#requesting-new-metrics). Here are several potential use cases for utilizing data:

#### Understanding The Basics of My Customer's Usage

With data syncing to Gainsight, we can quickly and easily look up an account and see instances (note: this data is currently limited to self-managed customers only) where we are receiving their data. Use this to see all instances related to your account (Production and non-Production) and their activity. NOTE: this only works for instances that are tied to an active subscription. 

* Who is sending us their usage ping data?
* Are they sending Production data?
* Is their activity in line with my expectations? Does the activity found in the product usage data agree with what I know about their usage?


#### How Active Is My Customer?

  While we can use License Usage (see above) to understand the activated seats vs. licensed seats, [Unique Monthly Active Users (UMAU)](/handbook/product/performance-indicators/#unique-monthly-active-users-umau) can help assess how many of those activated licenses are currently being used. For example, a customer may have 1,000 users "activated" but only 700 of them are logging in. That can highlight a risk.

  #### Understanding My Customer's GitLab Adoption  

  As an MVC, use metrics mapped to use cases SCM (Create), CI (Verify), and DevSecOps (Secure) to understand their adoption. See the [GitLab Adoption Journey](/handbook/customer-success/vision/#high-level-visual-of-gitlab-adoption-journey) for an explanation on the adoption of SCM, CI, and Secure. 

  Remember, this is an MVC — please [create an issue to suggest new metrics](/#requesting-new-metrics), different ways to evaluate the customer's journey, or other ideas.

  | Use Case (Stage)   | Purpose / Adoption Level | Description                                                  |
  | ------------------ | ------------------------ | ------------------------------------------------------------ |
  | SCM (Create)       | Basic Adoption           | Is my customer using the basic toolset? Most customers should adopt these features pretty quickly into their GitLab journey |
  | CI (Verify)        | Product Stickiness       | As part of their continued adoption and customer journey, we want to help our customers adopt CI, as well as helping their central DevOps teams to better understand their organization's adoption of CI. Use these metrics to help determine progress towards adoption |
  | DevSecOps (Secure) | Enablement & Expansion   | Finally, for customers using our security features or who are trialing and wanting to [shift left](https://about.gitlab.com/blog/2020/06/23/efficient-devsecops-nine-tips-shift-left/), use these metrics to help identify adoption and track growth |


  ### TAM Actions

  As a TAM, you are responsible to:
  1. For your self-managed customers, label your customers' instances as Production, Staging, or Obsolete (process TBD)


  ### Field Definitions

  The Product Stage definitions have been extracted from the [Metrics Dictionary](https://docs.gitlab.com/ee/development/usage_ping/dictionary.html). For more information on Stage metrics, please review the dictionary.

  Eventually, the metrics list and definitions will be embedded directly in the handbook. As a first iteration, the list of metrics and their definitions are in the [Data Mart - Table Definitions](https://docs.google.com/spreadsheets/d/1EhSXqx6YXcpqHg2TpS0ZN5Rk_d2hhrTPrW5FTbmuZjw/edit#gid=0) spreadsheet.

  See our technical documentation for our [instance of Gainsight's Adoption Explorer](https://docs.google.com/document/d/1TvSCT_yj73AS0PuLxPonuF5QHWyM3dqG_i8H1U1cwf0/edit).

  ### Requesting New Metrics 

  To request a new metric, please open an issue in the [Product Analytics project](https://gitlab.com/gitlab-org/product-analytics/-/issues/new) and at-mention Product Analytics PM. You can see [Add per project count](https://gitlab.com/gitlab-org/product-analytics/-/issues/425) as an example. However, before you create an issue, please confirm the metric does not already exist in the [Event Dictionary](https://docs.google.com/spreadsheets/d/1VzE8R72Px_Y_LlE3Z05LxUlG_dumWe3vl-HeUo70TPw/edit#gid=618391485&fvid=1422977269). 

  Examples of new metrics can include:

  * Tracking a new feature
  * Looking at feature use in a different context (raw count, activity per user, per project, etc.)
  * Expanding an existing metric to track usage at different product tiers (e.g., specifically tracking the feature component used in Core vs. a paid tier)


  ### Reference documentation

  * [Metrics Dictionary](https://docs.gitlab.com/ee/development/usage_ping/dictionary.html)
  * [Adoption Explorer - GitLab Documentation](https://docs.google.com/document/d/1TvSCT_yj73AS0PuLxPonuF5QHWyM3dqG_i8H1U1cwf0/edit)
  * [SaaS-Activity Dashboard](https://app.periscopedata.com/app/gitlab/684495/WIP---SaaS-Activity)
  * [High-Level Visual of GitLab Adoption Journey](/handbook/customer-success/vision/#high-level-visual-of-gitlab-adoption-journey)

  


