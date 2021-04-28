---
layout: handbook-page-toc
title: "Data Team Planning Drumbeat"
description: "GitLab Data Team Planning Drumbeat"
---

## On this page
{:.no_toc .hidden-md .hidden-lg}

- TOC
{:toc .toc-list-icons .hidden-md .hidden-lg}

{::options parse_block_html="true" /}

# Data Team Planning Drumbeat
The Data Team Planning Drumbeat is a pre-set sequence that happens every quarter. The Planning Drumbeat follows GitLab's financial year/quarter structure. The Data Team Planning looks as follows:

![Planning Drumbeat](/handbook/business-technology/data-team/planning/Planning_Drumbeat.png) <br>
[link to orginal](https://docs.google.com/spreadsheets/d/1hdJqCfDPR-LqTTRBy4JEQ-MbrL-RyNHzXaMzvsGWkSQ/edit#gid=0)

Milestone naming convention; Milestone FYxx-Qxx-MSxx. I.e. FY22-Q02-MS01 <br>
LT = Leadership Team (`@rparker2`, `@iweeks`, `@dvanrooijen2`) <br>
DT = Data team (Product Fusion Team, GTM Fusion Team or Data Engineering Team)

The overall ambition is to **structure** why, when and what we are doing. 
- OKRs will lead to **why**
- Work breakdown will lead to **what**
- Milestone planning will lead to **when**

This top-down approach is leading, but not fully limited to the way we work. 

## Define next quarter OKRs
The Data Team OKRs aspire to align with Business Operations OKRs, Finance Division OKRs, and CEO OKRs, thereby aligning with the OKRs of the Divisions we support. Due to the nature of the the technical and data infrastructure work required to develop and operate an Enterprise Data Warehouse this will not always be the case.

By the end of a FQ, the Data Team will outline all actions that are required to succeed with our KRs and in helping other teams measure the success of their KRs. We do this via an issue in which everyone lays out all the steps they anticipate for each of the relevant actions. This is a great time for the team to raise any blockers or concerns they foresee. These should be recorded for future reference.

These OKRs drive ~60% of the work that the central data team does in a given quarter.
The remaining time is divided between urgent issues that come up and ad hoc/exploratory analyses.

Examples of OKR alignment _in-action_ includes:

1. [FY21-Q2 CEO](https://about.gitlab.com/company/okrs/fy21-q2/) Objective 2, aligns to [Data Team Objective 2](https://gitlab.com/groups/gitlab-com/business-ops/-/epics/80) for delivering automated data pipelines in support of Growth initiatives.
1. [FY21-Q2 CEO](https://about.gitlab.com/company/okrs/fy21-q2/) Objective 3, KR4 and KR5 align to [Data Team Objective 1](https://gitlab.com/groups/gitlab-com/business-ops/-/epics/79) to deliver a Finance ARR Data Mart.

## OKR Review
During the OKR Review, the Data Leadership Team reviews the current status of the current FQ KRs. The results of the OKRs are evaluated and propagated to next FQ OKRs where applicable.

## Work breakdown
The outcome of the work breakdown is a detailed description of the work to be performed, deliverables and responsibilities in the next quarter and is determined by:
1. Defined upcoming OKRs 
2. OKR Review
3. New / forward looking insights 
4. Team availability
5. Team member ambitions

The work breakdown is team effort and everyone is encouraged to contribute.

### T-Shirt Sizing Approach

We use a T-Shirt sizing approach for quickly sizing the work required to deliver new issues, epics, and longer-term initiatives. The T-Shirt sizing approach is designed to support work breakdowns towards the creation of detailed work plans, but also intended to provide a sufficient level of detail to manage overall scope.

| Size | Dedicated Person Time | Weight (issue points) | Examples | 
| :--: | :--: | :-- |
| XS | < 1/2 Day | 1 | Update existing handbook page. #data research/response. New Trusted Data Test.
| S | < 1 Day | 2-3 | New handbook page; typical triage issue; New dashboard on top of existing models. 
| M | 1 Week | 5-8 | New dashboard requiring new models. New data source with Stitch or Fivetran.
| L | 2-3 Weeks | 13 | New fact table implementation & testing. Full XMAU solution.
| XL | 1-2 Months | 26 | New Data Pump to new system. New Data Source with complex source API.
| XXL | 2-4 Months | 52+ | New Dimensional Model subject area with New Data Sources.


## Milestone Planning

Milestone planning takes place on Thursday and Friday ahead of every milestone. 

The data team works in two-week intervals, called milestones. 1 milestones per quarter will take three weeks long, because a quarter contains 13 weeks. The milestone that takes 3 weeks is the milestone that covers a major holiday or if the majority of the team is on vacation or at Contribute.

As work is assigned to a person and a milestone, it gets a weight assigned to it.

Milestone planning should take into consideration:

- vacation timelines
- conference schedules
- team member availability
- team member work preferences (specialties are different from preferences)
- OKRs

### Start / End
Milestones start on Tuesdays and end on Mondays.

### Midpoint
Any issues that are at risk of slipping from the milestone must be raised by the assignee during the Milestone Midpoint meeting. 

### Last day to submit MR
The last Friday prior to milestone end a MR can be submitted, but the merge of the MR will take place on Monday. No MRs are to be merged on Fridays, or on Thursday in the case of Family & Friends day. MRs must include documentation and testing to be ready to merge.

### Last day to merge MR 
This is the last day of the milestone and the last day a MR can be merged for the milestone.

### Milestone Meeting Day
Sync-meeting to perform retro perspective on the current milestone and align/start on the next milestone according to the created milestone planning.
All unfinished issues either need to be removed from milestones or rolled to the next
<br>[Roll Milestone](https://gitlab.com/gitlab-data/analytics/issues/new?issuable_template=Milestone%20Rolling)    

## Goal of Planning Drumbeat

The goal of this process is to improve our ability to plan and estimate work through better understanding of our velocity.

During the milestone planning process, we point issues.
Then we pull into the milestone the issues expected to be completed in the timeframe.
Points are a good measure of consistency, as milestone over milestone should share an average.
Then issues are prioritised according to these categories.

People will likely be working on no more than 2 issues at a time.

This approach has many benefits, including:

1. It helps ensure the highest priority projects are being completed
1. It can help leadership identify issues that are blocked
1. It provides leadership view into the work of the data team, including specialty analysts whose priorities are set from outside the data function
1. It encourages consistent throughput from team members
1. It makes clear to stakeholders where their ask is in priority
1. It makes clear to all team where their duty is in priority
1. It helps alleviate the pressure of planning the next milestone, as issues are already ranked

**The Planning drumbeat and execution is team-effort**
