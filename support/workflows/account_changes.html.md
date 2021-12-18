---
layout: handbook-page-toc
title: Making Changes and Taking Actions on an Account
category: GitLab.com
subcategory: Accounts
description: "Workflow for when and how to make account changes on behalf of a customer"
---

## On this page
{:.no_toc .hidden-md .hidden-lg}

- TOC
{:toc .hidden-md .hidden-lg}

## Overview

This workflow focuses on the process when action is required by the Support team on behalf of the user.

The main situations where action may need to be taken on behalf of the user:

1. Project/Group Changes
1. Account Access Requests
1. Releasing an Email Address

### User Action First

Following our [Security Policy on "GitLab's Access to Your Private Repositories"](/security/faq), actions should always be taken by the user whenever possible.

For example, users should be deleting their own projects, but if they encounter an error with every attempt and there are no workarounds, then Support can intervene [with permission](#asking-permission).

If in doubt, please ask a Support manager to review.

## Project/Group Changes

In cases where Support needs to take action on the project or group, such as for troubleshooting purposes, Support should do two things:

1. Verify the user is a group _Owner_ or project _Maintainer_. Otherwise, ask the user to have an owner/maintainer contact us.
1. Ask for permission to take action. See the [Asking Permission](#asking-permission) section below.
1. Consider adding an [Admin Note](/handbook/support/workflows/admin_note.html) to the group admin page if Support may need to know the action was taken in the future.

You can continue working with the original requester once an owner/maintainer provides permission if that is their preference.

## Account Access Requests

In cases where a user has lost access to their account, all other options (such as SSH recovery codes, password reset) should be exhausted first.

For unconfirmed accounts, the only account action support will typically take is an [email typo fix](confirmation_emails.html.md#typo-fix).

Before taking any action on confirmed accounts, ensure that you have verified the account owner using the [Account Ownership Verification](/handbook/support/workflows/account_verification.html) workflow.

If ownership is verified, then:

1. [Confirm permission for the changes](#asking-permission).
1. Add an [Admin Note](/handbook/support/workflows/admin_note.html) to the user's account.

Example cases include:

1. Swapping secondary email with primary email due to primary email being unconfirmed, non-existent, or similar.
1. Removing an identity tied to the user account. The identity should also be verified in these cases.

## Releasing an Email Address

Similar to **Account Access Requests**, if a user has lost access to their account and the account shows **no activity** in its history, then we can consider releasing the email address for the user to create a new account with.

For unverified/unconfirmed accounts, please see the [confirmation emails](confirmation_emails.html) workflow.

Only use this process if the account shows **no** activity. If an account shows any activity tied to any type of contribution (such as snippets, or comments in a project or group), use the [Account Ownership Verification](account_verification.html) workflow instead.

To release an email address for an inactive account:

1. User should be able to verify the username and email address tied to the account.
1. Check the activity level of the account. Verify that the account shows **no activity** and is not a member of any projects or groups.
1. [Confirm permission for the changes](#asking-permission).
1. Update the email address with `+release`. For example, if the email address is `johndoe@example.com`, then update the email address on the account to `johndoe+release@example.com`.
    - This can be done with Admin access or [via Chatops](./chatops.html#Update-a-Users-Primary-Email)
1. Add an [Admin Note](admin_note.html) to the user's account.

## How is permission given for troubleshooting?

The Support team will not view any private information unless required to resolve an issue. Typically, the issue is filed by the account holder (for users) or valid members of the namespace (for projects and groups) via a support ticket for troubleshooting purposes as outlined in [Security Policy on "GitLab's Access to Your Private Repositories"](/security/faq).

A Support team member may look at information on pages not explicitly mentioned in the request, but will limit the scope of the review to the minimum access required to solve any issues.

The Support team will only take action from the requester if they:
- Are a member of the namespace.
- Have a problem that requires Support to investigate.
- Provide a link to the namespace.
  - This link can come from the initial form submission or a response in the ticket.

We expect users to provide specific links in order to focus on the related views and logs while investigating an issue. For example, a request to look into a CI/CD error should include links to the relevant job logs, pipelines, and/or CI YAML file.

Any time user data needs to be downloaded (such as cloning a repository), or where secrets must be revealed (such as [CI/CD Variables](https://docs.gitlab.com/ee/ci/variables/)), to further troubleshoot, requires [explicit permission](#asking-permission) before continuing. Any user data that has been downloaded for reproduction purposes must be deleted when the issue is resolved.

## Asking Permission

Before any actions are taken, please request explicit permission to take the required action. Be as specific as possible so that there is no confusion.

Once permission is confirmed by the user, then you may proceed.

Some sample phrases:

> Could you please provide permission for Support to ... ?

or

> Could you please confirm that you would like us to ... ?

Some examples:

> Could you please provide permission for Support to re-run one or more pipelines in project `xyz` to investigate the issue you've described? Replying in this ticket stating you provide permission will be sufficient.
>
> Could you please provide permission for our Support Engineers to look at the CI/CD variables in the project so that we confirm they are correct? Replying in this ticket stating you provide permission will be sufficient.
>
> Could you please confirm that you would like us to add `example@email.address` to your account and make it the _primary_ email address? Replying in this ticket stating you provide permission will be sufficient.

### Impersonating

Impersonating a user is considered performing an action as another account, impersonating will update the **Current sign-in IP** and **Current sign-in at** for the impersonated user.

When impersonating a user, the administrator account will receive a slack message from the **Tines** app asking to confirm if the impersonation was a legit action.
