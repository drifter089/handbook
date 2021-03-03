---
layout: handbook-page-toc
title: "Professional Services Delivery"
description: "Describes the workflow governing delivery of GitLab professional service projects."
---

## On this page
{:.no_toc .hidden-md .hidden-lg}

- TOC
{:toc .hidden-md .hidden-lg}

### Overview

The purpose of this page is to describe the workflow governing delivery of professional service projects. We will start by outlining the general workflow that is common across all service delivery categories. Then we will describe the differences for engagements that do not fit the general workflow shown below.

![ps-delivery-workflow](../PS-delivery-workflow.png)

[Source](https://docs.google.com/presentation/d/1TOI2aoseBoyWYQC6-xpJVMknEncCNreSFfMvOHO7EBA/edit?usp=sharing),  internal only

<!---Update this below
GitLab professional services employs three different workflows that control projects for the following categories:  standard professional services, education, and dedicated engineers.  Each of these categories have unique attributes that warrant a different approach.--->

### Planning and Delivering Standard Services

#### Scheduling

The Professional Services (PS) team scheduling is processed through the Sr. PS Project Coordinator (PC).  Our PSA sytem calendar is our single source of truth for scheduing our customer and internal projects.  

Follow these steps to schedule a customer engagement.

Submit a Resource Request through Mavenlink with the following details:

* Role
* Dates to be worked
* Hours requested
* Soft or Hard allocation

The PC will review the master planning for availability and procecss the resource request.  If there is a schedule conflict the PC will provide another set of project dates.

Scheduling updates and changes follow this same process with a resource request  in Mavenlink.

If a customer project has not booked, but planning/ scheduling discussions need to take place, reach out to the PC to review.

#### How to schedule internal time

There are 2 project that track internal time, Creditable and Non Creditable.  If hours need to be scheduled for the projects, a comment in the project activity and mention the PC:

* Requested Dates 
* Hours requested
* Task assignment
* Soft or Hard allocation

#### Weekly schedule review meetings

A weekly PS Operations call is held each week to review shedules.  This type of cadence and review of the schedule will help with utilization, planning and forecasting purposes.

#### Kicking off an engagement

See the details in the Project workflow section of the [PS Project Management](/handbook/customer-success/professional-services-engineering/project-mgmt/) page.

### Holding discovery sessions
During discovery or fact finding sessions with the customer, PSEs will often have a predefined list of questions that need to be answered to to ensure we're designing and building the appropriate solution given customer constraints and requirements. It is good practice to send these question to the customer prior to the discovery call so they can be prepared for the discussion.

During the call, take notes to ensure that things that have validated or invalidated your initial assumptions have been captured. At the end of the meeting, review the things you've learned to memorialize what will be designed and built. Reiterating back your understanding of the details of the agreement instills confidence in the customer representative that we understand their requirements and can deliver what was reviewed.

After the meeting, based on meeting notes, create issues in the gitlab.com customer collaboration project outlining the work. Include Consider using a simple template with `Overview`, `Open Questions`, `Tasks`, and `Acceptance Criteria`. These can be helpful in further memorializing the scope of work with the customer and getting asynchronous feedback to open questions. Make sure the `overview` is as detailed as possible, and the `tasks` section has build-to level tasks (e.g. update congregate list() function to include data from CI sources).

### Planning and Delivering Education Services

PSEs or Technical Instructors who deliver GitLab Education Services instructor-led courses can use the following workflow to ensure smooth interactions with customers. In addition, PSEs and Technical Instructors should complete these [GitLab Certified Trainer](/handbook/customer-success/professional-services-engineering/gitlab-certified-trainer-process/) steps for each course they are scheduled to deliver.

#### Preparation steps

1. The Project Coordinator will contact the customer with a "Welcome to PS Email".  The email will include proposed training dates and training session planning meeting details, which will include the trainer in the meeting. Trainer participation in this meeting is critical -- please let the Project Coordinator know if you need the meeting to be rescheduled to ensure your attendance.

1. The Project Coordinator will use these [email communication templates](https://docs.google.com/document/d/1rJ9q9gEzsumRxDhoWEe45u70efmKA0eWNg69WONuCYs/edit?usp=sharing) to ensure communication of the key details with the customer and training participants.

1. During the training planning meeting, be sure to discuss and document all of the event logistics listed in the [Training Event Plan Template](https://docs.google.com/document/d/1huNauyfhFPvLCuo-9T7Ol3FtBDYowYxiP_T5ItP2FN4/edit?usp=sharing). The Project Coordinator will create a draft of the Training Event Plan prior to the meeting and update the document during the training planning meeting.
1. The Project Coordinator will add the confirmed date(s) and start/stop time(s) for each training session to the issue.

1. The Project Coordinator will set up a Zoom Webinar session for each session using [these set up instructions](/handbook/customer-success/professional-services-engineering/remote-training-session-setup/) and add the registration link(s) to the issue. You will receive an email message with your unique link to join the Zoom Webinar session. Make sure to locate the Zoom webinar information within the email message and familiarize yourself with the Zoom functionality. Here is a useful Zoom article for [Managing Attendees and Panelists in a Webinar](https://support.zoom.us/hc/en-us/articles/115004834466-Managing-attendees-and-panelists-in-a-webinar). Depending on your Zoom set up, you may want to log into https://zoom.us

1. At least 2 weeks prior to the training session, the Project Coordinator will email the session registration link(s) to the customer, asking them to send the link(s) to each of the employees whom they want to attend the session(s). When each person registers they will receive an automated confirmation email with a Zoom Webinar join link unique to each person, along with a link to add the session to their calendar.

1. Contact the PS Instructional Designer to confirm you have the latest versions of course slides and other materials.

1. Review the train-the-trainer (T3) video for the course you are delivering.

1. Review, practice, and use these [PS Remote Training Tips and Tricks](/handbook/customer-success/professional-services-engineering/remote-training-tips/).

1. Complete the GitLab Training Lab set up steps below. Make sure that you review the lab exercises and ensure that the labs are working properly prior to the first day of class. 

1. When it's time to join the Zoom Webinar session as a presenter, use the Panelist link to join the session.

##### Training lab pre-course instructor workflow

PS uses the [GitLab Demo Cloud](http://gitlabdemo.com/) as the standard environment for hands-on course lab activities and hands-on certification assessments. Follow these steps to set up your course attendees for lab access.

**1. Register your account**
1. Self-register at [gitlabdemo.com](http://gitlabdemo.com/) to create your credentials on the GitLab instance during the automated provisioning process. This will provide you with your own user account and organization group for your own projects. This step is not specific course session, but is a required step as a GitLab team member.
1. Credentials for your course attendees will be generated  when they redeem an invitation code that you’d provide to them. In essence, we create a unique invitation code for each course session that attendees redeem on [gitlabdemo.com](http://gitlabdemo.com/) on Day 1 of the course session, and their GitLab instance credentials are generated after they enter their code.

**2. Generate invitation codes**
1. The Project Coordinator will generate the invitation code for your class using the steps below and provide the invitation code information approximately a week prior to your class start date as part of the instructor friendly reminders post within your Mavenlink project.
1. Visit gitlabdemo.com
1. Sign in with Okta
1. Click `Invitation Codes` in the top navigation.
1. Click the `Create Invitation Code` button in the top right corner.
1. Fill out the form. Your invitation code is generated and GitLab group is created when you click the green button.
1. You can see a list of previously created invitation codes and links to relevant details.
1. For any edits/extensions/etc or any custom redemption rules (different durations than our standards) make a request in the #demo-systems Slack channel

**3. Share the invitation code and access instructions below with attendees**: You can do this via an email to attendees as well as including it within their course materials, letting them know the expiration date (which is 14 days from the date you generated the code).


**Demo Cloud Access Instructions:**
1. Visit gitlabdemo.com
1. Click the blue button for redeeming the code above. An anonymous user account and password will be created.
1. Click on the red button to download your credentials (very important, don’t forget to do this since you will not be able to access this page again).
1. Click the blue button to access your group and create your first project.

**4. Training Closeout**:
1. Create a PDF version of the slides and send it to the Project Coordinator. The Project Coordinator will send a copy of the slide deck to the customer and save a copy to the Active Projects Google Drive folder.
1. The Project Coordinator will download the Zoom attendee report and send a Next Steps email to the customer main point of contact using an email template located in the [email communication templates](https://docs.google.com/document/d/1rJ9q9gEzsumRxDhoWEe45u70efmKA0eWNg69WONuCYs/edit?usp=sharing).
1. <strong>For courses that have certification assessments</strong>: When an attendee submits their certification assessment, review their work in the demo lab cloud within 7 days of the attendee's submission and manually release their results using the attendee's completed Google Form. [Here are the detailed instructions](https://gitlab.com/gitlab-com/customer-success/professional-services-group/education-services/-/wikis/GitLab-Certification-Instructions) for certifying customers.

### Planning and Delivering Dedicated Engineering Services

Work in progress


### Employing Subcontractors

If the project requirements exceed the current capacity of the available resources then the professional services team may employ a subcontractor to help deliver the project.  The following provides a checklist of items to process before and during the use of a subcontracted resource:

1. Confirm that the terms and conditions agreed to with the customer enable the use of a subcontractor.  In some cases, GitLab must first obtain written approval from the customer in order to employ a subcontractor.

1. Generate a list of potential subcontractors.  GitLab has established relationships and signed Master Service Agreements with a collection of professional services firms.  Review the list of firms and select ones that have pools of resources with the correct set of skills and certifications.

1. Contact the GitLab Channel Account Manager (CAM) who owns the relationship for the selected firms.  Provide the  CAM with a description of the services GitLab intends to subcontract along with the project start/end date and an estimate on the quantity of time GitLab intends to procure.

1. Contact the selected firms through an introduction by the CAM.  GitLab should then submit the requirements to the partner firm and request resumes and rates for any resources the partner deems available and suitable for the project.
Interview proposed resources. GitLab will meet with the proposed resources to determine if the person is a fit technically as well as from the perspective of fitting in with the project team that includes both GitLab and customer personnel.

1. Develop a Statement of Work between GitLab and the selected firm.  The Statement of Work should employ best practices that we use when developing SOW’s for GitLab customers.  The SOW should also align with terms and conditions that GitLab is obligated to follow.

1. Sign Statement of Work.

1. Onboard the resource.  This includes procuring a GitLab email address for the selected partner personnel.  It may also include procuring access to customer systems.

1. Track time.  As described in additional sections on this page, GitLab must account for all time logged against a project.  For subcontracted resources, GitLab will employ the following procedures:
    * Subcontractor submits a weekly status report outlining billable hours delivered along with a description of the services performed during the submitted hours.
    * GitLab staff load the time detail into the GitLab time tracking system.


1. Offboard the resource.  At the conclusion of the project, remove access and determine how to handle incoming email for the provisioned email address.





### Time Tracking

Accurate time tracking records of hours is essential to provide team utilization metrics along with ensuring revenue can be recognized based upon percentage completion of a project scope as outlined in a Statement of Work ("SOW"), and this data is used in the calculation of gross margin.  Key points for time tracking include:

- All Time should be recorded in the Mavenlink time sheet on a customer or internal project.
- Best practice is to record time at the end of each day.  This provides the most accurate account of hours worked and when it was worked.
- Each PSE is required and responsible for tracking their own hours, and submitted weekly by Friday EOD, for the week worked.  A minimum of 40, or whatever the hours worked per week is in your country.

Hours represent work hours that a staff member reports as being aligned to a specific SOW or internal task. The format for daily time tracking for each team member is shown below, and approved by the project lead and the teams PCs. Rounding to the nearest quarter hour is acceptable. 

#### Quarterly Time tracking entry and approval workflow

* All hours are submitted and approved in Mavenlink on a weekly basis
* The quarterly hours report is pulled from Mavenlink and reivewed by the PC and then provided to the PS Delivery Manager for review and approval
* A PS Delivery Manager will APPROVE the hours, create an issue and attach it to the Time Tracking Epic with the `ManagerCertifiedTimesheet` label
* The approving manager will submit to the Head of PS, [Sr. Director of Professional Services](https://about.gitlab.com/job-families/sales/director-of-professional-services/) for next level approval.  The Head of PS with apply judgement on productive utilization.
* Head of Professional Services will submit to the Professional Services Finance Partner for final approval.


#### Issue board

The [PS Issue Board](https://gitlab.com/gitlab-com/customer-success/professional-services-group/ps-plan/-/boards) contains everything that the group is working on, from strategic initiatives to SOW writing.

#### Mavenlink project categories

* ALL customer project hours
  
  * Project tasks are aligned with SOW activities and hours tracked against the tasks
  * Internal/ Sales Handoff Calls
  * Internal/ External status meeting
  * Support ticket submission while the project is in progress
  * Weekly/ Final customer reports and documentation
  * Status/ Close out customer calls
  * Customer Travel

* PS TimeTracking - Creditable
  
  * SKO
  * Contribute
  * Commit
  * Sales Assistance
    * All Pre-Sales activities
    * SOW Creation
  *  Support Assistance
     * Support Cases, (if pulled into customer questions after the project is closed)
     * Engineering Support
  *  Practice Development
     * Creating process/documents
     * Templates
     * Articles/ Tools
  * Product Development
  * Mentoring

* PS TimeTracking - Non Creditable
  
  * Knowledge Sharing
    * Slack
    * Internal Q&A
  * General Administrative
    * Time Sheets
    * Expense Reports
    * Reviews
    * HR Items
    * General Emails
  * Meetings/ Staff Time
    * Internal Meeting
    * 1:1s
    * Weekly Webinars
    * All Hands
    * Team Calls
  * Travel Time
    * Excluding Customer Travel
  * Personal Enablement
    * Development
    * Ramp Up
    * HR Training
    * Customer project shadow

* Time off, Holidays, along with Friends & Family Days
  * Time should be submitted in the time off feature in Mavenlink
  - Holidays along with Friends and Family day are scheduled in the Mavenlink calendar, which flow to the master planning schedule
  - Review [the company time off process](https://gitlab.com/gitlab-com/customer-success/professional-services-group/ps-process/-/issues/25)







