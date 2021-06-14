---
layout: handbook-page-toc
title: "Data Team Calendar"
description: "GitLab Data Team Calendar"
---
 
## On this page
{:.no_toc .hidden-md .hidden-lg}
 
- TOC
{:toc .toc-list-icons .hidden-md .hidden-lg}
 
{::options parse_block_html="true" /}
 
---
 
This page describes in detail the process of adding new data sources to the data warehouse. The Data Team embraces any initiative of adding new data sources towards our data warehouse. We envision that data could lead towards value, but adding new data towards the data warehouse does not go with no costs.
 
Both the development (assigning resources from the Data Team, from other teams involved to support and also you as requestor) and keeping the data pipeline up and running (storage, compute resources, software licensing, incident management, monitoring etc..) cost time and or money.
 
**Please, before request adding a new data source, take the following into account:**
- Is there a valid [business case](/handbook/business-technology/data-team/how-we-work/#data-team-value-calculator)?
   - Sometimes the business case is to comply with regulatory requirements.
   - Sometimes the business case is straightforward because value potential is clear above the investment costs.
   - Most of the time it’s hard to quantify, because either the value is unsure or the costs are unsure. Feel free to have an open and honest discussion with the Data Team. We have the experience and could help with the justification and this does not necessarily need to be a scientific calculation.
- Adding a new data source to the data warehouse is not a 1 off exercise. As soon as the data is extracted to the data warehouse, on a regular cadence (once week, once a day, multiple times per day, etc..) data will be refreshed. This means something can happen or can go wrong after the implementation. We will need a DRI from the source side to support this process when needed.
- The work is not done when data lands in the data warehouse. The data will land in the `raw` data layer, and this is not accessible by default for Sisense. Data will be loaded downstream into the [Enterprise Dimensional Model](/handbook/business-technology/data-team/edw/) (EDM) via dbt. Follow up needs to take place, and will come on top of the process described on this page.
   - Downstream modelling could be handled by the business team, because we embrace contribution on our data platform. Please note that extensive knowledge is needed ([dbt](/handbook/business-technology/data-team/dbt-guide/) knowledge, data modelling knowledge)
   - Downstream modelling could be handled by the Data Team. Planning needs to take place and priorities are set in line with company priorities. **This falls not within the scope of adding a new data source to the data warehouse.**
- Data could also be used, outside of the EDM. I.e. by a Function Analyst.
- When data ends up in the EDM, work is to be performed in [Sisense](/handbook/business-technology/data-team/platform/#visualization) by creating a dashboard. Also for doing this, some technical knowledge is required. 
- The data platform needs to get [access](/handbook/business-technology/data-team/platform/#data-team-access-to-data-sources) to the source system. Although this sounds obvious, this is not always straightforward.
 
## New data source
 
For adding a new data source, the workflow looks at follow (note, this is the [existing workflow](/handbook/business-technology/data-team/how-we-work/#workflow-summary) we use for all our work and made explicit here in the context of adding a new data source).
 
Process for adding a new data source:
 
| Stage (Label)               | Summery for new data source|
| --------------------------- | ------------------ |
| `workflow::1 - triage`      | All initial information will be provided by the requester and assessed by the Data Team |
| `workflow::2 - validation`  | A complete work breakdown for upcoming development will be created |
| `workflow::3 - scheduling`  | Once a month the Data Team OKRs are defined. Based on workload and priorities new data sources could be incorporated in the next quarter OKRs |
| `workflow::4 - scheduled`   | Adding a new data source is on the list of next quarter OKRs. An epic will be created with all the work breakdown activities attached |
| `workflow::5 - development` | Development is in progres |
| `workflow::6 - review`      | Development is under review |
| `workflow::X - blocked`     | Development is blocked |

### workflow::1 - triage
All new data source requests starts with an issue. Please use the `New Data Source` [template](https://gitlab.com/gitlab-data/analytics/-/blob/master/.gitlab/issue_templates/New%20Data%20Source.md). All initial information will be provided by the requestor and assessed by the Data Team. Cross check will be performed if the data doesn't already exist in the data warehouse.
 
### workflow::2 - validation
All details regarding the new data source will be flashed out.
 
#### Data scope
Based on the requirements, the data points that need to be extracted (i.e. which tables) will be determined. A total data scope must be given.
 
#### Extraction solution
The Data Team has different instruments available to extract data out of source systems (randomly ordered):
 
- Airflow
- Custom made via Python
- Fivetran
- Meltano
- Stitch
 
The decision for which instrument to use, is **always** based on the combination of:
1. Implementation effort
2. Maintenance effort
3. Extend effort
 
Its the Data Team that determines which instrument is used.
 
#### Work breakdown
End goal of the validation is to have a complete work breakdown, with DRI's and size estimation attached. All the work that needs to be performed is stated down. We aim to have it on a level, where every work action could be converted to an issue with no larger T-Shirt size than `M` / `5/8` issue poins.
 
#### Access request
Although it could be helpful to already provide the Data Team access to the source system, its not mandatory to raise an Access Request right now.
 
### workflow::3 - scheduling
Based on the business case, effort to implement, workload in the Data Team and Data Team priorities, the implementation will be scheduled. For scheduling we follow the GitLab Data Team Planning [Drumbeat](/handbook/business-technology/data-team/how-we-work/planning/). This means that for every quarter, the Data Team determines when a new data source request will be implemented. When a new data source request remains in `scheduling` this does not mean that it isn't on the radar of the Data Team. It means that it isn't been scheduled yet, because:
1. Defining the OKRs for the upcoming quarter didn't take place. Once a quarter the Data Team sets the OKRs for the next quarter.
2. It didn't fit in the OKRs for next quarter because of business case, effort to implement, workload in the Data Team and Data Team priorities.
 
### workflow::4 - scheduled
When a request for implementing a new data source is in scope for next quarter OKRs, the request is `scheduled`. An epic will be created with the issue attached to it. Based on the work breakdown all issues are created with the corresponding issue weight, label assigned `workflow::4 - scheduled`, the right milestone (if known) and attached to the epic.
 
### workflow::5 - development
When the execution of the work starts, the issue is in development and follows the regular development life cycle.
 
### workflow::6 - review
When the execution of the work is finished, the issue is in review and follows the regular development life cycle.
 
### workflow::X - blocked
When the execution could not continue due to the need of external intervention, the issue is `blocked`. There must be a clear problem statement given and the right people need to be assigned on the shortest notice possible.