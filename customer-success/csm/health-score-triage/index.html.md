---
layout: handbook-page-toc
description: "This page covers the factors to consider for customer health, guidelines for selecting the appropriate rating, communication guidelines, CSM responsibilities and instructions for the account triage issue creation."
title: "Customer Health Assessment and Management"
---

## On this page
{:.no_toc .hidden-md .hidden-lg}

- TOC
{:toc .hidden-md .hidden-lg}

{::options parse_block_html="true" /}

View the [CSM Handbook homepage](/handbook/customer-success/csm/) for additional CSM-related handbook pages.

----
This page covers the factors to consider for customer health, guidelines for selecting the appropriate rating, communication guidelines, CSM responsibilities and instructions for the account triage issue creation.

See [Customer Health Scoring](/handbook/customer-success/customer-health-scoring) for an overview on how customer health scoring is defined and calculated at GitLab.

## CSM Responsibilities

The CSM is responsible for coordinating with all relevant parties to develop a plan to address account risks. Typically, this will involve the account team and communication group ([Communication Guidelines](/handbook/customer-success/csm/health-score-triage/#communication-guidelines)), as well as other relevant stakeholders such as Product Managers, marketing, executive, or engineering team members to develop and deliver the plan to address the risks. The CSM then drives execution of the strategy and is responsible for logging regular updates. When the risks have been addressed bringing the customer to a healthy / green status, the account team can agree to move the account out of triage.

## Tracking Customer Health

CSMs can use Red, Yellow, and Green to reflect their sentiment of a customer's health. Below is an explanation about how to think about a customer's health.

### Green

Customer is very likely to renew and/or expand with no known or assumed risk of downsell or churn. Customer's experience: engagement, adoption and experiences are as expected or better than expected, delivering value and outcomes as appropriate the customer's stage in their journey. Examples:

- Progressive adoption of GitLab use cases as defined by their success plan, considering their stage in their journey
- Alignment with stakeholders who can drive desired outcomes
- Regular communication and engagement in meetings
- Positive feedback on the product and experience and/or high scores on NPS surveys
- Leveraging support services as defined by creation of tickets (1-5 tickets per month)
- Interest in providing feedback and engaging with GitLab through other programs and events (e.g., Commit, CAB)

### Yellow & Yellow "Needs Triage"

Potential risk or significant lack of information leading to uncertainty. Indicates challenges to overcome, with a lower risk of churn or downsell. Customer's experience: engagement, adoption and/or experiences are lower than expected, risking GitLab's ability to deliver customer value and outcomes and/or drive future revenue growth. Examples:

- Slow, delayed, or blocked adoption of GitLab use cases in support of the customer's success plan
- Customer lacks definition of goals or success criteria
- High number of support cases, critical / blocker product issue(s), or poor experience based on the customer's expectations
- Lack of engagement, responsiveness or participation in meetings and/or events
- Loss of sponsor or champion due to change of role or organization or acquisition
- Lack of adoption of releases (self-managed only) where they are more than a major release behind the current release
- Not leveraging technical support services or has a large number of cases and/or high severity cases (6-15 tickets per month, or no ticket(s) opened after being advised by the CSM that Support is the best path to resolution for an issue(s))
- Poor experiences with Support, Professional Services or another part of GitLab
- Working with a single contact at a company (single-threaded).

There might be well understood reasons within the account team why a customer is flagged as Yellow within the current phase of the customer lifecycle. If the CSM decides that corrective actions and follow up from team members outside of the CSM group is required the CSM must create an [At Risk Timeline Entry](/handbook/customer-success/csm/health-score-triage/#at-risk-timeline-entries) and flag the account as Yellow "Requires Triage".

### Red

Specific, known risks to account retention or upcoming opportunity, or overwhelming lack of information, such as unresponsiveness leading up to renewal. Customer's experience: engagement, adoption and/or experiences are significantly lower than expected where issues are blocking GitLab's ability to deliver expected value, outcomes, or positive experiences as defined by the customer.
Examples:

- Potential risk of contraction or churn (even if this is unconfirmed)
- Lack of alignment with stakeholders who can drive outcomes... 
   - [Economic Buyer](https://about.gitlab.com/handbook/sales/meddppicc/#economic-buyer) 
   - [Champion](https://about.gitlab.com/handbook/sales/meddppicc/#champion)
   - Key [Personas](https://about.gitlab.com/handbook/product/personas/) 
      - [Cameron (Compliance Manager)](https://about.gitlab.com/handbook/product/personas/#cameron-compliance-manager)
      - [Delaney (Development Team Lead)](https://about.gitlab.com/handbook/product/personas/#delaney-development-team-lead)
- Product does not deliver expected value or outcomes as defined by success plan
- No or low product adoption with no progression
- Communication of poor sentiment
- Lack of any engagement
- Significantly poor experiences with Support or Professional Services
- Significant number of support tickets (16+ per month)

### Will Churn

Very rarely, a customer reaches a point at which it is accepted by the account team and leadership that a customer will contract or churn. As Gainsight does not support a 'grey' color (or any color outside of the standard green to red health scoring), the `will churn` lifecycle stage can be applied in 360º Attributes.

In order for a customer to move to the `will churn` stage, the following must be completed:

1. All options discussed during the at-risk reviews have been exhausted
1. CSM discusses it with their manager and gets agreement on moving to `will churn`
1. RM/AE marks the opportunity as `Will Churn` or `Will Contract`
1. CSM updates the Lifecycle Stage in Gainsight C360 > Attributes > Lifecycle Stage to `Will Churn`

## Reporting and Viewing Customer Health

Use the `Customer Health` (CSM Portfolio Dashboard) report to view the health of every measure for your customers in one single view.

To view Timeline entires where the CSM Sentiment was updated:

1. Go to Global Timeline
1. Filter by Sentiment = Green, Yellow, or Red
1. Apply any other specific filters (CSM Name, Timeline date, etc)

## Gainsight Responsibilities

CSMs are responsible for keeping Gainsight up to date regarding all of their account risks.

### At Risk Timeline Entries

For any account that is Red or Yellow, the following steps for an At Risk timeline update is required: 

1. In the account timeline, log an `At-Risk Update`, marking CSM Sentiment as Red (or Yellow) and any context for the at-risk account
1. Gainsight will auto create the `At-Risk` CTA (in Cockpit) within 24h
1. CSM updates CTA [Risk Impact](/handbook/customer-success/csm/health-score-triage/#risk-impact-definitions) and [Risk Reason](/handbook/customer-success/csm/health-score-triage/#risk-reason-definitions) dropdown fields
   1. In the CTA, update `Stage Name` and `Competitor` fields if applicable
1. CSM logs new `At-Risk Update` based on [Frequency of At Risk Timeline Entries](/handbook/customer-success/csm/health-score-triage/#frequency-of-at-risk-timeline-entries). At-Risk Update entries should follow the template to include the following information:
   1. General background or updates on the At-Risk customer (i.e., key discussion points on the most recent cadence call)
   2. Next Steps and/or pending action items
   3. Date of the next scheduled call
1. At-Risk Conclusion:
   1. Customer is won back:
      1. Log Account-level Timeline `At-Risk Update` type for CSM Sentiment as Green and final notes
      1. Change customer Lifecycle Stage to Adopting
      1. Close out CTA with success criteria (Closed-Won, win reasons)
   1. Customer is lost:
      1. Log Account-level Timeline `At-Risk Update` type with final update
      1. Change customer Lifecycle Stage to: Will Churn for a churning customer and Adopting for downgrade customer
      1. Close out CTA with success criteria (Closed-Lost, loss reasons)

**Tips**:

- **Keep the CTA open until fully resolved**. Resolved can mean the customer is won back, contraction has happened, or they will churn
- Use `closed-won` when we saved the customer AND had a flat or positive net ARR opportunity
- Use `closed-lost` when we churned the customer or had contraction

This can then be discussed with the [Account Team](/handbook/customer-success/account-team/) during account reviews.

### Frequency of At Risk Timeline Entries

1. If customer renewal is this fiscal quarter or next: 
   1. Weekly [At-Risk Timeline](/handbook/customer-success/csm/health-score-triage/#at-risk-timeline-entries) updates
      - Entry should include progress towards risk mitigation over the past week and plans for the upcoming week.
1. If customer renewal is after next fiscal quarter: 
   1. Monthly [At-Risk Timeline](/handbook/customer-success/csm/health-score-triage/#at-risk-timeline-entries) updates
      - Entry should include progress towards risk mitigation over the past month and plans for the upcoming month.

![GitLab At-Risk Customer Process](/CSM_At-Risk_Customer_Process.png)

### When to open an Account Escalation

If a CSM has marked an account as [Red](/handbook/customer-success/csm/health-score-triage/#red) and further assistance from Product, Support or Managers+ is needed, open an [Account Escalation](/handbook/customer-success/csm/escalations/).

### Risk impact definitions

1. **Customer Churn** - fully churn the account
1. **Tier Downgrade** - move down tiers
1. **Seat Churn** - reduce license seat count
1. **Customer Sentiment** (Impact Unknown) - customer is unhappy and the impact isn’t quantified
1. **Competitor** - any competitive intelligence we might be up against
1. **Stage Name** - stage impact, for example, product deficiencies, direction, or needs.

### Risk reason definitions

#### Lack of adoption

Customer never adopted the product or specific features so they did not get value. This can be because of organizational silos or lack of internal resources. If they didn't adopt because they didn't see / experience value, it should be Product Gap

#### Product Value / Gaps

Prospect or customer used the product and features (i.e., trial, POV, or purchased product), but did not see the value. The product did not meet requirements of the customer. This can also be a prospect where they did not experience perceived value

#### Product Quality / Availability

Prospect or customer used the product and features (i.e., trial, POV, or purchased product) though they did not meet the prospect or customer's needs or expectations. This can be defects, poor performance, or uptime/availability issues. Includes both self-managed and SaaS products

#### Lack of Engagement / Sponsor

We lost or were never able to get engagement with the prospect or customer team. The champion / sponsor left, changed responsibility, or became unresponsive. We were never able to re-establish connection with a new sponsor or champion

#### Loss of Budget

The prospect or customer lost budget due to business contraction, change of priorities, reduction of employees, or other. This was not a competitive loss.

#### Corporate Decision

Due to management decision or policy, the prospect or customer chose a different product but not because of product gaps, adoption, etc. This would be a top-down decision (e.g., ELA, decision to commit to a single provider)
* **Other** - other company issues that contribute to a blocker for the renewal

### Mitigation Strategies

For CSM guidance on mitigating risk, please see the [Risk Types, Discovery & Mitigation Strategies](/handbook/customer-success/csm/risk-mitigation) page.


## At Risk Communication Guidelines

The following are guidelines on who to notify when an account is yellow or red. Please make sure the following people are notified with the respective customer health ratings.

### Yellow Health Rating

- Account Team (i.e. Account Executive and Solution Architect)
- Regional CSM Manager
- CSM Director (all non-Public Sector customers) or Director of Customer Success Public Sector (for Public Sector customers)

### Red Health Rating

- Include the list above as well as…
- Area Sales Manager and Regional Director
- Vice President of Customer Success



## Related Processes

[Customer Success Escalations Process](/handbook/customer-success/csm/escalations/)

