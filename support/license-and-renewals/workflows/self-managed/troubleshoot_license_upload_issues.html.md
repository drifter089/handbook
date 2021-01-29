---
layout: markdown_page
title: Troubleshooting license upload errors
description: "How to troubleshoot GitLab license uploading errors"
category: GitLab Self-Managed licenses
---

{:.no_toc}

----

Customers may report encountering the following error message when uploading a license to their GitLab Self-Managed instance:

> During the year before this license started, this GitLab installation had 286
> active users, exceeding this license's limit of 250 by 36 users. Please
> upload a license for at least 286 users or contact sales at [redacted]@gitlab.com.

This error is shown if **any** of the following 3 values are incorrect:

| Key Field | Definition & source of truth |
|------|-------|
| Users count |   We identify the minimum amount via the active.users command: `sudo gitlab-rails runner 'p User.active.count'`  |
| Previous users count |   We can try to assume based on licenses in our LicenseDot but this cannot be certain since multiple licenses may be generated for one period. Instead, the best identifier is the system itself. For this we request a screenshot of the user statistics panel from `Admin Area -> Overview -> Dashboard`. The Previous users count = `Users in License` in the widget on the top left. |
| True-up count |   The best identifier for this value is to take Max Users - Previous users count. We recommend using the historical.max command: `sudo gitlab-rails runner 'p ::HistoricalData.max_historical_user_count'` for the Max count. |

**Note:** For Ultimate licenses, guest users are not counted in the licensed user count. Therefore, the `User.active.count` will be a greater number than the `Active Users` count displayed in the Admin UI dashboard. This can be confusing in a situation where the customer is downgrading from Ultimate or if they have an Ultimate trial, because they need a license for `User.active.count` instead of what is displayed for `Active Users`.

You can use the Zendesk `Subscriptions::Active Users` macro to ask the customer for this information.

## Examples

**EXAMPLE 1**
   - Subscription for 10 users
   - During the subscription term incurs a max of 15 users
   - Before renewal, blocks 3 users
   - At renewal, the license must be generated as: `Users count: 12` (or more), `Previous users count: 10`, `Trueup count: 5 `

**EXAMPLE 2**
  - Subscription for 20 users starts in December with only 12 active users in the system
  - In March, 5 users are blocked leaving 7 active users (12 max users)
  - In April, 5 new users are added making the active user count 12 (12 max users)
  - In July, 10 more new users are added making the active user count 22 (22 max users)
  - In August, 5 users are blocked making the active user count 17 (22 max users)
  - At renewal, the license must be generated as: `Users count: 17` (or more), `Previous users count: 20`, `Trueup count: 2`

**EXAMPLE 3**
  - Ultimate subscription for 10 users
  - During the subscription term, has 12 active users, including 2 guest users
  - At renewal, customer downgrades to Premium license
  - License must be generated as: `Users count: 12` (or more), `Previous users count: 10`, `Trueup count: 0`
