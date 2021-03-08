---
layout: handbook-page-toc
title: Use of Admin Notes
category: GitLab.com
subcategory: Accounts
description: "Workflow for when and how to add admin notes to a GitLab.com account"
---

## On this page
{:.no_toc .hidden-md .hidden-lg}

- TOC
{:toc .hidden-md .hidden-lg}

### Overview

The admin note serves as a quick reference for any account changes or action performed on a GitLab.com account. It also helps to determine if the user was previously flagged for any violations to prevent any further abuse.

If you encounter a situation with the following cases, an admin note is required.

- User requested change
- Legal case
- Security or Abuse case

### Adding the Note

To add the admin note, simply go to the user profile in the admin page of GitLab.com, click on edit the profile, then fill the  Admin Notes section.

In general, the formatting should be standard in a one liner format:

- Violation: `Date | Note | Case | Link`
- Action Taken: `Date | Note | Case | Link`

Slack conversations or Issue links may be used for the link if no ticket is lodged for the type of request.

#### Viewing the Notes

There are two methods a team member can use to look up admin notes for a particular user:

1. If the team member has admin privileges they can navigate to the user's profile where the admin note will be present
2. Team members can use ChatOps to read admin notes for a particular user via the following command in a Slack channel where the chatops bot has been invited
   > `/chatops run user find <username or email>`

#### Sample Notes

Disabling 2FA:
`2021-02-01 | 2FA removed | user requested | https://gitlab.zendesk.com/agent/tickets/123`

Email Address Change/Removal:
`2021-02-01 | Primary Email Change - No Access | User Requested | https://gitlab.zendesk.com/agent/tickets/123`

DMCA Request:
`2021-02-01 | DMCA Violation | Abuse | https://gitlab.zendesk.com/agent/tickets/123`

Abuse Case:
`2021-02-01 | Flagged for terms violation |  Abuse Case | https://gitlab.zendesk.com/agent/tickets/123`

User Blocked:
`2021-02-01 | User blocked by infra | see https://gitlab.com/gitlab-com/support/internal-requests/issues/441`
