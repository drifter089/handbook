---
layout: handbook-page-toc
title: "Go-To-Market Technical Documentation"
---
## On this page
{:.no_toc .hidden-md .hidden-lg}

- TOC
{:toc .hidden-md .hidden-lg}

## How to use this documentation

The Documentation below is organized by Feature, each section will have the relevant inputs and outputs as well as references to the logic that processes the input and outputs.

---

## ARR

Please see the dedicated [ARR Technical Documetation Page](https://about.gitlab.com/handbook/sales/field-operations/sales-systems/gtm-technical-documentation/sfdc-booking-metric-fields/)

## Gainsight

Please see the dedicated [Gainsight Technical Documentation Page](/handbook/sales/field-operations/sales-systems/gtm-technical-documentation/gainsight/)

## Territory Success Planning

**Business Process this supports:** [Territory Success Planning](/handbook/sales/field-operations/sales-operations/#territory-success-planning-tsp)

**Overview:** The goal of TSP is to keep a set of staging fields consistently up to date from a variety of data sources, then at given intervals copy these values to the "Actual" set of fields for general use. This allows for us to constantly receive changes but only apply those changes in a controlled fashion. This also allows us to easily track exceptions. Note: This project was originally referred to as ATAM, which is why the API names of the fields reference that instead of TSP.

**Logic Locations:** [AccountJob.cls](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/blob/master/force-app/main/default/classes/AccountJob.cls)
Code Units:
* highestEmpsAndTSPAddress
* ownerTransfer

**Inputs:** DataFox, Zoominfo, Manually Entered Address & Employee Data, Account Parenting Hierarchy

**Outputs:** Here is the outline between two sets of fields we are setting on the Account object. Staging(TSP / ATAM) are set nightly via an APEX job. Actuals are set at given intervals found in the business documentation.

| **Data Name**     | **Actual - Field API Name**                  | **TSP - Field API Name**        |
|---------------|--------------------------------------------|-----------------------------|
| Owner         | Owner                                      | ATAM_Approved_Next_Owner__c |
| Owner Role    | Owner.Role                                 | ATAM_Next_Owner_Role__c     |
| Owner Team    | Account_Owner_Team__c                      | ATAM_Next_Owner_Team__c     |
| Sales Segment | Ultimate_Parent_Sales_Segment_Employees__c | JB_Test_Sales_Segment__c    |
| Territory     | Account_Territory__c                       | ATAM_Territory__c           |


## Contact Ownership

**Business Process this supports:** This supports our [contact ownership rules](/handbook/sales/field-operations/gtm-resources/#changing-contact-ownership-in-salesforce)

**Overview:** The goal of the Contact Ownership code is to ensure that contacts are owned by the appropriate user within salesforce in an automated fashion so that contact ownership is maintained without any work needed by team members. 

**Logic Locations:** [ContactJob](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/blob/master/force-app/main/default/classes/ContactJob.cls)
Code Units:
* maintainContactOwnership

**Inputs:** Contact Owner, Account Owner, Account SDR Assigned, Account Type, Sales Segment

**Outputs:** Contact Owner


## Salesforce Record Sharing And Visibility Settings 

**Business Process this supports:** Security and compliance requirements for federal customers

**Overview:** The goal of our record sharing settings in Salesforce is so that the Public Sector Team and approved supporting functions can view public sector records. A Public Sector record is considered any record in Salesforce that is owned by the Public Sector team. This is accomplished by the use of sharing rules and groups within Salesforce. If a record is owned by a member of the Public Sector Group then that record is only shared and visible to other members of the Public Sector Group. If the record is owned by anyone other than a member of the public sector group, then that record is visible to all internal users within our Salesforce Instance. Membership to these applicable groups is controlled by System Administrators and Sales Operations.  

**Logic Locations:** 
* [Salesforce Object Sharing Settings](https://gitlab.my.salesforce.com/p/own/OrgSharingDetail?setupid=SecuritySharing&retURL=%2Fui%2Fsetup%2FSetup%3Fsetupid%3DSecurity)
* [Public Groups in Salesforce](https://gitlab.my.salesforce.com/p/own/OrgPublicGroupsPage/d?setupid=PublicGroups&retURL=%2Fui%2Fsetup%2FSetup%3Fsetupid%3DUsers)


## Quote Approval System

**Business Process this supports:** Discount Approvals

**Overview:** According to the [Deal Approval Matrix](https://docs.google.com/document/d/1-CH-uH_zr0qaVaV1QbmVZ1rF669DsaUeq9w-q1QiKPE/edit) Quotes must have discounts approved by different management levels depending on discount percentage and term length. To achieve this, we have written automation to stamp a quote with each potential approver, revised the code that determines which approvals are required, and revised the actual approval process in Salesforce.

**Quote Management Stamp** When a Quote is inserted, get the owner of the related Opportunity. Then, find the manager of the owner and the manager of the manager for each manager, five managers down. Record the first active Regional Director, Area Sales Manager, and Vice President on the Quote. These lookup fields will be used in the Approval Process, if needed.

**Quote Approval Code** This is a table of the Quote (API Name: zqu__Quote__c) fields that trigger quoteApprovals to recalculate and what must happen to them.

|**Field API Name**|    **What Must Happen**|
|----|----|
|Rate_Plan_Count__c|Change|
|zqu__Previewed_TCV__c|Change|
|zqu__Previewed_SubTotal__c|Change|
|zqu__Previewed_Discount__c|Change|
|Non_Standard_Contract_Terms__c|Change|
|Reseller_PO_Status__c|Change|
|zqu__PaymentTerm__c|Change|
|zqu__Previewed_Total__c|Change|
|zqu__Previewed_Discount__c|Change|
|Quote_Amendment_Last_Modified_Date__c|Change|
|zqu__InitialTerm__c|Change|
|zqu__RenewalTerm__c|Change|
|X_Trigger_Quote_Approval_Check__c|Become true|

If any of these events happen, all "Required_Approvals" fields (Required_Approvals_From_CEO__c, Required_Approvals_From_CFO__c, Required_Approvals_From_CRO__c, Required_Approvals_From_CS__c, Required_Approvals_From_Legal__c, Required_Approvals_From_VP_of_Channel__c, Required_Approvals_From_VP_of_Sales_RD__c, Required_Approvals_From_RD__c, Required_Approvals_From_ASM__c) are cleared. These are the rich text area fields that show which management levels need to approve the Quote on the page layouts.
Then, all relevant Quote Rate Plan Charges (API Name: zqu__QuoteRatePlanCharge__c) related to the Quote are queried, these are what hold the term, product, and discount information we need to determine what approvals are required. Following the [Deal Approval Matrix](https://docs.google.com/document/d/1-CH-uH_zr0qaVaV1QbmVZ1rF669DsaUeq9w-q1QiKPE/edit), we determine what level of management the Quote Rate Plan Charge needs and stamp the correct "Required_Approvals" fields with the discount percentage, type, and term. Similar logic is then run for any Quote Rate Plan Charges related to Professional Services products.
Finally, the Quote's Approval_Stage__c field records whether it needs approval, doesn't need approval, or has been approved.

**Quote Approval Process**
This utilizes Salesforce's built-in Approval Process functionality.
We have two Approval Processes for Zuora Quotes, the first for undiscounted, and the other for ones with discounts.
The Quote must be submitted using the "Submit for Approval" button on the page layout to enter the correct Approval Process.
* Undiscounted Approval Process
    * If the Quote's Approval Stage is "Approvals Not Required" or null, the Approval Stage is updated to "In Review" and the Owner of the Quote is emailed confirming submission for approval. Then, if there are any Special Terms and Notes or has been flagged as Requires Deal Desk Review, a member of the Deal Desk team must approve. If neither of those are true, the deal auto-approves. Upon approval, the Owner of the Quote is emailed to inform them of the approval and the Approval Stage is updated to "Approved". If the Quote is rejected, the Approval Stage is set to "Rejected" and the Owner is emailed informing them.
* Discounted Approval Process
    * If the Quote's Approval Stage is "Approvals Required" or "Rejected", the Approval Stage is updated to "In Review" and the Owner of the Quote is emailed confirming the submission for approval. Then, based on the "Required_Approvals" fields, the Quote waits for approval by the people in that step. Once all approvals are acquired, the Approval Stage is set to "Approved" and the Owner of the Quote is emailed. If any step rejects, the Approval Stage is set to "Rejected" and the Owner is emailed as well.

**Logic Locations:**
* [ZuoraQuoteClass.cls](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/classes/ZuoraQuoteClass.cls)
Code Unit:
    * stampManagerStack
* [ZuoraQuoteClass.cls](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/classes/ZuoraQuoteClass.cls)
Code Unit:
    * quoteApprovals
* [Salesforce Approval Process Setup](https://gitlab.lightning.force.com/lightning/setup/ApprovalProcesses/home)
Manage Approval Process For:
    * Quote (Installed Package: Zuora Quotes)


## Salesforce Chatter to Cases 

**Business Process this supports:** The field needs a streamlined process to address their concerns on specific salesforce records [within salesforce](/handbook/sales/field-operations/sales-operations/#how-to-communicate-with-us). This is also used by the finance team to help address record specific billing issues, as well as the Community Advocate team to manage the influx of requests the team receives. 

**Overview:** The goal of the Chatter To Cases functionality is to allow a streamlined communication channel that the field can leverage while also providing a streamlined case management system for the supporting team members to manage the requests that are sent to them from the field. If a team member uses an appropriate tag in salesforce a salesforce case record will automatically be created. Once these records are created supporting team members can work through the respective cases that are created to address the fields needs and concerns.

**Inputs:** Chatter text within Salesforce

**Outputs:** Salesforce Case Records 

**Logic Locations:** 
Code Units:
* Triggers
   * [ChatterFeedCommentTrigger.trigger](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/triggers/ChatterFeedCommentTrigger.trigger)
   * [ChatterFeedItemTrigger.trigger](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/triggers/ChatterFeedItemTrigger.trigger)
* Clases
   * [ChatterFeedCommentClass.cls](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/classes/ChatterFeedCommentClass.cls)
   * [ChatterFeedItemClass.cls](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/classes/ChatterFeedItemClass.cls)
* Tests
   * [ChatterFeedItemTest.cls](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/classes/ChatterFeedItemTest.cls)

**Supported Groups**
* `@sales-support`
   * This alias is leveraged by the Deal Desk team to manage inbound request from the Sales Team 
* `@billing ops`
   * This alias is leveraged by the Billing team to manage inbound request as they pertain to Billing
* `@revenue`
   * This alias is leveraged by the Revenue team to review Opportunities and how we will record revenue. [Detailed Response Here](https://gitlab.com/gitlab-com/sales-team/field-operations/systems/-/issues/859#note_386593491)
* `@SMB Flat Renewals`
  * This alias is used by our SMB team for flat renewal support. Please see this [section of the handbook](###) for how this is used. 

**Steps to add a Group:** 
* Do to limitations with Salesforce much of the minor updates must be implemented manually in production
* Create a Chatter Group with the alias that you want the end users to be able to chatter in Salesforce (In Production)
* Create a Queue that will own the Case until it is automatically switched into a users name who will work the case. (Changeset)
   * Review Queue member and email options with requester 
* Update the `ChatterFeedCommentClass` and the `ChatterFeedItemClass` to monitor for the use of the Chatter Group in chatters within Salesforce (Changeset)
* Update the `CaseClass` to include the new groups Id so that it updates the case owner what ownd by this queue. 
* Add a picklist value to the `Origin` field on the case object (In Production) 

**Related Epic**
* [@Sales-Ops Case Epic](https://gitlab.com/groups/gitlab-com/sales-team/field-operations/-/epics/7)


## Legal Request System

**Business Process this supports** The sales cycle, if a GitLab sales rep encounters an issue that requires legal knowledge, opinion, or action.

**Overview** A sales rep can quickly and easily create a Case for our legal team directly from an Opportunity's page layout in Salesforce. The legal team has access to a Salesforce dashboard to see how many Cases have been created for them, how many are in their name, etc. Clicking the "Legal Request" button on each Opportunity's page will bring the user to a page that asks a few questions that the legal team would like to know. Once the page is submitted, a Case is created with the Origin marked as "Legal Request." The legal team has dashboards that view Cases with Origin equal to "Legal Request" and can assign and take action from there.

**Logic Locations**
* Custom Buttons:
    * [In Setup, under Opportunity, "Buttons, Links, and Actions", Legal Request](https://gitlab.my.salesforce.com/00b4M000001ZNps)  
* Visualforce Pages:
    * [LegalCaseCreate.page](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/pages/LegalCaseCreate.page)  
* Apex Classes:
    * [LegalCaseCreateController.cls](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/classes/LegalCaseCreateController.cls)


## Primary Quote System

**Business Process this supports** The sales cycle and the financial processes around deals.

**Overview** We are now ensuring Opportunities in Salesforce have only one Quote that is marked as Primary. If multiple Quotes are being inserted under an Opportunity marked as primary in the same transaction, only the first in the list will be the primary. If a Quote is being inserted as primary, and there is an existing primary Quote, the existing will become not-primary and the incoming will be the new primary. If more than one Quote under the same Opportunity is being updated to become primary in the same transaction, an error message will prevent the update. A primary quote will not be allowed to be deleted. To change which Quote is primary, simply navigate to the Quote you want to be primary and update it as such, the previous primary Quote will automatically be updated to no longer be primary.

**Logic Locations**
* [ZuoraQuoteClass.cls](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/classes/ZuoraQuoteClass.cls)
Code Unit:
    * primaryCheck


## Opportunity Stage Progression Tracking

**Business Process this supports** The sales cycle and analytics.

**Overview** The goal of this functionality is to capture the progression of an opportunity through the stages in the sales process.  To support this, a check box and date stamp will be automatically populated for each stage as the oportunity advances and or moves back in stage.  The tracking begins at stage 0-Pending Acceptance.  In the event an opportunity advances forward and skips stages, all of the skiped stages will be stamped with the same date as the resting stage. In the event of Closed Lost and Unqualified, the checks and dates will only apply for the stages that were actually met.  To avoid data loss and confusion, the stage progression tracking will only run once, the first time through the stages. 

**Logic Locations**
* To be added once functionality is in Production

## Opportunity Validation Rule for Closed Accounting Period

**Business Process this supports**  The Sales Finance & Analytics

**Overview** The goal is have a static opportunity population in salesforce once the opportunity close date is past accounting close date ( which is 10th day of the month) so it ties to everything that was reported to the Board. And to ensure the bookings data don't change as there are other downstream implications such as Commissions Calculation, Booking Reporting & Adaptive Bookings Data,need to build a mechanism to lock the booking related opportunity fields after green light from Deal Desk & Finance. If there are any minor adjustments ( if needed ) to historical periods we have a specific permission sets to make the appropriate changes.

**Logic Locations**
* [ Validation Rule](https://gitlab.my.salesforce.com/03d4M000001113V?setupid=OpportunityValidations)

## Block Salesforce From Transferring Historical Opp Owners On Account Owner Transfers

**Business Process this supports:** In order to provide reliable and accurate historical data to the analytics team, the sales organization and to the companye as a whole we need to ensure that historical opportunities and relevant information on opportunities is not changed once the opportunity is closed. 

**Overview:** The goal of this blocking logic is to close a backdoor that Salesforce has built into the system. While we have a number of validation rules in place to prevent information from changing on closed opportunities it is possible to change historical opportunity owners (as well as fields that are derived from the owner field) while transferring accounts. Anyone who could have been able to change the owner on an account would have been able change historical opportuntiy data that they would not be able to edit otherwise. This logic still allows users to complete this account ownership transfer without any impact to historical opportunities while also allowing the various business teams at GitLab to manually update the owners of opportunities at month close.

**Inputs:** Account records that are changing ownership

**Outputs:** Reverts opportunity owners to their original owners if the user attempted to change them 

**Logic Locations:** 
Code Units:
    * ProtectClosedOppOwnersBefore
    * ProtectClosedOppOwnersAfter
* Triggers
   * [AccountTrigger.trigger](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/triggers/AccountTrigger.trigger)
* Clases
   * [AccountClass.cls](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/classes/AccountClass.cls)
* Tests
   * [AccountClassTest.cls](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/classes/AccountClassTest.cls)

## Order Type System

**Business Process this supports:** [New vs Connected New vs Growth](/handbook/sales/sales-term-glossary/)

**Overview:** The goal of the Order Type system is to determine a given Opportunity's relationship with the business. Did it start a new customer relationship, cross into a related segment of the customer, or grow an existing relationship.

**Design Presentation:** [https://docs.google.com/presentation/d/1G95aExDMTT1of6TkVWMPsx1FhNp3sNBl431t5PsKZmE/edit?usp=sharing](https://docs.google.com/presentation/d/1G95aExDMTT1of6TkVWMPsx1FhNp3sNBl431t5PsKZmE/edit?usp=sharing) 

**Logic Locations:** [AccountJob.cls](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/blob/master/force-app/main/default/classes/AccountJob.cls)

Code Units:
* determineOpportunityRevenueTypes

**Inputs:** Salesforce Account Hierarchy, Salesforce Opportunity Close Date and Stage.

**Outputs:** Populates the Order Type field on the Opportunity with New - First Order, New - Connected or Growth based on the following logic:

| **Order Type**     | **Description** |
|---------------|--------------------------------------------|
| New - First Order | The First Closed Won Opportunity in an Account Family. |
| New - Connected | The First Closed Won Opportunity on an individual Account, that is not the first one in the Account Family.|
| Growth | All opportunities that follow the `New - First Order` or `New - Connected` opportunities. This includes Add-ons, Renewals, and additional Subscriptions. |


## Lead Segmentation

**Business Process this supports:** [Sales Segmentation](/handbook/sales/field-operations/gtm-resources/#segmentation)

**Overview:** Leads should be sorted into different Sales Segments based on their company's employee count so the appropriate salesperson can pursue them. We have a number of different information sources to get company size, so we must also establish a hierarchy for them.

| **Info Source** | **Salesforce Lead Field API Name** |
| ---- | ---- |
| Lean Data | Lean_Data_Matched_Account_Sales_Segment__c |
| Web Portal | Web_Portal_Purchase_Company_Size__c |
| Marketing | Employee_Buckets__c |
| DemandBase | DB_Employee_Count__c |
| Zoominfo| 	ZI_Employees__c |
| Salesforce User | NumberOfEmployees |

**Logic Locations:** [LeadClass.cls](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/classes/LeadClass.cls)
Code Unit: 
   * determineSegment


## Force Management / Command of The Message / Command Plan

**Business Process this supports:** [Command of The Message](/handbook/sales/command-of-the-message/)

**Overview:** This Visualforce page and supporting controller provide the sales team with an easy to use button on their opportunities to populate the needed information. 

**Logic Locations:** 
* [ForceManagement.cls](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/classes/ForceManagement.cls)
* [ForceManagement.page](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/pages/ForceManagement.page)


## Linear Weighted Net ARR

**Business Process this supports:** [Linear Attribution](/handbook/marketing/marketing-operations/bizible/#linear-attribution)

**Overview:** Linear Weighted Net ARR is a measure at Gitlab that is used to measure the effectiveness of our marketing campaigns. Please refer to the excellent [Linear Attribution](/handbook/marketing/marketing-operations/bizible/#linear-attribution) section in our handbook for additional details. In summary the Linear Weighted Net ARR is calculated by taking the Net ARR of an Opportunity and dividing it by the Number of associated Bizibile Touchpoints related to the Opportunity. 

**Logic Locations:** [OpportunityJob.cls](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/classes/OpportunityJob.cls)
Code Unit: 
   * countBizibleTouchpointsCalculateLineariACV


## Mavenlink


**Business Process this supports:** This supports our professional services team. They leverage Mavenlink projects to coordinate their projects, the hours they spend on each project and their associated tasks, schedules and more. 

**Overview:** The following sections of code control the process by which Mavenlink project in Salesforce are created, which in turn are then pushed over to Mavenlink by leveraging an extension class that was provided by Mavenlink. Currently a Mavenlink Project is created when one of the following scenarios is met
   - A primary quote is created, that has a flagged Quote Rate Plan Charge on it (Mavenlink flag), where its associated opportunity is in stage 5 or later and their is not already an existing Mavenlink project for the related Opportunity
   - A Opportunity is moved into stage 5 or later, and it's primary quote has a flagged Quote Rate Plan Charge on it (Mavenlink flag) and their is not already an existing Mavenlink project for the related Opportunity
   - In the above two cases if there is an associated Mavenlink project the project is updated with the new updated information that has been changed 

**Logic Locations:** 
   * [OpportunityClass.CreateAndMaintainMavenLinkProject](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/classes/OpportunityClass.cls#L176)
   * [QuoteRatePlanChargeClass.CreateAndMaintainMavenLinkProject](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/classes/QuoteRatePlanChargeClass.cls#L3)
   * [MavenlinkProjectClass.upsertMavenLinkProject](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/classes/MavenlinkProjectClass.cls)
   * [GitlabMavenlinkExtension.cls](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/classes/GitlabMavenlinkExtension.cls)
   * [OpportunityClassTests.CreateAndMaintainMavenLinkProject](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/classes/OpportunityClassTests.cls#L227)
   * [QuoteRatePlanChargeClassTest.CreateAndMaintainMavenLinkProject](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/classes/QuoteRatePlanChargeClassTest.cls#L3)
   * [GitlabMavenlinkExtensionTest.cls](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/classes/GitlabMavenlinkExtensionTest.cls)


## Opportunity Splits


**Business Process this supports:** This supports the automatic creation validation of our opportunity split that supports our compensation team. This helps ensure that our team members are compensated for the opportunities that they are associated with in an automated fashion 

**Overview:** 
   -  **Split Creation and Automation**
   -  Below we'll see some key points as they pertain to Opportunity splits and below that we attempt to summarize the automation by end user story. 
   -  Split for any Opportunity can only be created by an individual on one of the teams Below. To clarify the current permission does not aim to say who should be creating opportunity splits but rather who can create them based on our current permission set assignments.  
         - Compensation Team
         - Deal Desk
         - Sales Ops
         - System Admins
   - `Account Executives` / Opportunity Owner
      - All of these splits should only ever appear in ``Opportunity - Incremental ACV 2`` split type
      - When the Opportunity Owner is updated, the splits for the Opportunity Owner are updated.
      - If a split is needed for the Owner the split needs to be created manually by an approved user 
   - `Sales Development Representatives` / `ISR` / `Primary Solutions Architect`
      - All of these splits should only ever appear in `Opportunity - iACV Overlay` split type
      - When the corresponding lookup field on the Opportunity is populated (created or updated) a split for 100% is created for the user in the lookup field and added to the opportunity
      - The population of the above lookup fields follow the same rules and processes as they have before the rollout of this automation
      - If a lookup field is changed from User A to User B then ALL splits for that User Role on the Opportunity are deleted and a split for 100% is assigned to User B
      - If a lookup field is changed from a User to Null/Empty then ALL splits for that User Role on the Opportunity are deleted, and there will be not splits for that Team Role on the Opportunity
      - If a split is needed for any of these roles the split needs to be created manually by an approved user 
   - `Technical Account Manager`
      - All of these splits should only ever appear in `Opportunity - iACV Overlay` split type
      - When the `Technical Account Manager` field on the Opportunity is populated a split for 100% 
         - The population of the `Technical Account Manager` is currently handled automatically, OpportunityClass.maintainTamTeamLookup, as they are only to be stamped onto Opportunities when the Opportunity is a Growth Opportunity
      - If a split is needed for a Technical Account Manager the split needs to be created manually by an approved user
   -  **Split Validation** 
   - When an Opportunity has its stage changed there is a validation run against the splits on the opportunity. The validation aims to ensure that all splits on the Opportunity when grouped by Role add up to 100%. If the splits do not add up to 100% an error is thrown and the splits must be updated prior to moving the opportunity forward
   - For the purposes of this validation the Team Roles of `Opportunity Owner`, `Account Executive`, `null/Empty` are assumed to be the same role and are summed accordingly. 


**Logic Locations:** 
   - [OpportunityClass.maintainTamTeamLookup](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/classes/OpportunityClass.cls#L315)
   - [OpportunityClass.maintainTeamMembersToSplits](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/classes/OpportunityClass.cls#L399)
   - [OpportunityClass.checkAndConfirmSplitPercentages](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/classes/OpportunityClass.cls#L337)
   - Please also see the [OpportunityClass.singleWonOppSplitOwnerUpdate](https://gitlab.com/gitlab-com/sales-team/field-operations/salesforce-src/-/blob/master/force-app/main/default/classes/OpportunityClass.cls#L126) where split are also handled but not directly in alignment with the needs for this process
