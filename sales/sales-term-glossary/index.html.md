---
layout: handbook-page-toc
title: "Sales Term Glossary"
description: "Definitions of key terms for the WW Field Team"
---

## On this page
{:.no_toc .hidden-md .hidden-lg}

- TOC
{:toc .hidden-md .hidden-lg}

The below page includes key definitions for the WW Field Team. 

## Customer Definitions for External Reporting

### Customer
We define the number of customers as the number of accounts with a unique account identifier for which we have an active subscription in the period indicated. Users of our free trials or tier are not included in our customer count. A single organization with multiple divisions, segments or subsidiaries is generally counted as a single customer.

We snapshot customer count on business day 4. 

- [Sisense Dashboard - Breakdown of Customers by ARR buckets](https://app.periscopedata.com/app/gitlab/474959/Customer-Count-by-ARR-Buckets)

### First Order Customers

A First Order customer is a customer within an Account Family that makes the first subscription order for the Account Family in the period.

### Connected New Customers

A connected new customer is the first new subscription order with an Account that is related to an existing customer Account Family (regardless of relative position in corporate hierarchy) and the iACV related to this new customer is considered "Connected New".

### Growth Customers

A Growth Customer is a customer within an Account Family when it is a subsequent subscription (not the first) or when a parent account consolidates new and existing subscriptions together. 

| **Situation** | **Marketing View** | **Sales & Finance View** |
| :------ | :------ | :------ |
| First Order | New | New |
| Connected New | New | Growth |
| Add-on Order | Growth  | Growth  |

First Order and Connected New can be reported on via the Order Type fields in Salesforce. We have iterated on this field so please use the following guide:

| SFDC Field Name       | Source of Truth for Time Period | Description                                                                                                    |
|-----------------------|---------------------------------|----------------------------------------------------------------------------------------------------------------|
| Order Type 1.0        | FY21                            | Value stamped at close.                                                                                        |
| (WIP) Order Type 2.0        | FY22 and Future Looking         | Value stamped at close. Includes enhanced logic to filter out Additional CI Minutes and Credits as First Order |
| (WIP) Order Type 2.0 (Live) | None                            | Used to track movement of values post deal close. Analysis Field Only.                                         |

Order Type (all iterations) runs on a nightly job, please allow 24 hours after a relevant change for the fields to update. [Technical documentation here](https://about.gitlab.com/handbook/sales/field-operations/sales-systems/gtm-technical-documentation/#order-type-system).

#### Order Type 2.0 Field Values

Order Type 2.0 introduced additional values that relate back to our [ARR defintion framework](https://about.gitlab.com/handbook/sales/sales-term-glossary/arr-in-practice/#arr-analysis-framework)

| Value                | Definition                                                                                       |
|----------------------|--------------------------------------------------------------------------------------------------|
| 1. New - First Order | Same as definition above                                                                         |
| 2. New - Connected   | Same as definition above                                                                         |
| 3. Growth            | Same as definition above                                                                         |
| 4. Contraction       | A renewal transaction that closes at a lower value then its prior value                          |
| 5. Churn - Partial   | The inverse of New - Connected. When an Account churns, but the family is still a customer.      |
| 6. Churn - Final     | The inverse of New - First Order. The final churn in an account family.                          |
| 7. PS / Other        | Non-recurring deals. Currently implemented as any deal value < $48 and is not coded as Pro Serv. |

### Additional customer definitions for internal reporting

We define customers in the following categorical level of detail:
1. Subscription: A unique subscription contract with GitLab for which the term has not ended.
As customers become more sophisticated users of GitLab the number of subscriptions may decline over time as Accounts and Parents consolidate subscriptions to gain more productivity.
1. Account: An organization that controls multiple subscriptions that have been purchased under a group with  common leadership.
In the case of the U.S. government, we count U.S. government departments and major agencies as a unique account.
1. Parent: An accumulation of Accounts under an organization with common ownership.
In the case of the U.S. government, we count U.S. government major agencies as a unique parent account. (In Salesforce this is the `Ultimate Parent Account` field)

Because "customer" can have three different meanings whenever customer is used in presenting data it must be qualified by the type of customer.

The default description is parent. When the default is used, no further description is required.

When account or subscription is being reported then the title or field description on the chart must be added to call out the basis for reporting.

Metrics that are based on customer data should also carry a clarifying description. For clarity parent will be the only customer type used for external reporting.

### Customer Segmentation

Customer segmentation follows the segmentation as laid out in the [Business Operations Handbook](/handbook/sales/field-operations/gtm-resources/#segmentation) at the [Parent Account level](#customers).

### Customer Counts

If an account was active at any point in time during the proposed timeframe it is counted as active.
For example, an account that is active from March 2019 to May 2019 but is inactive from June 2019-on is counted for CY2019, FY2020 (which runs from February 2019-January 2020), FY20-Q1, and FY20-Q2; it is not counted in FY20-Q3 or FY20-Q4.

## Revenue Definitions

### Deal Sizes

Deal Size is a dimension by which we will measure stage to stage conversions and stage cycle times of opportunities.
Values are [IACV](/handbook/finance/operating-metrics/#bookings-incremental-annual-contract-value-iacv) in USD.

1. Jumbo - USD 100,000 and up
1. Big - USD 25,000 to 99,999.99
1. Medium - USD 5,000 to 24,999.99
1. Small - below USD 5,000

Note that we use the same amounts to group customers by ARR.

### Annual Contract Value (ACV)

Value of **all** bookings from new and existing customers that will result in recurring revenue over the next 12 months less any credits, lost renewals, downgrades or any other decrease to annual recurring revenue.

Excluded from ACV are bookings that are non-recurring such as professional services, training and non-recurring engineering fees (PCV).

### Incremental Annual Contract Value (IACV)

Value of new bookings from new and existing customers that will result in recurring revenue over the next 12 months less any credits, lost renewals, downgrades or any other decrease to annual recurring revenue.

For a deep-dive into iACV, including how it is calculated, see the [iACV in Practice Page](/handbook/sales/sales-term-glossary/acv-in-practice)

### Annual Recurring Revenue (ARR)

GitLab defines ARR as the annual run-rate revenue of subscription agreements from all customers in a given month. GitLab calculates ARR by taking the monthly recurring revenue, or MRR, and multiplying it by 12. MRR for each month is calculated by aggregating, for all customers during that month, monthly revenue from committed contractual amounts of subscriptions. ARR and MRR should be viewed independently of revenue, and do not represent GitLab's GAAP revenue on a monthly or annualized basis, as they are operating metrics that can be impacted by contract start and end dates and renewal rates. ARR and MRR are not intended to be replacements or forecasts of revenue. ARR and MRR calculates subscription fees normalized to a monthly value, and does not include one-time or usage fees.

We snapshot ARR on business day 4. 

For a deep-dive into ARR, including how it is calculated and the analysis framework, see the [ARR in Practice Page](/handbook/sales/sales-term-glossary/arr-in-practice)

### Monthly Recurring Revenue (MRR)

Monthly recurring revenue from subscriptions that are active from all customers in a given month.

### Average Sales Price (ASP)

IACV per won deal. This metric can be reported against various dimensions (e.g. ASP by customer segment, cohort, sales channel, territory, etc.)

### ProServe Contract Value (PCV)

Contract value that is not considered a subscription and the work is performed by the Professional Services team.

### Total Contract Value (TCV)

Value of **all** bookings from new and existing customers that will result in revenue less any credits, lost renewals, downgrades or any other decrease (i.e. within 90 days from close of the deal).

If Deal Length is greater than 12 months:
Then TCV = ((ACV / 12) * Deal Term in Months) + Professional Services + Other One Time Fees

If Deal Length is less then or equal 12 months:
Then TCV = ACV + Professional Services + Other One Time Fees

### Credit

Lost or lowered contract value that occurs before a subscription renewal or subscription cancellation.

### Downgrade

Contract value that results in a lower value than the previous contract value.
Downgrade examples include seat reductions, product downgrades, discounts, and customers switching to Reseller at time of renewal.

### True Up

***What is it?***

A true up is a back payment for a customer going over their license count during the year.

***Why do we use it?***

We use the true up model so that the license never becomes a barrier to adoption for the client.

***Let's take an example.***

A customer takes out a subscription for 100 users.
During the year they grow the usage of the server and 200 additional users come on board.
When it comes time to renew, they are now up to 300 active users despite the license only being for 100 users.

At this point the customer needs to do two things: they need to renew the license and to add the true up users.
The number of true up users in this case is 200.
It is the difference between the `Maximum Users` and the `Users in License`.
This can be found by the customer in their GitLab server by going to the Admin > License area.
It will look like [this](https://docs.gitlab.com/ee/user/admin_area/img/license_details.png)

There is more information below on the steps you need to take, but in this example you would need to update the number of users for the renewal to 300 and add the `True Up` product to the renewal quote for 200 users.
This will create a one time only charge to the customer and in a year's time, they will have a renewal for 300 users.

[***See here more information on the steps to take for the true up***](/handbook/business-ops/enterprise-applications/portal/troubleshooting/)

***Note that we make provision for true ups in our standard [Subscription Terms](https://about.gitlab.com/terms/) Section 5 - Payment of Fees.***

### Total Addressable Market (TAMkt)

Annual revenue opportunity of the [entirety of GitLab’s market](/handbook/sales/tam).
The potential value of everyone worldwide that could purchase our product.
Both TAM and [LAM](landed-addressable-market-lam) can be scoped globally, by region/market segment, or customer-specific.

### Landed Addressable Market (LAM)

LAM is the annual revenue opportunity of the entirety of GitLab's market within our current customer base ("landed accounts").  The market is defined as total developers managed (employees and/or contractors for whom software is purchased and managed).  The definition uses "total developers" as the input.

*Basic LAM Formula:*

1. **LAM at a specific account** = Total Developers at the account x price/user/per year paid for currently contracted tier of GitLab
1. **LAM in a territory, segment, region, or other group of accounts** = Sum of LAM at the specific accounts in the group

*Calculation*

For territory and business planning, calculation will be automated using multiple data sources including customer verified totals.

The LAM formula has two inputs: Total Developers at the account and price.  

1. Price: Current ARPU based on the current subscription(s) in Zuora
1. Total Developers:
   1. Total developers at the account
   1. Data source: All validated fields below will be included in the calculation 
        1. Aberdeen Developers
        1. ZoomInfo Developers
        1. Potential Users (SAL Input)
        1. Potential Users Verify (SAL Input)

The formula calculation algorithm reviews the developer fields to ensure trustworthiness.  This is determined by comparing the developer fields to the number of employees and the number of licenses on the account.  If the developer data point is validated, the number of developers is reduced by the amount of paid licenses on an account to determine the number of potential developers. If the field fails the validation rules, it is eliminated. 

A fifth field based on license usage is added to the surviving data points from above.  

        5. Product Usage Overage (activated users - paid licenses) 

In order to calculate LAM, the MAX surviving data points is multiplied by the average seat price of the account. In the event the average seat price is below the average premium seat price, the result is multiplied by the average premium seat price instead of the actual account seat price.  

In circumstances where none of the developers fields are deemed trustworthy and there is no overage on the account, the formula defaults to the following: 

1. TSP Max Family Employees * Estimated Dev % (based on industry bucket)

*Rounding:* 

LAM for a specific account is always rounded to the nearest thousand dollars and capped at $5M per account.

### Developer Count 500 (D500)

D500 accounts are any prospect & customer accounts in SFDC that have more than 500 total developers.  This is useful when prioritizing high growth potential with high propensity to buy GitLab to ensure long-term growth within accounts. This field is populated by the number of developers used in the [LAM](https://about.gitlab.com/handbook/sales/sales-term-glossary/#landed-addressable-market-lam) calculation.  

### Customer Acquisition Cost (CAC)

Given our land and expand model, we need to attribute our sales and marketing expense toward both our acquiring new customers and growing new customers.
We allocate sales expense by using number of active customers because the number of active customers operationally drives where sales spends time. It also doesn't underweight sales time spent on first order which tends to be smaller than growth.
We divide our customer base into cohorts by the quarter when they had their first active subscription. We then weight sales expense to each cohort by the number of active customers in that cohort.
Our marketing expense is allocated between first order business and connected new business based on IACV because those are the key [KPIs](/handbook/ceo/kpis/) we use to evaluate marketing. Marketing expense includes the cost of free users of gitlab.com.

### Customer Acquisition Cost (CAC) Ratio

Defined as how much we spend in sales and marketing to generate revenue in a period. We calculate this by taking a ratio of the amount of sales and marketing spend (including the cost of free users of gitlab.com) in the prior period compared to the growth in revenue in the current period.  The formula is:

`(sales and marketing expense over trailing twelve months) / (recurring revenue current quarter * 4 - recurring revenue from same quarter prior year * 4)`

While the metric is easy to calculate, its limitation is that the sales and marketing efforts don't have as much impact on revenue in the current period as they do on bookings or future period revenue.

We've seen this definition of CAC Ratio used by companies in their investor presentation. [Industry guidance](http://www.forentrepreneurs.com/2017-saas-survey-part-1/) reports that median performance is 1.15, with anything less than 1.0  considered very good.

### Life-Time Value (LTV)

{: #ltv}
Customer Life-Time Value is the amount of gross margin contribution on a cash basis from a customer over the life of that customer.

### LTV to CAC

The customer Life-Time Value to Customer Acquisition Cost ratio ([LTV](/handbook/sales/#ltv):[CAC](/handbook/sales/#customer-acquisition-cost-cac) measures the relationship between the lifetime value of a customer and the cost of acquiring and growing that customer. [A good LTV to CAC ratio is considered to be > 3.0.](https://www.klipfolio.com/resources/kpi-examples/saas-metrics/customer-lifetime-value-to-customer-acquisition-ratio). 

To accurately calculate the LTV to CAC of a customer sum all the cash that a customer has paid GitLab over the life of the customer times the gross margin and divide it by the total sales and marketing cost to acquire and grow this customer. These cash flows are discounted back using the GitLab cost of capital or discount rate. We use 15% for our discount rate. This metric is the most accurate view of our unit economics however given we don't have many customers over 4 years of tenure with us there are assumptions in the numbers. This should be used for internal decision making only.

### Customer Acquisition Payback
As we acquire new customers we analyze how long it takes to recoup the investment to acquire a new customer. This is calculated by taking one cohort of customers and plotting the sum of the cash paid to GitLab by new customers over time and then plotting the amount of sales and marketing expense allocated to that cohort. Where the two lines cross is where GitLab breaks even on the customer acquisition.

### Available to Renew (ATR)

ATR is the sum of all ARR for subscriptions with a contract term ending in a given time period.  For clarity, this excludes all ARR for active subscriptions with contract terms ending in other time periods.  For example, if there were only 4 customers and Customer 1 (C1) and C2 have contracts ending in February 2022, C3 has a contract ending in Feb 2023, and C4 has a contract ending in June 2022, then the ATR for Q1 2022 would be the C1 ARR + C2 ARR.  It does not include C3 despite the fact that it is on a Q1 contract cycle since the contract does not expire until the following year.

### Lost Renewal

Contract value that is lost at the time of subscription renewals.
Lost Renewals examples include cancellations at or before the subscription renewal date.
If you have a customer who is not renewing, you must mark the Stage as `8-Closed Lost`.

### Growth Efficiency

(Recurring revenue T-1) - (Recurring revenue T-2)) * 4 / GTM spend T-2

T = current quarter

The thesis is that Go To Market (GTM) spend on marketing and sales in the second to last quarter caused the growth in the last quarter.

[Industry guidance](http://www.thesaascfo.com/calculate-saas-magic-number/) suggests a good Magic Number is > 1.0, this means you generate more than $1m in incremental ARR from $1m in Sales and marketing investment). Best in class is > 1.5 (for example Twilio). Atlassian is the best in the B2B SaaS industry > 2.0

This number is also sometimes called 'Magic number'.

### Revenue per Licensed User (also known as ARPU or ARPA)

ARR divided by number of [Licensed Users](#licensed-users).

This metric may also be referred to as Average Revenue Per User (ARPU) or Average Revenue Per Account (ARPA).

### Self-Serve Sales Ratio

Ratio of total IACV from closed won, Web Direct opportunities (i.e. customers who purchase via the self-service portal) divided by the total IACV of all closed won opportunities.
GitLab's target is greater than 30%. The default measurement is IACV but this can also be calculated and reported for ACV.

### Late Stage Pipeline

The IACV of all open opportunities currently in the stages of 4-Proposal, 5-Negotiating, and 6-Awaiting Signature.

### Total Pipeline

The IACV of all open opportunities.

### Pipeline Generation

We measure pipeline generated on a monthly basis for net new customers and existing customers.
For KPI measurement pipeline creation vs plan should exceed 1.0.

### Renewals + Existing Growth

Renewals ACV plus Growth IACV minus (Lost Renewals + Credits + Downgrades)

### Upsells/Cross sells and Extensions (IACV)

The value of the first twelve (12) months of any mid-term upgrade.

### Proto PTB (Propensity To Buy)

Is a classifier model built to identify customers most likely to increasing their ARR by >25% within the next 12 month. 

The model works at a parent account level and leverages data from previous periods like: ARR, ARR changes, created contacts, created opportunities, created support tickets, won/lost deals, touchpoints, products per period, # of seats and industry. 

The model was created following the iteration value and delivered a working Proof Of Concept for the FY22 planning exercise.  

[Link to repository](https://gitlab.com/gitlab-com/sales-team/field-operations/analytics/-/blob/041ec9eb0921dd117995b8f370dbd257cb52024b/Proto%20PTB/PTB%20-%20UPA%20-%20Wo%20Excl.%20-%20Per%20Segment%20-%20v4.ipynb).

## Rep Performance and Behavior Definitions

### Rep Productivity

The average amount of annualized IACV a native quota carrying sales rep produces in a given month
formula: (IACV / # of native quota carrying reps adjusted for ramp time) * 12 months. See [Quota Ramp](/handbook/sales/commissions/#sales-rep-iacv-quota-ramp)

The IACV used in this calculation only includes opportunities owned by quota carrying sales reps (not by a manager, director, or VP).
Additionally, opportunities that represent web portal purchases are split out separately.

#### Measuring Sales Rep Productivity

The primary metric when measuring rep productivity for only for quota attainment but also for compensation is the Gross Incremental Annual Contract Value (Gross IACV).
Is is important to remember that while renewals are not a part of comp or quota attainment, renewing customers is still very important aspect of our business.

Rep Productivity is defined as IACV divided by the number of reps of a particular type (i.e. SAL, MM AEs, SMB Customer Advocates).
Web portal purchases are split out separately.

Another measured KPI is Rep Productivity (as defined above) divided by On Target Income.

### Full Time Equivalent (FTE)

A ramp adjusted sales head count. 

## Systems Terminology Definitions 

### Parent and Child Accounts

* A Parent Account is the business/organization which owns another business/organization.
Example: The Walt Disney Company is the parent account of Disney-ABC Television Group and Disney.com.
* A Child Account is the organization you may have an opportunity with but is owned by the Parent Account.
A Child Account can be a [business unit](#business-unit), subsidiary, or a satellite office of the Parent Account.
* You may have a opportunity with the Parent account and a Child Account.
Example: Disney and ESPN may both be customers and have opportunities. However, the very first deal with a Parent Account, whether it is with the Parent Account or Child Account, should be marked as "New Business".
All other deals under the Parent Account will fall under Add-On Business, Existing Account - Cross-Sell, or Renewal Business (see Opportunity Types section).
* If the Parent and Child accounts have the same company name, either add the division, department, [business unit](#business-unit), or location to the end of the account name.
For example, Disney would be the name of the Parent Account, but the Child Account would be called The Walt Disney Company Latin America or The Walt Disney Company, Ltd Japan.
* When selling into a new division (which has their own budget, different mailing address, and decision process) create a new account.
This is the Child Account.
For every child account, you must select the parent account by using the parent account field on the account page.
If done properly, the Parent/Child relationship will be displayed in the Account Hierarchy section of the account page.
* Remember that a child account can also be a parent account for another account.
For example, Disney-ABC Television Group is the child for The Walt Disney Company, but is the parent for ABC Entertainment Group.
* We want to do this as we can keep each opportunity with each child account separate and easily find all accounts and opportunities tied to a parent account, as well as roll-up all Closed Won business against a Parent Account.

### Account Family
The collection of all Salesforce Accounts that roll up to the same Ultimate Parent Account.

### Business Unit

A distinct group or organization within a customer which, from a GitLab customer relationship perspective, can be treated and thought of as a separate customer. When determining whether a group is a business unit, factors to consider include whether they have:

- Their own contract with GitLab
- Their own GitLab instance
- Their own GitLab management team

### Licensed Users

The number of contracted users on active paid subscriptions. Excludes OSS, Education, Free and other non-paid users. The data source is Zuora.

### Closed Deal - Won

A unique deal that is set to `Closed Won` in SalesForce.

### Closed Deal - Won Reasons

The opportunity owner's primary reason as to why GitLab won the deal.

- **Accelerate Software Delivery:** Enable teams to deliver new code/code updates faster
- **Competitor Product Support/Performance:** Competitor missing a key feature the customer needed or the cutomer was not happy with competitors product performance
- **Expanding Use-Case:** Customer already using GitLab for one UseCase (CI for example) now they are expanding that to another (SCM for example)
- **GitLab Incumbency:** GitLab user already (most cases Free) and now they are moving to another Tier for more features
- **GitLab Champion:** Either someone tried GitLab for the first time and loved it or they used GitLab previously and they want their exisiting team/company to use GitLab
- **Performance/Great Features:** GitLab out performed the competition - customer felt we just had a better product than the competitor
- **Reduce Tooling Cost:** Customer paying for many multiple tools, wanted to reduce DevOps tooling cost with a single tool
- **Reduce Tooling Count:** Customer tool chain too complex, wanted to transition to a simple DevOps solution
- **Channel Deal:** A Channel Deal where we do not have a specified Clsoed Won Reason
- **Web Direct:** A Web Portal purchase where we do not have a specified Closed Won Reason
- **Other:** The deal was won due to reasons other than noted above

### Closed Deal - Lost

A unique deal that is set to `8-Closed Lost` in SalesForce.

### Closed Deal - Lost Reasons

The opportunity owner's primary reason as to why GitLab lost the deal

- **Budget/Value Unperceived:** Prospect's overall evaluation of product or service did not have the ability to meet their needs and expectations or there was a loss of budget
- **Competitive Loss:** Lost to a competitor
- **Competitor Incumbent:** Prospect is staying with existing competitor product
- **Do Nothing:** Prospect has chosen to take no action 
- **Duplicate:** Opportunity is a duplicate to another in SFDC
- **Legal Blocker:** Could not come to agreement on legal related items
- **Merged into another opportunity:** Associated licenses have been merged into another opportunity
- **No Relationship:** Evangelist /Champion Left or was not present
- **Operational Silos:** Departments or management groups do not share information, goals, tools, priorities and processes with other departments
- **Performance/Missing Features:** Prospect's overall evaluation of product or service meet some of their needs and expectations, but majorly lacked specific areas
- **Product Maturity:** For the customers specific need, the product is not mature enough in certain areas. This should include large feature sets or large areas of capabilities that the customer believes is missing or not fully developed as opposed to one missing feature. 
- **Went Silent:** Prospect has ceased communication 
- **Other:** The deal was lost due to reasons other than noted above


### Utilization

Utilization is defined as `Seats currently in use / Seats in license`.
When not qualified, referring to "utilization" always refers to license utilization.
All other uses, (e.g. CPU utilization), should be qualified and mentioned specifically.

### Sales Qualified Lead (SQL)

[Sales Qualified Lead](/handbook/sales/field-operations/gtm-resources/#customer-lifecycle)

### D300 (Account)

`D300` accounts are any prospect & customer accounts in SFDC that have more than 300 total developers.  This is useful when prioritizing high growth potential with high propensity to buy GitLab to ensure long-term growth within accounts.
