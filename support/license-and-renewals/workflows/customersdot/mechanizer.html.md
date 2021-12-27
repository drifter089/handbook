---
layout: handbook-page-toc
title: Mechanizer 
category: CustomersDot
description: How to use the mechanizer for L&R requests. 
---

## On this page
{:.no_toc .hidden-md .hidden-lg}

- TOC
{:toc .hidden-md .hidden-lg}

## Overview

This workflow details how to use the various automated forms that utilize the [Mechanizer](https://gitlab.com/gitlab-com/support/toolbox/mechanizer) for GitLab.com account related tasks.  The forms may be found in [hosted on Gitlab Pages here](https://gitlab-com.gitlab.io/support/toolbox/forms_processor/LR/) and team members should have access.

## Existing Automations

### Add CI Minutes

The [Add CI Minutes form](https://gitlab-com.gitlab.io/support/toolbox/forms_processor/LR/extra_minutes.html) allows adding minutes to a customer namespace. The form has two required fields:

- **Namespace**: The customer namespace as it appears in the URL.
- **Extra minutes**: The number of minutes to add

### Force Associate

The [Force Associate form](https://gitlab-com.gitlab.io/support/toolbox/forms_processor/LR/force_associate.html) assoicates a group with a subscription. All fields are required.

- **Your GitLab Username**: Your non-admin GitLab.com username without a preceding @ (ex. `username` and not `@username`).
- **Namespace**: The customer namespace as it appears in the URL.
- **Subscription ID**: The unique ID of the purchased subscription in Salesforce

### Update GitLab Subscription or Customer Trial

The [Update Plan](https://gitlab-com.gitlab.io/support/toolbox/forms_processor/LR/update_gitlab_plan.html) form is meant for the following cases:

1. Downgrade to Free
1. Trials
    1. Change Plan
    1. Renew/extend Date
1. "Extend" an existing active or expired subscription.
    - Note: To "extend" a subscription, a trial is triggered on the namespace. An old trial order is used if it exists. Otherwise, a new trial is created.

Please note that in order to extend or renew a trial, the customer **MUST** have an active trial because a CustomersDot account needs to exist.  If the prospect has not yet initiated a trial themselves, please have them do so via the [customers portal](https://customers.gitlab.com/trials/new?gl_com=true).

These three fields are mandatory:

- **Your GitLab Username**: Your non-admin GitLab.com username without a preceding @ (meaning `username` and not `@username`).
- **Namespace**: The customer's namespace as it appears in the URL.  For example, if the customer namespace is located at http://gitlab.com/gitlab-com then the namespace would be `gitlab-com`. Please confirm through your own observation and through communication with Sales, the TAM, or the customer that the namespace is the one with the subscription or trial to be updated.
- **Plan**: The subscription plan that you would like applied for the customer's group.  If the `free` option is selected, the customer's namespace will immediately be downgraded and the trial or subscription ended.

These two fields are optional:

- **End Date**: The updated date the plan will end.
- **Sales Manager Approval**: The GitLab.com username (without a preceding @) of the sales manager who approved a trial extension of more than 30 days.

Required to "extend" a subscription:

- **Subscription name**: The name of the existing (active or expired) subscription tied to the namespace.

### Clear Subscription
The [Clear Subscription](https://gitlab-com.gitlab.io/support/toolbox/forms_processor/LR/clear_subscription.html) form unlinks a grop from a subscription.

- **Your GitLab Username**: Your non-admin GitLab.com username without a preceding @ (ex. `username` and not `@username`).
- **Extra minutes**: The number of minutes to add
