---
layout: handbook-page-toc
title: Log and audit requests
description: "Overview of agrigated information which GitLab Support may provide to customers, from the gitlab.com logs. Details beyond a summary require a Security request."
category: GitLab.com
subcategory: Legal
---

## On this page
{:.no_toc .hidden-md .hidden-lg}

- TOC
{:toc .hidden-md .hidden-lg}

# Log requests for GitLab.com

Users often ask for access to GitLab.com logs, typically, due to [IP blocks](/handbook/support/workflows/ip-blocks.html), a possible security issue, or for internal auditing purposes.

Always include a link to the log as an internal note, with additional information if needed.

If required, post in the `#support_escalations` channel for a senior engineer or manager review.

A standard response is available in ZenDesk as a macro `GitLab.com::Audit logs access request`.

Log requests beyond a summary (similar to the examples below) or where logs are not readily available on Kibana should be handled according to the process outlined in the handbook page dedicated to [providing assistance to GitLab.com customers during customer-based security incidents](/handbook/security/customer-requests/).

## Who can make a request

Requester must be Account Owner of a Paid Account.  
 - Must verify that this is who is making the request

## What we can provide

We can provide the following information:
- Information found in the Audit Events Features
- Information about who has accessed the account/projects that the customers owns.  This can include:
  - IP address
  - number of users
  - number of times accessed
  - number of unique IPs
  - range of timestamp of occurance
  - project path

## What we cannot provide

We cannot provide the following information: 
- Information about accounts or projects that the requestor does not own
- Any information that would disclose GitLab confidential information or processes   

## Examples

The following are examples to provide a better idea of what responses we can provide.

### Example 1: Who accessed a specific repo

A customer, who had accidentally set their project to the incorrect visibility setting, wanted to know if anyone outside the company accessed their project. Here is a modified excerpt of the response:

> Excluding users who have the company email domain, 2 users viewed the main project page a total of 4 times between 20:06 and 20:10 UTC 2019-08-15. However, I can confirm that all 4 instances originated from one of the IP addresses you provided as being from your office.

From ticket: https://gitlab.zendesk.com/agent/tickets/129594

### Example 2: IP block

User writes in to say their entire team is getting blocked and they want to know the source. When the user writing in has access to the projects in question, we can provide the specific path(s).

> It appears that the majority of requests that returned `401`, which likely caused the temporary block, involved `/project/path`.

Example ticket: https://gitlab.zendesk.com/agent/tickets/132652

Also see ["Identifying the Cause of IP Blocks on GitLab.com"](/handbook/support/workflows/ip-blocks.html).

### Example 3: GitLab requests action due to high load

GitLab reached out to the owners of a project that was causing concern for the production team, who asked Support to reach out. The user wanted to know where the requests were originating from.

> There are 3 different IPs showing in our logs, 2 of which are based in CountryA and 1 in CountryB (please note these locations may not be accurate as they are based purely on geolocation web searches). They also all have the same user agent.

Example ticket: https://gitlab.zendesk.com/agent/tickets/130153
