---
layout: handbook-page-toc
title: "LeanData"
---

## On this page
{:.no_toc .hidden-md .hidden-lg}

- TOC
{:toc .hidden-md .hidden-lg}

## Overview     
LeanData is an application used within Salesforce (SFDC) to process and assign [lead](#lead-routing-object) and [account](#account-routing-object) record types. LeanData allows for the creation of dynamic and complex record routing to support Go-to-Market (GTM) strategy.  

## Lead routing workflow
The LeanData lead routing flowbuilder can broken into three major sections: [record validation](#record-validation), [lead to account match](#lead-to-account-match) and [unmatched lead](#unmatched-lead). 

### Record validation
This initial phase reviews new and updated lead records to ensure they meet the criteria to route to an SDR. These checks include confirming the requirements below.
#### Leads were created by an admin user
#### Score thresholds are met
As of 2020-09-10, AMER, ABM and EMEA leads are eligible to route to aligned SDRs when their `Person Score` is greater than or equal to 0. APAC and LATAM leads are eligible to route when their `Person Score` is greater than 15.   
#### Company information is available
#### Last Interesting Moment listed does not require specialized routing or supression from SDR organization

### Lead to account match
Records that meet all [record validation](#record-validation) criteria and can be matched to an existing Salesforce account by LeanData are then assessed using the workflow below. If LeanData is able to identify the SDR responsible for engaging the lead, the record is assigned. If LeanData is not able to identify the aligned SDR, the lead progresses to the [unmatched lead](#unmatched-lead) workflow.
- **`SDR Assigned` match** - Used to route ABM, PubSec, APAC, EMEA Large and AMER Mid-Market leads. The custom account object field `SDR Assigned` is populated with SDR responsible for engaging and qualifying the lead.
- **Owner mapping available** - Used to route leads from `Named` accounts. Owner mappings are maintained within LeanData linking SDRs aligned to `Named` accounts with an account owner. If a lead is matched to an account with an owner mapping available, the record is assigned to the SDR listed in the owner mapping.
- **[TSP]-based alignment** - Used to route EMEA Mid-Market leads. LeanData uses a combination of `[TSP] Sub-Region`, `[TSP] Area` and `Account Owner` fields on matched accounts to route leads.

### Unmatched lead

### FlowBuilder   

#### `New Lead` Node 

1. `Created by Admin` = Records must be created by `Sales Admin` AND have `Person Score` < (greater  than) 15 points.
     1. Minimum of 15 points means the records has interacted with *at least* one piece of content, is a known name or provided a company-domained `Email`.
1. `Do Not Route? (New)` = Records must not have the `Do Not Route` checkbox checked.
2. `GitLab email address? (New)` = Records must not have an email that contains gitlab.com.
2. `Company Missing?` = if the `Company` field is empty or filled with a non-standard enrichment value, the workflow will send to `Standardize Company` node. 
     1. Accepted enrichable value is `[[unknown]]` OR **blank**.
     2. Any other value will render the field "filled" and enrichment solutions **will not** overwrite.
1. `LIM Suppression` = `Last Interesting Moment Desc` must not be equal to any currently suppressed value. 
1. `Matched Account` matches `Company Name` to any existing ACCOUNT with Salesforce (SFDC).  
     1. If matched records advances to `Route to Matched Account` which will leverage the [owner mapping](#owner-mapping) functionality or `SDR Assigned` listed on the account object to route the record to the designated SDR. 
     1. If ACCOUNT Owner is `Invalid`, `Inactive` or `Sales Admin` -> workflow will push record to `Sales Segment` node. 
1. `Sales Segment` - filter records based on segment (Large, Mid-market, SMB, Unknown), enriched on the SFDC record by our designated data sources. Explanation of how `Sales Segment` is determined can be found on the [Business Ops Resource page](/handbook/business-ops/resources/#segmentation)
     1. If `Large` => `Enterprise` this will route and filter based on the pairings for the Enterprise level SDRs. 
     1. If `Mid-Market` or `SMB` => `Commercial` this will further filter by `Region` then `Sales Segment` before ultimately routing to appropriate SDR team or Representative.
     1. If `Unknown` => progresses to next node.
1. `Employee Bucket` - specific forms on our website & in-product ask for end user to self-select **Number of Employees** in their company. This is a tertiary data point and is only used to route when no other information is available on the record.    
     1. If `2,000-9,999` or `10,000+` => `Enterprise` node which will further segment by `Region` and route to the correct Round Robin or Territory SDR. 
     1. If `1-99`, `100-499` or `500-1,999` => `Commercial` node which will further filter by `Region` then `Sales Segment` before ultimately routing to appropriate SDR team or Representative.
     1. If `Unknown` => routed to the `SDR Queue`
1. `SDR Queue` is managed by SDR Leadership and they are responsible for routing the records to their respective teams for research and follow up.   

## Account routing workflow
This workflow **is not** activated to run on a recurring basis. It only can be used on a one-time routing manual push at this time. 

![](/handbook/marketing/marketing-operations/leandata/20191212_LeanData_ACCOUNTflow.png)

## Territory Management 
 
The Territory Management capability aims to help sales and marketing teams execute go-to-market strategies that seamlessly automate complex territory lead routing and distribution.    

### Version 1.0 

Launched Version 1.0 of **Territory Management for ACCOUNTS** on 12 December 2019. Each of our three `Segments` (`Large`, `Mid-Market` and `SMB`) have a dedicated Territory spreadsheet which are only editable by the Sales & Marketing Operations teams.  

* [Large](https://docs.google.com/spreadsheets/d/1PYU8oQJQEPpi8K-SHuqSgPeSpLcWeSQd9FuwKtgD048/edit#gid=1172192878)
* [Mid-Market](https://docs.google.com/spreadsheets/d/1PYU8oQJQEPpi8K-SHuqSgPeSpLcWeSQd9FuwKtgD048/edit#gid=1477932297)
* [SMB](https://docs.google.com/spreadsheets/d/1PYU8oQJQEPpi8K-SHuqSgPeSpLcWeSQd9FuwKtgD048/edit#gid=1917614011)

Launched Version 1.0 of **Territory Management for SDR** on 20 December 2019. Each of the three `Segments` (`Large`, `Mid-Market` and `SMB`) have a dedicated Territory spreadsheet cloned from the above documents but modified to define `OwnerID` as an SDR or Round Robin matching the pairings.  

* [Large](https://docs.google.com/spreadsheets/d/1PYU8oQJQEPpi8K-SHuqSgPeSpLcWeSQd9FuwKtgD048/edit#gid=463255548)
* [Mid-Market](https://docs.google.com/spreadsheets/d/1PYU8oQJQEPpi8K-SHuqSgPeSpLcWeSQd9FuwKtgD048/edit#gid=1196243637)
* [SMB](https://docs.google.com/spreadsheets/d/1PYU8oQJQEPpi8K-SHuqSgPeSpLcWeSQd9FuwKtgD048/edit#gid=991220603)

### LEAD Territory Management Append Workflow

A dedicated workflow was created to append the Territory Management data to specific fields on the LEAD object that would not interfere with the regular LEAD workflow that handles inbound LEAD flow.  

Specific LeanData fields on the LEAD object in Salesforce related to Territory Management: 
- `LeanData Owner`
- `LeanData Territory`
- `LeanData Region`
- `LeanData Sub-Region`

![](/handbook/marketing/marketing-operations/leandata/20191222_LeanData_LEADtmflow.png)


#### Follow our [implementation process](https://gitlab.com/gitlab-com/marketing/marketing-operations/issues/84)
{:.no_toc}


### Product Documentation

* [**LeanData Datasheet**: Territory Management](http://info.leandatainc.com/DSTerritoryManagement_2Download.html)
* [**LeanData Blog**: Territory Management: Align Sales & Marketing on Revenue](http://learn.leandatainc.com/routing-rules-leandatas-sales-and-marketing-blog/territory-management-align-sales-marketing-on-revenue)


## Advanced Functions  

### Owner Mapping

Extracted from LeanData:  
> Map an existing account owner to a new account team owner in LeanData Router for leads routed to matched accounts. This is typically used by organizations with account teams where SDRs first qualify leads for account exec owners.

The [Sales Development team](/handbook/marketing/revenue-marketing/sdr/) is responsible for qualification of all records both inbound/outbound.   

Utilizing **Owner Mapping** an ACCOUNT owner (i.e. Strategic Account Leader (SAL)) can be mapped to a designated Sales Development Representative (SDR), which will route any matched records to the SDR for qualification before handing it off to a SAL.   

The **Owner Mapping** functionality is leverated in the `Route to Matched Account` node of the [LEAD workflow](#lead-workflow).  

More information about [Record Ownership](/handbook/business-ops/resources/#record-ownership). 

### Need to make a change to lead routing? 
Open an issue using our [LeanData change request issue template](https://gitlab.com/gitlab-com/marketing/marketing-operations/-/issues/new?issuable_template=leandata_change_sdralignment).