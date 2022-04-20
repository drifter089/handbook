---
layout: markdown_page
title: How to be a Support Manager On-call
category: On-call
description: "Describes the role and responsibilities for the Support Managers rotation in Support Engineering"
---

- TOC
{:toc}

----

## Introduction

The Support Manager On-call helps coordinate responses to urgent and important situations that arise within the scope of delivering a quality
experience to GitLab customers.

The Support Manager On-call is one of the rotations that make up [GitLab Support On-call](/handbook/support/on-call/).

## Expectations for Support Manager On-call

As part of [GitLab Support on-call](/handbook/support/on-call/), Support Managers serve in a rotation. The support manager on-call is responsible generally for:

1. Ensuring customer emergencies are [handled promptly and accurately](#handling-customer-emergencies-and-incidents), [according to SLAs](https://about.gitlab.com/support/)
1. [Handling customer-related escalations](#mechanics-of-handling-escalations) during business hours according to the [support escalation definitions of urgency](/handbook/support/internal-support/support-escalations.html#definition-of-urgency)
1. Acting as a [notification point for security incidents](#act-as-a-notification-point-for-security-incidents)
2. Providing direction and assistance with regards to [Upgrade Assistance Requests](#provide-assistance-with-upgrade-assistance-requests) initiated during the shift
3. Help ensure new tickets don't breach by keeping an eye on the `Needs Org / FRT` view. Ping your region in `#support_team-chat` if tickets are building up to remind people to take new tickets. See [Meeting our FRT SLA](/handbook/support/workflows/meeting-frt-sla.html) for details of how we meet our FRT SLA.

## Handling customer emergencies and incidents

The [Support Engineer on-call](/handbook/support/on-call/) is the first responder for customer emergencies. Managers support this work as follows:

- Act as the next-tier escalation point for emergency pages that get missed (you will be notified automatically by PagerDuty).
- Be aware of ongoing emergencies, and assist or lead our response as appropriate.
- During an emergency: find additional staff for subject-matter expertise; replace the on-call engineer if needed; lead any Zoom call(s) as needed; hand off the emergency to the next on-call manager.
- Find additional staff when there are [multiple emergencies](/handbook/support/on-call/#handling-multiple-simultaneous-emergencies).

## Handling customer-related escalations during business hours

[Support Escalations](/handbook/support/internal-support/support-escalations.html) are handled by the Support Manager on-call.

Your responsibilities are as follows:

1. Triage and investigate tickets and internal-requests that are announced in `#support_escalations`.
1. Establish ownership and assignment for escalated tickets.

You can use [Support Team Skills by Subject](https://gitlab-com.gitlab.io/support/team/skills-by-subject.html) to find appropriate engineers to assign.

A very high percentage of support escalations involve licenses and renewals. For guidance in handling these escalations, please see the [Plan/License Escalations Workflow page](/handbook/support/license-and-renewals/workflows/managers_working_with_extensions.html).

**NOTE:** GitLab team members may attempt to draw attention to tickets in regular support Slack channels (`#support_self-managed`, `#support_gitlab-com`, `#spt_managers`). Any such attempt constitutes an escalation. Redirect the team member by responding to their post with **only the `:escalate:` emoji**, which will send an automated and anonymous reply describing the correct process.

**NOTE:** There are two other distinct situations, not discussed on this page:

1. [Escalated Customers](/handbook/customer-success/tam/escalations/)
1. [Emergencies that become Escalations](/handbook/support/workflows/emergency-to-escalation-process.html)

### Mechanics of handling escalations

Some steps of escalation management are handled by bots and auto-responders. The text `**BOT**` is used below to show these steps.

1. When someone declares an escalation using the [support escalation form](https://gitlab-com.gitlab.io/support/toolbox/forms_processor/support_escalation/):
   1. **BOT**: Creates a new Issue in the [support escalation issue tracker](https://gitlab.com/gitlab-com/support/escalations/-/issues).
   1. **BOT**: Slack announcement is posted to `#support_escalations`, with an `@mention` of the current on-call Support Manager's name.
   1. In many cases **BOT** adds an internal note to the Zendesk ticket and escalation issue, documenting the escalation.
1. Add the `:eyes:` emoji to acknowledge you are looking at the escalation.
1. In the Zendesk ticket, use the `Support::Managers::Escalated Ticket` macro to crosslink the escalation issue, discussion thread and tag the ticket as escalated.
1. Assess the ticket, and the business case behind the escalation (triage).
   - Questions to the escalation initiator can be put in Slack (synchronous) or in the escalation Issue (asynchronous).
1. If you need input or help from engineers, initiate a new thread in `#support_gitlab-com`, `#support_self-managed` or `#support_licensing-subscription`. Then return to the thread in `#support_escalations` and comment that all **technical** ticket-related discussion is happening in the ticket (or in the new thread). This helps ensure all technical discussion stays in one channel/thread.
1. [Resolve the escalation thread](#resolving-an-escalation).

### Rejecting an escalation request

There are times when an escalation request does not meet the threshold for escalation. In such situations, return to the thread in `#support_escalations` and notify the escalation initiator.

### Resolving an escalation

An escalation is considered resolved when the correct next-step is identified and underway; it does not require the Zendesk ticket to be Solved or Closed.

When an escalation is resolved:

1. Apply a `:green-check-mark:` emoji to the escalation notification in `#support_escalations`.
1. Update the associated escalation Issue with an appropriate comment, and Close it.
1. Consider applying an appropriate label, such as one of the scoped label examples below, to help categorize and track trends in escalations.
    - `~Escalation::License-Issue` : Identifies the core issue at hand resolves around licensing / subscriptions
    - `~Escalation::Response-Time` : Useful when the purpose of the escalation is to expedite a response to an issue or case

## Act as a notification point for security incidents

When GitLab experiences a [security incident](/handbook/engineering/security/security-operations/sirt/security-incident-communication-plan.html#extended-team-roles-responsibilities-and-points-of-contact), the Support Manager on-call is responsible for triaging and responding to customer communications stemming from the security incident. This may include involving the [CMOC](/handbook/support/workflows/cmoc_workflows.html).

## Provide assistance with Upgrade Assistance Requests

[Upgrade assistance requests](https://about.gitlab.com/support/scheduling-upgrade-assistance.html) are currently triaged by engineers as part of the [Working on Tickets](/handbook/support/workflows/working-on-tickets.html) but in some cases the triaging agent(s) may need assistance from Support management.

#### Example situations and potential solutions

- User requesting Upgrade Assistance outside of [GitLab Support Hours](/support/#definitions-of-gitlab-global-support-hours)
   - Reach out to your reports to determine whether any individuals would be open to shifting their working hours to accommodate the day/time being requested
   - Work with the end user to reschedule for another date/time that is more amenable to support staffing
- User has provided insufficient [scheduling notice](/support/scheduling-upgrade-assistance.html#how-far-in-advance-must-i-open-a-support-request-to-request-upgrade-assistance)
   - Evaluate whether the scope of the upgrade may allow for an expedited review within the original timeframe (ie. single minor version upgrade on single node omnibus)
   - Work with the end user to reschedule or advise them that we may be able to perform a review of their plans but may not be able to schedule a session with an engineer
- Last minute change in assignee availability
   - Work with available team members to determine if the upgrade assistance can be transferred to a new engineer and communicate the change(s) to the end user for awareness

## Reassigning or swapping your on-call shift

If you will be unable to handle on-call for a few hours on a weekday due to being engaged in a customer call or otherwise, arrange for another manager to handle on-call responsibilities temporarily:

1. Ask a specific manager to cover; if that doesn't work,
1. Post a request in `#spt_managers` for any manager to volunteer to cover.

To swap your on-call duty with someone, follow the steps listed under [Swapping on-call duty](/handbook/support/on-call/#swapping-on-call-duty).

## Manually triggering a PagerDuty notification

At times, you may receive an escalation where the customer is reporting a situation that qualifies for emergency support under our [definitions of support impact](https://about.gitlab.com/support/#definitions-of-support-impact). In such cases you may elect to trigger an emergency directly, rather than asking the customer to open a new emergency ticket.

You can trigger a PagerDuty notification by using the [`Support::Managers::Trigger manual emergency`](https://gitlab.com/search?utf8=%E2%9C%93&group_id=2573624&project_id=17008590&scope=&search_code=true&snippets=false&repository_ref=master&nav_source=navbar&search=id%3A+360074073259) macro in Zendesk.

Alternatively, you can manually trigger a PagerDuty notification through PagerDuty itself.

Login to [gitlab.pagerduty.com](https://gitlab.pagerduty.com) and select **+ New Incident** from the upper right corner. Then fill out the form as follows:

- **Impacted Service**: Customer Support
- **Assign to**: Customer Emergency Rotation
- **Title**: Add the Zendesk ticket number here

No other fields need to be filled out, therefore you may then click **Create Incident**

![Manually triggering an emergency](/images/support/manually-trigger-emergency.png){: .shadow}

## Special Handling Notes

[Special handling notes](/handbook/support/workflows/customer_emergencies_workflows.html#special-handling-notes) are documented on the [customer emergencies on-call workflow](/handbook/support/workflows/customer_emergencies_workflows.html). As a Support Manager, you are empowered to handle these (and other) unique situations
according to your judgment. If you need help or advice, don't hesitate to [escalate to unblock](/handbook/values/#escalate-to-unblock).

### Compromised instances

We advise Support Engineers to contact a Support Manager before offering a call in the case of a [compromised instance](/handbook/support/workflows/customer_emergencies_workflows.html#compromised-instances). 

Support's role in these cases is to help the customer get to a good, known working state as quickly as possible. The fastest route will be to restore to a previously known good state (most often by restoring from a backup). Customers with an instance in this state will have other concerns though, and likely be in a heightened emotional state:
- How did this happen? (Which we may or may not easily be able to answer, and they should do this forensic analysis _after_ they have restored.)
- How can we recover from this without restoring? (They can't "safely". We advise a restore to have 100% confidence in their environment.)
- What data was accessed? (This is always a challenging question, and if the compromise was led by a human, they may have covered their tracks. We may never have full knowledge. They should start restoring ASAP, and do forensics after.)

If moving towards a call is the right thing to do, consider joining the call _before_ (or instead of) the engineer to communicate the scope of what can be accomplished. 

Example framework for a call we establish (or a bridge call the customer is leading):

> Hi `customer`. Based on the ticket it sounds likely that your instance is compromised. In cases like these we've prepared a set of best practices ([GitLab internal link](https://gitlab.com/gitlab-com/support/support-ops/zendesk-global/macros/-/blob/master/macros/active/Incident/Compromised%20Instance.yaml)) to help you get back up and running as quickly as possible. We're here to support and advise where GitLab is concerned. Unfortunately, GitLab cannot provide a one-size-fits-all solution or comprehensive checklist to completely secure a server that has been compromised. GitLab recommends following your organization's established incident response plan whenever possible.

> The first step is to shut down the instance, create a new one at the same version, and restore your most recent backup. This ensures you are operating on a "clean" environment, where you have confidence that all the software installed is unmodified. Please get that process started;  we are monitoring this ticket with HIGH priority. If you have any problems getting set up or restoring, please let us know in the ticket immediately. 

> After your new instance is set up, you need to upgrade to a more recent version of GitLab before you expose this server to the public Internet. If you have any trouble with the upgrade process, let us know in the ticket immediately.

> Finally, as described in the recovery guide previously sent (should have been shared in the ticket via the [Compromised Instance Zendesk macro](https://gitlab.com/gitlab-com/support/support-ops/zendesk-global/macros/-/blob/master/macros/active/Incident/Compromised%20Instance.yaml), you should do an audit of the integrity of GitLab itself: checking for any users, code, webhooks, runners or other settings that you did not enable yourselves. If you have any questions, please let us know in the ticket.

> I'm going to leave the call now, but rest assured that we're on standby and ready to help as you work through this.
