---
layout: handbook-page-toc
title: Support Channels
description: "Communication channels for GitLab Support"
---

## On this page
{:.no_toc .hidden-md .hidden-lg}

- TOC
{:toc .hidden-md .hidden-lg}

Our [support engineers](/job-families/engineering/support-engineer) handle the channels listed below. They are sorted in order of priority (strictest SLA at top), and as a result, it is possible that channels that appear lower in this list experience longer delays in receiving responses. We are actively [hiring](/jobs/) more Support Engineers to strengthen the team and provide support to the community.

## Emergency Tickets

When an emergency ticket comes in, it triggers a [PagerDuty](https://gitlab.pagerduty.com) incident. All Support Engineers must have the PagerDuty application installed on their phones once they are added to the on-call rotation schedule.

When a PD incident is triggered, the alarm will go off for the person on call. You should acknowledge the incident within 5 minutes, or the person on second level support will be alerted. The PD incident will have the link to the corresponding Zendesk issue from where you will continue the conversation with the customer.

Once acknowledged, you need to login to [Zendesk](https://gitlab.Zendesk.com), go to the corresponding ticket and let the customer know that you will handle their case and send them a Zoom meeting link. If the customer is unable to access Zoom, you may need to use phone, Skype, WebEx or Hangouts.  The full procedure for emergency tickets can be found [here](/handbook/support/on-call/#pagerduty-alerts).

Once the emergency has been resolved, return to the ticket in [Zendesk](https://gitlab.Zendesk.com) and document any steps taken to resolve the issue.

### Crisis Situations

If you are unable to help the customer and their instance is in a critical state (unavailable, uncertainty of data loss, etc.), you should **escalate** the PD incident to second level support, and work through the issue together. It may also be necessary to ask for assistance from a developer in the appropriate Slack channel. While you are waiting for help to join the call, focus on getting their server to a usable state.

If an emergency takes longer than an hour to resolve, and/or multiple people are or need to be involved, **start a Google Doc** that is open to the customer and the wider team at GitLab, and keep track of the issues and ideas there. Zendesk's 'linear' display of communication with a customer is not as effective in crisis situations, and the majority of developers do not have access to Zendesk in the first place. Announce the Google Doc in the appropriate Slack channel (`#infrastructure`, `#development`, `#whats-happening-at-gitlab`) so that individuals can contribute solutions and ideas. When the crisis has been resolved, be sure to transfer pertinent know-how from the Google Doc to relevant documentation, handbooks, and/or issue trackers, so that the Google Doc can be deprecated a.s.a.p.  In addition, Support Engineers and Developers involved in the crisis should make time to have a hangout for hand-off to make sure that everyone has the chance to recover and stay clear-headed.

## Security Disclosures

We have a [Responsible Disclosure Policy](/security/disclosure/). Emails sent to security@gitlab.com go into Zendesk and receive an autoresponder that says:
`"Thank you for your responsible disclosure of a potential GitLab vulnerability. We'll follow up with you within one business day."`
We also accept reports via [HackerOne](https://hackerone.com/gitlab); see [more information](/handbook/support/channels#hackerone) on this channel.

Occasionally, issues do not get automatically labeled as `security` or assigned to the Security Team; refer to [working with Security](/handbook/support/workflows/working_with_security.html) for information on identifying and handling these tickets. Sometimes issues that would be better served directly by Support Engineers end up in the `security` queue.  It is okay to take and handle issues such as 2-factor authentication and other authorization configuration problems for GitLab.com.
users.

When in doubt, please be very patient with these reports. Do not say 'there is no problem'. You might be misunderstanding something that can lead to a 0-day disclosure. Give examples and keep asking questions until you understand the problem or until the researcher concludes there is no problem. If someone invested time to help us, offer to mention them on our [Security Researcher Acknowledgments page](/security/vulnerability-acknowledgements/) even if there was no actual vulnerability. If you say that we'll get back to them, **always** mention that they can email us at any time for an update. This is really important to prevent a 0-day disclosure resulting from us forgetting to respond.

Issues created from reports to `security@gitlab.com` must follow the [security issue triage](/handbook/engineering/security/#issue-triage) process.

Reports that are PGP-encrypted will be handled by the [Security Team](/handbook/engineering/security/#external-contact-information).

### HackerOne

We also use [HackerOne](https://hackerone.com/gitlab) to manage security reports. The HackerOne program is managed by the Security Team. The complete workflow for handling HackerOne reports can be found on the [Security Team page](/handbook/engineering/security/#hackerone-reports).

If a Team Member requires access to HackerOne, create an [access request](https://gitlab.com/gitlab-com/Team-member-epics/access-requests/-/issues/new?issuable_template=New_Access_Request).

## Support Tickets for customers on paid plans

Customer can submit support tickets via the Support Portal. The Support Team follows our [workflow for Zendesk tickets](/handbook/support/workflows) to manage these.

Tickets can be submitted by customers on paid plans for either gitlab.com or self-managed.

## Support for customers on free plans

For customers on free plans (.com 'Free' and self-managed 'core'), there is the [GitLab forum](https://forum.gitlab.com). The Support Team does not currently work with the forum - the Community Relations Team aims to answer questions there on a best-effort basis in conjunction with the wider community.

## GitLab issue trackers

When an issue for either GitLab.com or self-hosted installations is confirmed (bug, regression etc), it will be reported on the main [GitLab project issue tracker](https://gitlab.com/gitlab-org/gitlab/issues). As a Support Team member, most issues will be reported here, however you might report issues in one of the other following areas listed below (based on the specific feature or product):

- [GitLab Runner issue tracker](https://gitlab.com/gitlab-org/gitlab-runner/-/issues) for issues specific to GitLab Runners.
- [GitLab Charts issue tracker](https://gitlab.com/gitlab-org/charts/gitlab/-/issues) for issues specific to GitLab Helm Charts.
- [GitLab Omnibus issue tracker](https://gitlab.com/gitlab-org/omnibus-gitlab/-/issues) for issues specific to GitLab Omnibus.
- [GitLab Documentation issue tracker](https://gitlab.com/gitlab-org/gitlab-docs/-/issues) for issues related to the docs site.

## Non Channel Work

The Support Team also works to improve GitLab: write documentation, fix bugs, add features, and polish the website.
