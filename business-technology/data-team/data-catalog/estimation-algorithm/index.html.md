---
layout: handbook-page-toc
title: "Estimasted Algorithm"
---

## On this page
{:.no_toc}

- TOC
{:toc}

---

## Estimated Algorithm

For the Self-Managed instance that hosts our SaaS GitLab.com product, we get the accurate value via Usage Pings. For other Self-Managed instances, customers have the option to turn disable Usage Ping; therefore, we would not receive any usage statistics for that instance. In order to calculate estimated usage values across our Self Managed customers, we need to develop an algorithm to predict usage across instances who have disabled their Usage Ping.

This section explains our first attempt in these xMAU estimations.

### Current Methodology

**What we know ?**

* The number of Active subscriptions per month
* The number of Active subscriptions that send us a Usage Ping payload per month broken down by version
* The release date (therefore month) of a specific xMAU counter in Usage ping. For example we know that the `merge_requests_users` which is the GMAU of the Create - Source Code Group was released in version 12.9

**What we don't know ?**

* Number of Active Free Instances

**What we can do ?**

Let's discuss a real-life example! The counter used as SMAU for Dev:Create stage is `action_monthly_active_users_project_repo`. It was released on version 13.3. To calculate the Estimated SMAU we follow this process step-by-step:

* Calculate recorded GMAU split by delivery
* Calculate per month 
  * For October, we know we have 3500 subscriptions that sent us a Usage Ping Payload out of 5000 subscriptions
  * Among them we split between subscriptions that are on a version 13.3 or above and the ones which have 13.2 or below and the ones which don't send us any payload.
  * [This SiSense chart saw the split per month](https://app.periscopedata.com/app/gitlab/602123/Data-For-Product-Managers:-Supporting-Dashboard?widget=10065654&udv=953103)
* We get from the chart above a % of subscriptions that send us payloads and that are on 13.4 or above out of all Active Subscriptions
* We then deduce that Estimated SMAU = Recorded SMAU / % on 13.3

Since counters are released on different GitLab version, the estimation is customised form one counter to another. 

This number is actually a quite accurate number to estimate paid XMAU but can be used at first for calculating estimated xMAU. Though we can imagine several improvements in order to make this estimator more robust:

* The first improvement would be to use the sum of the seat quantity ordered instead of the number of subscriptions.
* We could also break down the estimator per plan (current problem: a subscription can have 2 instances from 2 different product tiers)
* A major area of improvement is regarding our Core estimation. We currently assume that we have the same patterns between paid and free in terms of version upgrade and usage ping opt-in. While usage ping opt-in rate estimation seems very complicated to improve an critical area of improvement would be around version upgrade and usage data trend for Core Instances
