---

title: Working with Issues
category: Handling tickets
description: The support team uses the processes and escalation points described on this page when creating, updating and escalating GitLab issues.

---



Creating, updating and escalating GitLab issues correctly is an important part of providing quick and accurate customer support. The support team uses the processes and escalation points described on this page when dealing with GitLab issues.

## Issue Prioritization

In general, the Product team  will [prioritize all issues](/handbook/product/product-processes/#how-we-prioritize-work) (not just customer requests) based on types of issues and the [direction of the product](/direction/).

The Support Team plays a role in communicating the **impact to customers** of issues and feature requests. By using appropriate templates, adding labels, and adding relevant information in descriptions and comments, the team can communicate which issues affect customers along with their priority and severity. By participating in the scheduling effort for each release, the Support Team represents an additional voice of the customer in product development.

### Additional Context and Notes

Having the Product team comment in the issues directly follows our core value of being transparent and will help customers understand the context around why / when their issues are being resolved, and it provides direct feedback from customers to the Development and Product teams.

Working this way, it is possible that a customer reported issue is not picked up for a while (scheduling first, then time to work on a fix, then schedule for release, etc.). However, the idea is that this is OK because most truly urgent issues will in fact be regressions that don’t have this scheduling problem. If a bug isn't a regression, that means it has existed for more than a month when the customer notes it, and thus we've gone at least a full month without someone reporting the issue as urgent.

Issues are not scheduled for a particular release unless Product adds them to a release milestone *and* they are assigned to a developer. We aim to be realistic about scheduled deliverables and will avoid scheduling issues that cannot be delivered in a given release.

## Adding Comments on Existing Issues

Regardless of the type of issue, please include any relevant information *along* with a link. Also check that the [correct labels](#adding-labels) have been applied.

Please see the product handbook to see [what information product wants us to provide for feature requests](/handbook/product/how-to-engage/#customer-feature-requests)

Optional:

[Search for Zendesk tickets based on the `GitLab Issues` custom field](https://handbook.gitlab.com/handbook/support/readiness/operations/docs/zendesk/searching/#searching-by-custom-ticket-field). Copy and add the link to the search query as a comment to the issue, specifying that it's an internal link to a ZenDesk search of related tickets. This will give the PM more insight into how many customers have encountered an open bug, or have requested a certain feature.

**Note:** To obtain the field ID for the `GitLab Issues` field, you can reference [this repository file](https://gitlab.com/gitlab-com/support/support-ops/zendesk-global/ticket-forms-and-fields/-/blob/master/ticket_fields/active/GitLab%20Issues.yaml).

## Adding Labels

Using the appropriate labels is *critical* to ensuring visibility of issues and to get them on relevant PM's radar.

Required:

- [Group](https://gitlab.com/gitlab-org/gitlab-ce/blob/master/doc/development/contributing/issue_workflow.md#group-labels): Unsure of which? Check out [documentation metadata](https://docs.gitlab.com/ee/development/documentation/#metadata), [label descriptions](https://gitlab.com/gitlab-org/gitlab/-/labels), [DevOps Stages](/handbook/product/categories/#devops-stages), [features list by stage](/features) or similar existing issue.
- [Type Labels](/handbook/engineering/metrics/#work-type-classification) should be added by the template, but *add* them if any are missing.
- `~customer` (if a ZenDesk link is added, the bot will add this automatically if you forget)
- `~regression ##.x` if applicable; for high-impact ones, add `~"Next Patch Release"` and ping the relevant lead and subject area experts

For `~customer`+ any label that allows severity (most commonly `~"type::bug"`) labeled issues, a Severity estimate is required. If it is missing, please add them to attract PM attention to the issue:

- [Severity](/handbook/engineering/quality/issue-triage/#severity): Follow the definitions to the best of your ability when assigning severity. If it's an `~severity::1`, mention the PM and consider posting in the appropriate Slack channel as well.  As Support often has a better idea of the impact on the customer(s), please explain the impact in a comment when you assign the Severity label. Feel free to have the customer add a comment as well, adding any other context they feel might be important.

Optional, but highly recommended:

- [Stage](https://gitlab.com/gitlab-org/gitlab-ce/blob/master/doc/development/contributing/issue_workflow.md#stage-labels)
- `~Reproduced on GitLab.com` if applicable

For L&R related issues, please see the [specific guidance on Fulfillment issues](../license-and-renewals/workflows/managing_product_issues.html).

## Escalate New and Existing Issues

The Support team can directly ping the PM on the issue or in the #product Slack channel (see [DevOps Stages](/handbook/product/categories/#devops-stages)) in case this may help with communication. Comments might include asking for an update on behalf of the customer, or discussing the severity or priority especially if it needs to be increased.

## Creating Issues

Whenever possible, reproduce the issue and file a *public* issue with a reference to the ZD link as an additional example.

When reporting a problem, use the `Bug` template, then fill out as much of the information as possible. Ensure you [add labels](#adding-labels).

When writing issues, consider adding questions as a comment after creating the issue. For example: "@PM please provide feedback on this issue. Are we interested in fixing/implementing this? How critical do you think it is?"

## Avoid Re-opening Closed Issues

If you find an existing closed issue that is the same or similar to the customer problem at hand, you probably should not re-open the closed issue. The closed issue may actually be unrelated. Or maybe the closed issue describes the same problem you see now, but has a different root cause. Even if it's the same identical problem, you probably should not re-open the issue because that issue might have a previous milestone and so now the re-opened issue would have an invalid milestone in the past.

Instead, consider creating a new issue, and mention/link the existing closed issue to it. Let the Product and Engineering teams triage the new issue further and don't worry about creating duplicates.

### Maintain confidentiality

If an image, log output, etc. is required for the issue, try to produce your own test image. If you are unable to reproduce the issue and you wish to use the image/information provided by the customer make sure you *obtain permission* from the customer since the image/information may (inadvertently) include sensitive information like names, group names, user names, or code.

Public issues are always preferred, but if customer logs or other information needs to be included and the customer is willing to share it internally, but not publicly then make the issue *confidential*.

### Information gathering

For the *Application and environment information* section of issue templates, use:

- Omnibus: `sudo gitlab-rake gitlab:check`
- Source: `sudo -u git -H bundle exec rake gitlab:check RAILS_ENV=production SANITIZE=true`

and

- Omnibus: `sudo gitlab-rake gitlab:env:info`
- Source: `sudo -u git -H bundle exec rake gitlab:env:info RAILS_ENV=production`

## Creating Feature Proposals

As per our [Statement of Support](https://about.gitlab.com/support/statement-of-support/), the Support Team will generally ask the customer to create feature requests. Feature requests with direct feedback from customers are valuable as customers are often best equipped to explain their use case, requirements, and needs. Ask customers to create the feature request issue and share the link with us. Once an issue link is available, [add labels](#adding-labels) and relevant details in the [comments](#adding-comments-on-existing-issues), and [link the source](/handbook/product/how-to-engage/#customer-feature-requests).

If you create a feature proposal on behalf of a customer, please follow the same process as [Creating Issues](#creating-issues) by using the `Feature Proposal` template. After the issue is created, share the link in a reply encouraging the customer to follow and contribute to the issue.

**Note:** GitLab has limited development resources. Additionally, we must think about how widely applicable a feature may be to other users. Requests that are very specific to one company's workflow are likely to be rejected. Even if a feature seems widely applicable, we may leave the feature proposal dormant for some time and see if other users and customers chime in that they are also interested. Features that garner interest from multiple organizations will be considered more rapidly. Of course, there are always exceptions to these 'rules'. This note is meant to set the expectation that feature proposals may not be implemented quickly.

## Functional escalation points

| Service/Product  | Escalation Types                 | Escalation Point                                        | Assignment      |
|------------------|--------------------------------|-----------------------------------------------------------|------------------
| GitLab           | Bug reports or Feature proposals | [Bug](https://gitlab.com/gitlab-org/gitlab/-/issues/new?issuable_template=Bug) or [Feature proposal](https://gitlab.com/gitlab-org/gitlab/-/issues/new?issuable_template=Feature%20proposal%20-%20detailed)           |
| Omnibus GitLab   | Bug reports, Feature proposals | <https://gitlab.com/gitlab-org/omnibus-gitlab/issues/new>   | Omnibus GitLab specialist
| GitLab Runner    | Bug reports, Feature proposals | <https://gitlab.com/gitlab-org/gitlab-runner/issues/new>  | GitLab CI specialist
| GitLab Workhorse | Bug reports, Feature proposals | <https://gitlab.com/gitlab-org/gitlab/-/issues/new?issue%5bdescription%5d=%2flabel%20%7eworkhorse> | Maintainer of gitlab-workhorse

**See the [GitLab team page](/company/team/) for assignments**

## Operational escalation points

| Service/Product       | Escalation Type                                                                                  | Escalation Point                                         |  Assignment      |
|-----------------------|-------------------------------------------------------------------------------------------------|---------------------------------------------------------|----------------------- |
| GitLab Infrastructure | Anything related to the **running of GitLab.com**, performance, something breaks                | <https://gitlab.com/gitlab-com/infrastructure/issues/new> | Production Lead/Senior Production Engineer
| GitLab.com Support Engineers| Anything related to the **use of GitLab.com**, operations that can't be performed with admin access  | <https://gitlab.com/gitlab-com/support/internal-requests/issues/new> | Use `~"GitLab.com Console Escalation"` label |
| GitLab Support        | Any and all questions in relation to providing customer service for GitLab users and customers. | <https://gitlab.com/gitlab-com/support/support-team-meta/issues/new>        | Support Team Lead/Senior Support Engineer

**See the [GitLab team page](/company/team/) for assignments**

### Omnibus GitLab

- Related to Omnibus GitLab packaging only.
- GitLab [omnibus release packages](https://packages.gitlab.com/gitlab)

### GitLab Runner

- Information on [GitLab Runner](https://gitlab.com/gitlab-org/gitlab-runner#features)
- [Runner documentation](https://docs.gitlab.com/ee/ci/runners/)

### GitLab Workhorse

- Information on [GitLab Workhorse](/blog/2016/04/12/a-brief-history-of-gitlab-workhorse/)
- **Description**  *"GitLab-workhorse is a smart reverse proxy for GitLab. It handles "large" HTTP requests such as file downloads, file uploads, Git push/pull and Git archive downloads."*

### GitLab Infrastructure

- Reach the infra team on [Slack](https://gitlab.slack.com/archives/infrastructure)
- Old blog post on [infrastructure](/blog/2016/04/29/look-into-gitlab-infrastructure/)

## General Product Feedback

In the case where general product feedback is received and it is not clear whether it is related to or belongs in an issue, feel free to convey the feedback to the product team as outlined in our [Product Feedback section](/handbook/support/workflows/feedbacks_and_complaints.html#product-feedback).