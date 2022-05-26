---
layout: markdown_page
title: How to Perform CMOC Duties
category: On-call
description: "Describes the role and responsibilities for CMOC rotation in Support Engineering"
---

- TOC
{:toc}

----

## Introduction

As the [Communications Manager on Call (CMOC)](/handbook/engineering/infrastructure/incident-management/#roles-and-responsibilities) it's your job to be the voice of GitLab to our users and stakeholders during an incident. To do this effectively you'll use a combination of [our status page](https://status.gitlab.com/) (powered by [Status.io](https://status.io)), Slack, Zendesk, and GitLab itself. The CMOC rotation is one of the rotations that make up [GitLab Support On-call](/handbook/support/on-call).

Our Slack bot [Woodhouse](https://gitlab.com/gitlab-com/gl-infra/woodhouse) provides a command (`/incident post-statuspage`) to quickly spin up an incident on [Status.io](https://status.io). From there, the basics of how to update and close incidents in Status.io are covered by their [Incident Overview](https://kb.status.io/incidents/incident-overview/) documentation. This document covers how GitLab specifically uses Status.io to perform those tasks. 

### CMOC Performance Indicators
{:.no_toc}

Success as a CMOC is determined by the following performance indicators:
- **Time to Acknowledge PagerDuty Pages**: Acknowledge all PagerDuty notifications within 15m and join the incident bridge. See [Acknowledge the PagerDuty Page](#acknowledge-the-pagerduty-page)
- **Frequency between status updates**: Post status page updates according to severity at documented intervals or other cadence if so communicated. See [Frequency of Updates](#frequency-of-updates).
- **Stakeholder communication threads created per incident**: Communicate incident existence to stakeholders according to the documented process. See: [Notify Stakeholders](#notify-stakeholders).
- **Handover issue created after a shift**: At the end of every shift, create a handover issue to prepare the incoming CMOC. See: [End of Shift Handover Procedure](#end-of-shift-handover-procedure)
- **Contact requests opened during shift per completed contact request issue**: Complete, handover or otherwise communicate plan to complete all incoming contact requests. See: [About Contact Requests](#about-contact-requests)
- **Participation in one training event per quarter**: Join at least one incident or participate in (or organize) a training activity. See: [CMOC Training Activities](#cmoc-training-activities)

## Things to Know

Before getting started, take note of the following sections or to get straight into the workflow start at [Incident Management](#incident-management).

### About Incidents

This section contains information specific to how incidents are started, what various status messages in PagerDuty mean, and the difference between the EOC and the Incident Manager during an incident.

#### How Incidents Are Declared
{:.no_toc}

Infrastructure uses [Woodhouse](https://gitlab.com/gitlab-com/gl-infra/woodhouse) to [declare incidents through Slack](https://about.gitlab.com/handbook/engineering/infrastructure/incident-management/#reporting-an-incident). Doing so will:

1. Automatically page the EOC, Incident Manager, and CMOC.
1. Create an issue for the incident in the [Production](https://gitlab.com/gitlab-com/gl-infra/production/-/issues/) issue tracker.
1. Provide a link to the Zoom call for the incident.
1. Create a dedicated Slack channel for the incident.

This information will all be posted to Slack in the `#incident-management` channel by Woodhouse and it'll look similar to the following example.

![Incident declared by Woodhouse](/images/support/cmoc_incident_declared.png){: .shadow}

GitLab team members are encouraged to use this method of reporting incidents if they suspect GitLab.com is about to face one.

#### PagerDuty Status Definitions
{:.no_toc}

- **Triggered** - "An incident exists that requires the attention of a CMOC."
- **Acknowledged** - "I have seen the page and am in the process of joining the incident Slack channel and Zoom call."
- **Resolved** - "I have joined the dedicated Slack channel for the incident along with the Zoom call, created the incident in Status.io, notified internal stakeholders, and labeled the incident issue and am actively working the incident."

**NB:** "Resolved" in PagerDuty does not mean the underlying issue has been resolved.

#### Deciding Whether to Initiate Status Page Communications: EOC vs. IM
{:.no_toc}

The Incident Manager (IM) is the DRI for the decision of whether to initiate public communications via the Status Page. When joining an incident as the CMOC you should inquire as to whether communications are currently required.

In later sections of this workflow it's called out that at times you should be asking the [Incident Manager (IM)](https://about.gitlab.com/handbook/engineering/infrastructure/incident-management/#roles-and-responsibilities) assigned to the incident for permission to move it between stages (open, monitoring, resolved). 

On the rare occasion that an incident does not have an Incident Manager, the [Engineer On Call (EOC)](https://about.gitlab.com/handbook/engineering/infrastructure/incident-management/#roles-and-responsibilities) assumes these responsibilities and you may ask them instead.

#### Reviewing Past Incidents
{:.no_toc}

You can always [review past incidents](https://status.gitlab.com/pages/history/5b36dc6502d06804c08349f7) if you need examples or inspiration for how to fill in the details for a current incident.

### About Status.io

#### Frequency of Updates
{:.no_toc}

Status.io should be updated whenever we have new information about an active incident that our stakeholders should be aware of. Outside of that, it should be updated at a consistent rate depending on the severity of the incident as outlined in the table below.

Once you join the incident Zoom call, take note of any updates that have been made to Status.io and the time they were made at. Set a timer to remind yourself and stick to the time intervals below unless you make a note of how long it will be until the next status update. For example, if you're in "monitoring" it may be appropriate to specify an hour before the next update.

| Incident Status | Severity 1 Update Frequency | Severity 2 Update Frequency | Severity 3/Severity 4 Update Frequency |
|--|--|
|Investigating| 10m | 15m | 15m |
| Identified | 10m | 30m | 30m |
| Monitoring | 30m | 60m | 60m |
| Resolved | No further updates required |

#### What If I Don't Know What to Say?
{:.no_toc}

- Provide a generic update based on the best information you have:

- _We're seeing elevated error rates on GitLab.com, investigation is underway in: link_
- _Some users are reporting connection issues to GitLab.com, we're working on it in: link_
- Craft a draft of what you think is correct. Whenever possible use ["I intend to..." language](https://www.youtube.com/watch?v=7KnPjakwqeI) when communicating with the Incident Manager and EOCs:

  - _@IM - I'm going to post: "We've isolated the network problem to the APAC region and are working with Cloudflare support to get it resolved_.
  - _"In my next update I'm going to move the status to monitoring"_
- Bias to action - you can post another update if there was an error in your last update.

- If there are no material updates to report, say something so that people know we care and are working on it. Below are a few example messages:
   1. _"No material updates to report. We're discussing if we should restore from backup or let the replica catch up first but we have not made a decision."_
   1. _"No material updates to report. We tried starting the Gitaly servers but we're still missing connectivity."_
   1. _"No material updates to report. We are doing a handover to a new CMOC since the current CMOC has been at it for three hours straight."_
   1. _"No material updates to report. We would like to thank Google for the #hugops tweet we received. LINK"_

- If you really don't know, it really is okay to ask!

### About Zendesk

#### Finding Related Tickets
{:.no_toc}

In some circumstances, the Incident Manager may ask you to find the number of tickets that an incident may have raised in order to evaluate the impact of the incident.

Because the default views will only show unassigned tickets in your region, start with using this [Zendesk Search](https://gitlab.zendesk.com/agent/search/1?type=ticket&q=created%3E4hours%20order_by%3Acreated_at%20sort%3Adesc%20group%3Anone%20group%3A%22support%22%20-form%3Abilling%20-form%3Asecurity) to find all recent tickets.

Alternatively, you can paste the following search string into the Zendesk search bar (useful if you are using Zendesk Quicktab extension): `created>4hours order_by:created_at sort:desc group:none group:"support" -form:billing -form:security`

This shows new tickets created in the previous 4 hours - change the range if the incident began earlier than that.

#### Tagging Tickets
{:.no_toc}

If there is any customer contact regarding an incident regardless of severity, you should create an incident tag in Zendesk as soon as possible. You can check for customer tickets by using the tips above, by scanning the FRT & Free ticket queue and validating the tickets, or by asking the wider Support team. You can create a tag on a ticket directly by finding the `tags` field and using the format `com_incident_####`. Replace #### with the production incident number of the issue. Once you've added the tag, submit the ticket with an appropriate `Incident First Response` macro and the tag will become available to use on other tickets.

Tagging tickets can be done throughout the incident process but the CMOC should check the queue for accurate tagging during the incident resolution stage. The tagging of tickets is useful for gauging support impact, ease of finding related tickets for active incident troubleshooting, and ease of finding related tickets for historical reference.

For details on tagging and tracking incidents, please see [Tracking Incidents](tracking_incidents.html) workflow.

### About Contact Requests

Whether related to an ongoing incident or not, Infrastructure or Security may ask you to reach out to one or more users if they detect unusual usage. Please follow the [Sending Notices](sending_notices.html) workflow to action these requests.

### How to page the CMOC?

You can page the CMOC even after incident creation. To engage the CMOC please follow the steps outlined in [How to engage the CMOC?](https://about.gitlab.com/handbook/engineering/infrastructure/incident-management/#how-to-engage-the-cmoc) handbook section.

## Incident Management

As the CMOC you'll guide the incident through the following three stages.

1. Stage 1: **Incident Creation** - Creating the incident in Status.io, joining the incident Zoom call, and [notifying stakeholders](#notify-stakeholders).
1. Stage 2: **Updating Incidents** - Following along with the work being performed by the EOC and any assisting engineers to resolve the incident and making updates to Status.io along the way while adhering to the [Frequency of Updates](#frequency-of-updates) schedule. We may also be going through the Zendesk queue replying to incident tickets and tagging them.
1. Stage 3: **Incident Resolution** - Setting the incident to **Monitoring** in Status.io for a period of time to ensure that the issue does not recur before we close it out, eventually setting the incident to **Resolved**, and adding a link to the post-mortem issue in Status.io. In certain cases we may be asked to skip the monitoring period and move straight to **Resolved**.

The following sections outline how to perform each of the steps within these stages.

### **Stage 1: Incident Creation**

The following steps should be taken immediately after receiving a PagerDuty page for an incident.

#### Acknowledge the PagerDuty Page

We mark the PagerDuty page as [acknowledged](#pagerduty-status-definitions) immediately upon receiving it. Acknowledge the page through the mobile app, web interface or PagerDuty App in the `#support_gitlab-com` Slack channel.

#### Join Incident Channel & Zoom

Before you create an incident in Status.io you should join the incident Zoom call. A link to the call is provided in the incident declaration post by Woodhouse in `#incident-management`.

Your role while on the call is to follow along while the incident is worked and make updates to Status.io either when asked to or when it's necessary. Oftentimes chatter in this room will be lively, especially in the early stages of an incident while the source of the issue is being discovered. Use your best judgment on when it's appropriate to speak up to avoid vocalizing at inopportune times. You can always ping anyone on the call through Slack if you need to ask a non-urgent question about the situation.

#### Upon First Joining
{:.no_toc}

The first thing you should do is to verify that you can be heard by others in the room. To do this, say something like:

> "Hi, I'm the CMOC on duty. I intend to send an update, please review this in the Slack thread."
>
> "Hi, I'm the CMOC on duty, how can I help?"

Whatever you choose to say, make sure that you receive a verbal acknowledgement directed at you before you move on to focus on other aspects of the incident.

#### When CMOC Is Asked to Take Action
{:.no_toc}

From time to time, you may be asked to perform some specific tasks in the room. Always verbally acknowledge any such asks by repeating your understanding of the ask back to the requestor. This helps everyone understand that the ask was heard, and also serves to verify that everyone has the same understanding of some action to be taken.

In some cases, the ask may be implicit, rather than explicit. If you're in doubt, always speak up and ask for confirmation. For example:

> **IM:** CMOC is here, we need to roll out a first update.

A good response would be to ask for confirmation that an action was requested:

> **CMOC:** IM, do you want me to send a first update on status.io?

A better response would be to assume that an action was requested, relay your intended course of action in response, and give the requestor the opportunity to provide input:

> **CMOC:** IM, acknowledged, I will draft an update for status.io and ping you in Slack for input.

#### Create Incident

You can create an incident on Status.io with minimal effort through Slack (provided by Woodhouse) **OR** manually if need be (e.g., Slack is down or you need to customize the incident more than what the Slack form allows).

##### Slack (provided by Woodhouse)
{:.no_toc}

You simply need to issue `/incident post-statuspage` from anywhere on Slack. You will be presented with a pre-filled form that you can update to your liking. Once submitted, the incident will be broadcasted to the following media:

- Email subscribers
- Webhook subscribers
- Slack subscribers
- IRC (#gitlab on [Libera Chat](https://libera.chat))
- MS Teams subscribers
- [Twitter](https://twitter.com/gitlabstatus)
- [RSS feed](https://status.gitlab.com/pages/5b36dc6502d06804c08349f7/rss)
- [iCalendar](webcal://status.gitlab.com/pages/5b36dc6502d06804c08349f7/calendar/all.ics)

##### Manually
{:.no_toc}

After logging in to Status.io you'll be met with the dashboard that displays various statistics about our current status. Create a new incident by clicking `New Incident` along the top bar.

![New incident](/images/support/cmoc_new_incident.png){: .shadow}

Now on the incident creation screen, you'll be asked to fill in the details of the incident, including its severity and what systems are affected. The following is an example of what a new incident would look like if we're experiencing an issue with a delay in job processing on GitLab.com.

![Incident details](/images/support/cmoc_incident_details.png){: .shadow}

Change the following values:

`Title` - Titles should be brief and concise. The incident title should answer the question: **In simple terms, what is the issue?**

`Current State` - In nearly all cases an incident should be created in the `Investigating` state. If it's been communicated to you that we're aware of what is causing the current incident this could be set to `Identified` from the beginning.

`Details` - In keeping with our value of [transparency](/handbook/values/#transparency), we should go above and beyond for our audience and give them as much information as possible about the incident on its creation. This field should **always** include a link to the incident issue from the [production issue tracker](https://gitlab.com/gitlab-com/gl-infra/production/issues) so that our audience can follow along.

`Incident Status` - When creating a new incident this will never be `Operational`. The status of an incident depends entirely on its scope and how much of the platform it's impacting.

`Broadcast` - Always check each box in this section.

`Message Subject` - Always leave this at its default value.

`Affected Infrastructure` - This should almost always be unchecked so that the value of the `Incident Status` field is only applied to the specific aspects of the platform that are affected by the incident. In the example above we're only experiencing an issue with job processing so only `CI/CD` is selected.

#### Notify Stakeholders

The CMOC now needs to notify internal stakeholders of the incident using the Incident Notifier Slack workflow. This should be done after the severity of the incident has been confirmed by the Incident Manager.

This workflow, once used, will ask you to fill out a form with details of the incident and will then post those details to `#community-relations` and `#customer-success`. This serves to notify those teams of the incident. A copy will also be sent in a direct message to you, should you be asked to post it anywhere else. To engage the workflow:

1. Click the lightning bolt in the message composition box within `#support_gitlab-com` and select `Incident Notifier`.

   ![Incident Notifier Application](/images/support/cmoc_incident_notifier.png){: .
shadow}

1. Fill in all of the details.
1. Click `Submit`

#### Label Incident Issue

It is important that we are able to differentiate incidents which included outbound status page and related notifications from those incidents which were deemed less impactful to our customers. This can be useful both in filtering for active incidents which include outbound notification as well as for after-incident reporting.

Whenever a GitLab service incident includes the use of a status page incident this should be identified on the GitLab Incident Issue. See this, and other uses of this scoped label in the [Incident Management section of the handbook](https://about.gitlab.com/handbook/engineering/infrastructure/incident-management/#labeling).

1. Add the `~Incident-Comms::Status-Page` scoped label to the incident issue.

#### Resolve the PagerDuty Page

We mark the PagerDuty page as [resolved](#pagerduty-status-definitions) once everything in Stage 1 has been completed. Resolve the page through the mobile app, web interface or PagerDuty App in the `#support_gitlab-com` Slack channel.

### **Stage 2: Updating Incidents**

To publicly communicate attention and progress incidents should be updated according to the [frequency of incident updates table](/handbook/support/workflows/cmoc_workflows.html#frequency-of-updates) unless you communicate otherwise. 

To update an active incident, click the incidents icon from the dashboard. 

![Active incident dashboard icon](/images/support/cmoc_update_incident_dashboard.png){: .shadow}

Then click on the edit button next to the incident.

![Incident edit button](/images/support/cmoc_update_incident.png){: .shadow}

Change the following values:

1. `Current State` - Change this depending on the current state of the incident and whether or not we've identified the cause (Identified) or implemented a fix (Monitoring).
1. `Details` - Be as descriptive as possible about the update and include a link to the production issue.
1. `Broadcast` - Check all boxes.
1. `Current Status` - If the incident has improved or worsened update this value. If neither, leave it as it was from when the incident was created.
1. `Set Status Level` - Uncheck this and keep only the affected component selected unless the incident has increased in scope and now affects other components of our infrastructure. **IMPORTANT** These must be checked individually as in the screenshot below.

A ready to be published update should look similar to the following.

![Incident update](/images/support/cmoc_post_incident_update.png){: .shadow}

Make sure to [verify](https://wordcounter.net/character-count) the update length before publishing it. If it exceeds 280 characters, the update won't be published on twitter with no failure notification from `status.io`.

If the incident title needs to be changed or additional affected infrastructure needs to be added,
this is done separately. Instead of clicking the update incident button, click on the incident title to view
the details page. Then click the edit pencil icon next to the incident name or affected infrastructure section
to change them. It is very similar to [adding Post-Mortem](#add-post-mortem).

After publishing the update, visit the live status page to verify that the update went through and looks clear.

### **Stage 3: Incident Resolution**

When it comes time to close an incident out as resolved, the following flow is usually used.

1. Switch to a monitoring state for a time.
1. Resolve the incident.
1. Add a link to the production issue to the post-mortem section of the incident.

As noted in the specific sections below, some of these steps are situational and may not be used for every incident.

#### Begin Monitoring (Situational)

Once the component affected by the incident has returned to operating normally we will often switch the incident over to a monitoring period to ensure that the problem does not recur. The monitoring period typically lasts for 30 minutes by default, but it can vary and a different amount of time may be requested by the Incident Manager. **It may also be requested that the monitoring period be skipped entirely.**

If a monitoring period will be used simply edit the incident, and configure the update similar to the following.

![Switch to monitoring](/images/support/cmoc_monitoring_stage.png){: .shadow}

Take special note of the changes made to the following fields at this stage.

1. `Current State` - Change to `Monitoring`.
1. `Details` - Along with any information specific to the incident be sure to mention that all systems have returned to normal operation, that we're monitoring in order to ensure the issue doesn't recur, and provide an estimate for how long we'll be monitoring before we resolve the incident. For example:

   > *While all systems are online and fully operational, out of an abundance of caution we'll leave affected components marked as degraded as we monitor. If there are no recurrences in the next 30 minutes, we'll resolve this incident and mark all components as fully operational.*

1. `Incident Status` - At this point, the affected component should be back to normal operation. However, to be clear that we're still in the incident management process we will **not** flip this back to `Operational` until we leave the monitoring state.

#### Resolve Incident

Once we're confident that systems have returned to normal operation, **the Incident Manager has given the all-clear**, and we've completed a monitoring period (if we chose to) of the incident we should mark it as resolved.

Once these conditions are met, make an update to the incident and change the following fields.

1. `Current State` - Change to `Resolved`.
1. `Details` - State that the issue has been resolved and that systems have returned to operating normally. Be sure to also include a link to incident issue even if you've already done so in previous updates so that any users who missed them know where to go for more info.
1. `Incident Status` - Change to `Operational`. **IMPORTANT**: Make sure the "Apply status level to all affected infrastructure" box is checked.
1. Double check the status page to make sure everything looks good.

Before resolving the incident your draft should look similar to the following:

![Resolve incident](/images/support/cmoc_resolve_incident.png){: .shadow}

#### Add Post-Mortem

A review will be conducted by production engineering for every incident that matches a [certain criteria](/handbook/engineering/infrastructure/incident-management/#incident-review). Status.io allows us to add a link to a post-mortem after an incident has been resolved which will then be viewable on our status page for that specific incident.

Do the following to add a post-mortem to a resolved incident:

1. From the dashboard click the `Incidents` button.

   ![Active incident dashboard icon](/images/support/cmoc_update_incident_dashboard.png){: .shadow}

1. Scroll down and click on the title of the incident.

   ![Incident history list](/images/support/cmoc_post_mortem_incident_list.png){: .shadow}

1. Click `Add Post-Mortem` and supply the link to the issue being used for the incident review, this is usually the same issue that was opened for the incident.

   ![Add post-mortem link](/images/support/cmoc_add_post_mortem.png){: .shadow}

## Maintenance Management

Infrastructure will at times plan scheduled maintenance events for GitLab.com, some of which will directly impact users. New maintenance events are announced as issues created in the [gl-infra/production](https://gitlab.com/gitlab-com/gl-infra/production/-/issues) issue tracker using the [external_communication.md](https://gitlab.com/gitlab-com/gl-infra/production/-/blob/master/.gitlab/issue_templates/external_communication.md) issue template accompanied by the [**Scheduled Maintenance**](https://gitlab.com/gitlab-com/gl-infra/production/-/labels?utf8=%E2%9C%93&subscribed=&search=scheduled+maintenance) label.

In the event that a maintenance will affect users, infrastructure can request that the maintenance be visible on our status page, and if required, that the CMOC actively provide status updates during the maintenance window. In these cases infrastructure will apply the [**CMOC Required**](https://gitlab.com/gitlab-com/gl-infra/production/-/labels?utf8=%E2%9C%93&subscribed=&search=cmoc+required) label to the issue, causing a notification to be sent to the `#support_gitlab-com` channel that mentions the on-call CMOC. Once this notification is received the CMOC uses the details within the issue to create the maintenance in Status.io.

To create a new maintenance event, click `New Maintenance` from the Status.io dashboard.

![New Maintenance](/images/support/cmoc_new_maintenance.png){: .shadow}

The contents of the maintenance should be filled out according to the details provided in the maintenance issue. Once complete, it might look something like the following.

![Maintenance Details](/images/support/cmoc_maintenance_details.png){: .shadow}

### Rescheduling a Maintenance Event
{:.no_toc}

In case you are required to reschedule a maintenance window, Go to _status.io_ > _Maintenances_ tab
![Maintenance Tab](/images/support/cmoc_select_maintenance.png){: .shadow}

Select the maintenance you need to reschedule.
![Maintenance selected](/images/support/cmoc_get_in_maintenance.png){: .shadow}

Update the new schedule time by hitting on the _Reschedule Maintenance_ button **Make sure you have the correct timezone details when updating** Then hit save.

### Sending Updates About Maintenance Events
{:.no_toc}

> **Note About Automated Maintenance Events**: On the Maintenance Event page you may see `Automation: Running`  with red text in parentehsis next to it reading `(Disable)`.
Once `(Disable)` has been clicked and subsequently disabled it cannot be re-enabled. 
In order to `Post Update` and `Finish Maintenance` the automated Maintenance Event must be `(Disable)`.
After being disabled all future updates to this Maintenance Event must be manual updates from that point forward.

To send an update about a maintenance event, such as a reminder, go to the _Maintenances_ tab in Status.io and select the one that needs an update. On the maintenance's information page, make note of whether automatic email reminders are set to go out. If yes, make sure not to send email broadcasts for your update in order to avoid sending duplicate reminders to subscribers. Once ready to update, select the _Post Update Without Starting_ button.

![Post Update Without Starting](/images/support/cmoc_post_without_rescheduling.png){: .shadow}

Enter the update details provided by the Infrastructure team and have them confirm the appropriate broadcast channels before proceeding to send the update. If "Send Reminders" was enabled in the maintenance information page, be sure not to check "Notify email subscribers" in the broadcast settings.

![Broadcast Maintenance Update](/images/support/cmoc_broadcast_maintenance_update.png){: .shadow}

Once the GitLab Status Twitter account has posted about the maintenance schedule, send a link of the tweet to the `#social_media_action` channel to let the social team know that you'd like amplification on our GitLab brand twitter account. This should only be used once during a selected scheduled maintenance timeline, preferably mid-week prior to the scheduled maintenance.

## End of Shift Handover Procedure

It's necessary to inform the ingress CMOC of any relevant activity that ocurred during your shift or if there are incidents that are still ongoing. To perform a handover create an issue in the [CMOC Handover](https://gitlab.com/gitlab-com/support/dotcom/cmoc-handover/issues) issue tracker using the [Handover](https://gitlab.com/gitlab-com/support/dotcom/cmoc-handover/issues/new?issuable_template=Handover) template. Do this even if nothing happened during your shift, signaling that everything is fine is also useful information. It's critical to remember that since we [work out in the open](https://about.gitlab.com/blog/2015/08/03/almost-everything-we-do-is-now-open/) by default, the CMOC Handover issue tracker is open to the public. **A handover issue should be made confidential if it must contain any sensitive information.**

If handover occurs during an active incident where the quick summary you'd provide in the issue is insufficient to properly prepare the ingress CMOC of the situation, you are encouraged to start a Zoom call in [#support_gitlab-com](https://gitlab.slack.com/archives/C4XFU81LG) and invite the ingress CMOC to it so that they can be caught up synchronously. You can use the following slash command to expedite setting the meeting up.

```plain
/zoom meeting CMOC Handover Briefing
```

## CMOC Training Resources

### CMOC Shadow PagerDuty Schedule
{:.no_toc}

The [CMOC Shadow Schedule](https://gitlab.pagerduty.com/schedules#PQBZCSY) can to be used by anyone who wishes to shadow the CMOC to learn before officially acting as CMOC. A soon-to-be-CMOC can adjust the schedule to match their working hours by clicking _Edit this schedule_ > _Add Another Layer_; add your username and the days/hours that you wish to shadow.

### CMOC Training Activities
{:.no_toc}

A "training activity" for CMOCs is an activity under which CMOCs are exposed to items in the workflow with the expressed purpose of maintaining or increasing performance against [CMOC performance indicators](#cmoc-performance-indicators).

Some example training activities are:
- tabletop exercises
- a "CMOC Squawk" in which CMOCs in a region synchronously or asynchronously discuss process improvements, tips and tricks
- Being the CMOC or shadowing an actual incident: real life training is training too!
