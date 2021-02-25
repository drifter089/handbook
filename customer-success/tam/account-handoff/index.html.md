---
layout: handbook-page-toc
title: "Account Hand-Off TAM-to-TAM Checklist"
---

## On this page
{:.no_toc .hidden-md .hidden-lg}

- TOC
{:toc .hidden-md .hidden-lg}

View the [TAM Handbook homepage](/handbook/customer-success/tam/) for additional TAM-related handbook pages.

----

TAMs will need to occasionally transfer accounts they have been working with to another TAM (e.g. a TAM changes territories, a realignment occurs in Sales, a need to equalize books of business, etc.), and they should use this handbook page to help guide them through important questions and topics during the handoff.

Below are checkpoints during the account handoff process that TAMs can use to keep track of information they will need in order to successfully transition accounts. For the sake of this page, most of this guidance is directed towards the new TAM but is helpful information for everyone involved.

## Account Handoff CTA

The first step once you are aware of a handoff is for the new TAM to open an [CTA in Gainsight](/handbook/customer-success/tam/gainsight/#ctas). This is where you will track completion of tasks necessary to a successful handoff. Be sure to select the "Account Handoff" playbook and assign the relevant tasks to the previous and new TAM.

### Account Handoff CTA Tasks

- Open a [handoff issue](https://gitlab.com/gitlab-com/customer-success/tam/-/issues/new?issue%5Bassignee_id%5D=&issue%5Bmilestone_id%5D=#) to be the source of truth for any discussion items, questions, notes, etc. that pop up during the handoff process (new TAM)
- Have an internal meeting with old and new team (new TAM)
- Intro new team on next cadence call (old TAM)
- Send intro email to customer with new team's contact details (old TAM)
- Invite new team to customer Slack channels if applicable (old TAM)
- Add new account team to SFDC and/or Gainsight (new TAM)
- New TAM turn on watch notifications for collaboration project (new TAM)

As you follow the tasks in the CTA and collaborate in the issue and in the internal meeting, be aware of the following suggestions to ensure a seamless handoff experience.

## Topics to Cover

### License

Discuss the state of the customer's license, such as:

- Active users count
- True-up assessment
- Upcoming renewal

### Communication

One of the most important parts of a handoff is excellent transparent and timely communication. It's important for the new TAM to have a thorough understanding of the communication channels used to interact with the customer.

- What is the customer's preferred method of communicating?
- How often does the customer usually communicate with us outside of calls?
- Who are the most important contacts and who do we interact with regularly?
- What is the frequency for [cadence calls](/handbook/customer-success/tam/cadence-calls/)?

### Collaboration Project

Does a collaboration project exist? If not, discuss with the previous TAM to understand why not and evaluate if it would be helpful going forward or not. If yes, review all open issues and ask the previous TAM to update/close any that may be out of date. It may be worthwhile to skim closed issues to understand what types of initiatives or questions they've had in the past.

Pay special attention to the customer's product sentiment and their feature requests, and check if the list of feature requests is up to date, are they prioritized, how many have been shipped, etc. If there are any gaps, ask the previous TAM for any additional context they may have.

### Gainsight

While all information in Gainsight is important, the below sections have been found to be the most useful to review when getting up to speed on an account.

#### Attributes

Review the "Attributes" tab in the Gainsight account to get a high-level overview of account-related details.

#### Health Score

Review their [health score](/handbook/customer-success/tam/health-score-triage/) and any [timeline](/handbook/customer-success/tam/gainsight/timeline/#timeline-view) entries associated with it, and discuss the history of the relationship, as well as what the previous TAM anticipates from the customer going forward.

#### Success Plan

Review their success plan to understand the strategic objectives the customer cares about. If it's out of date or empty, sync with the previous TAM to get their feedback and determine a strategy to build the success plan out.

#### Adoption

Understand what [stages](/handbook/customer-success/tam/stage-adoption/) the customer is using on GitLab or on other tools; if any stages are unknown, ask the customer once you've started cadence calls with them.

#### Opportunities

Review the open opportunities for the account; is there an upcoming renewal, or is there an upgrade potential? Additionally, by clicking into a closed-won opportunity, you can access the command plan that SALs/AEs complete during the sales process.

#### Salesforce Activities

If you're interested in past email exchanges, these can be found in the "Salesforce Activities" tab on the account, which if you click on the eyeball will direct you to Salesforce to view the contents. If there are several entries with the same title, choose the most recent one, as it will also show the history of the messages in the email thread.

### Meetings

### Meeting Notes

Meeting notes docs should be in the standard location in [Google Drive](https://drive.google.com/drive/u/1/folders/0B-ytP5bMib9Ta25aSi13Q25GY1U); if there isn't a folder for the customer there, create one. If there isn't a notes doc in the folder, ask the previous TAM for a link to their notes and ask them to move the notes to the folder. Also do a search within Google Drive of the customer name to identify any other relevant documents or materials and move any to the folder if not already there.

Read through past meeting notes to get full clarity of the history of our engagement, and take special note of any meeting notes from past [EBRs](/handbook/customer-success/tam/ebr/).

#### Meeting History

It can be helpful to look at the history of the types of calls the previous account team has had with the customer. This information most likely can already be found in the meeting notes and/or Gainsight timeline, but if you want to get a list for a high-level understanding of the face-to-face meetings the customer has been involved in, you can pull up the calendars of the SAL/AE, SA, and TAM and search for the customer name in Google Calendar to get a list of all meetings they've had with them in chronological order.

#### Chorus Recordings

While not all customer calls are recorded, many are, and they can be a wealth of information. To avoid becoming overwhelmed, ask the previous account team if there are any impactful or informative calls to watch, and review any with a subject line that may be particularly interesting (ex. EBRs, product feedback, etc.) or that could help fill in some gaps from meeting notes.

### Support Tickets

Thoroughly understand the main technical issues the customer cares about and has had problems with. Take note of critical open tickets and collaborate with support as needed, and review any key technical issues the customer experienced in the past; for example, migrations, integrations, major upgrades, etc.

### Installation

Assess the environment where the customer's GitLab instance is hosted.

- Self-Hosted Assessment:
  - Health Checks
  - Architecture diagrams
  - Machine specifications
  - GitLab configuration files
- GitLab.com (SaaS) Assessment:
  - Runners Evaluation
    - Private On-Prem Runners
  - CI Minutes Utilization
    - CI usage trends (i.e daily, weekly, monthly etc.)
