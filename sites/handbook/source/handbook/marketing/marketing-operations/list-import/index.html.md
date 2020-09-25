---
layout: handbook-page-toc
title: "List Imports"
---

## On this page
{:.no_toc .hidden-md .hidden-lg}

- TOC
{:toc .hidden-md .hidden-lg}

The MktgOps team is responsible for importing records into Marketo for both field events and prospecting. List imports are processed in **Marketo** which has native matching by `Email Address` functionality.    

**Field event list uploads are to be done *before* any kind of follow up or outreach is done so we can ensure proper order of operations & attribution is given correctly.**

There are three primary ways to import records into the database:

| Import Method | SLA | Submission Instructions | Operations Instructions |
| :------------ | :-- | :---------- | :-------- |
| Zoominfo w/in SFDC | self-managed | [Instruction video how to do this can be found in the handbook](https://about.gitlab.com/handbook/marketing/marketing-operations/zoominfo/) | Not applicable |
| csv file | **Accepted by OPS** - 24 business hours<br><br>**Upload to SFDC** - up to 5 business days | Use [MktgOPS **general** list import request template](https://gitlab.com/gitlab-com/marketing/marketing-operations/issues/new?issuable_template=general-list-import-request), format as a Google Sheet (Gsheet) & place **link to Gsheet in issue**<br><br>[Written Instructions how to use template](#import-cleaning-template) | [Ad Hoc Upload](#ad-hoc-import) |
| List from Field Event, Sposorship or Advertising | **Accepted & uploaded by OPS** - 24 business hours | Use [MktgOPS **event** clean and upload issue template](https://gitlab.com/gitlab-com/marketing/marketing-operations/issues/new?issuable_template=event-clean-upload-list), format and clean csv per instruction & place **link to Gsheet in issue**<br><br>[Written Instructions how to use template](#import-cleaning-template) | [Field Event Upload](#field-and-corporate-event-import)<br><br>[Alliance Event Upload](#alliance-event-upload) |

#### Import Methods and their SLA
The SLA for each import method has been decided based on the perceived optimal response time. The turnaround time for an `Event, Sponsorship and or Advertising` list upload is deemed a high priority due to the nature of necessary `SDR` outreach on "warm" prospects. If a list of prospects cannot be considered "warm", please expect a turnaround time of the listed 5 day SLA and use the appropriate template.


#### If a last minute request, please open issue any way and ASK for a faster turnaround or ping OPS in `#mktgops` slack channel to discuss options.
{:.no_toc}

#### Import Cleaning Template - Info for Pre-MktgOps Hand-off

- Please utilize the [Google Sheet](https://docs.google.com/spreadsheets/d/143REaMQLyIy7to-CFktL45TTTLZxBQRJUDIOMCA3CVo/edit#gid=257616838) included in the `event list upload` and `general list upload` issue templates. This spreadsheet template allows for quick edits and faster data checks, such as:
     - Capitalizing `First name` and `Last name`
     - Highlighting `last names` that appear more than once in green for faster duplicate detection
     - Highlighting duplicate emails and GitLab emails in red
     - Labeling possibly erroneous emails as `FALSE`. Be advised, this does not work for all email domains
     - Highlighting when `self` or `GitLab` are listed as `Company Name` in red
     - Converting `State` abbreviations from `Canada` and the `US` into full names
     - Highlighting when `Country` names match with each other in green for faster typo detection
- Be aware that any changes to the spreadsheet layout may affect the built-in formulas. Consults MktgOps before making changes
- Columns highlighted in teal are considered `Required Data` and not including this data is grounds for refusal

**DO NOT MAKE CHANGES TO THE ORIGINAL SPREADSHEET OR INPUT DATA INTO IT. MAKE A COMPLETE COPY AS INDICATED IN THE LIST UPLOAD ISSUE TEMPLATE**

The following data cleanup is required for any list prior to sending it to the Marketing Operations team. **If your spreadsheet/data does not meet these guidelines it will be returned to you to fix prior to being uploaded.**
- It is the responsibility of the person submitting the list to clean the list utilizing the import cleaning template
- All fields are separated into their own column
     - Person name separated into two columns - `First Name` `Last Name`
     - Duplicates must be reviewed and reduced
     - Address separated into individual fields (`Street`, `City`, `State/Province`, `Zip/Postal Code`, `Country`)
     - `Country` that **are not** `United States` or `Canada` *must* have `State` field deleted or cleared as it will create conflicts
- Preferred format for Marketo upload is .csv, but will accept an .xls, or .xlsx. Provide as Google Sheet in the upload issue. **DO NOT** upload the file directly on the issue. Uploading files to the issue exposes ALL collected personal data to the internet and opens GitLab up to litigation
- Record ownership will be assigned using established lead routing, which is [controlled by LeanData](/handbook/marketing/marketing-operations/leandata/)
- In order to mark leads as `Opt-in = TRUE`, a record of the terms and conditions the leads agreed to upon having their data collected must be recorded. Check the `terms of service` wording has been recorded in the upload issue **before** opting in leads to receive marketing communications. No ToS, no `Opt-in`. Period.
- If there are any records who have opted out of contact for any reason, define that on the spreadsheet by selecting `Opt-in = FALSE`
- Leave `Opt-In` empty if no other option is available

**Steps (also documented in *How it Works* tab of the spreadsheet):**
1.	Use the "Lead Data for upload" tab to drop your relevant data into the matching blue columns in the left-most rows (i.e. copy the column in your file for "First Name" and paste it in the column "First Name"). This tab will remain locked and untouched by MktgOps as they will `Duplicate` into a new tab for additional cleaning
1.	Do not alter any rows or columns with the green column headers. These contain formulas that will reference your inputs under the blue column headers and provide you with proper capitalization (see clarifications below for more detail), as well as data entry that is acceptable for Marketo/Salesforce, and check the syntax of the email provided by your event organizer.
1.	Check for any ""warnings"" highlighted in red in the blue columns and erroneous emails marked as `FALSE` in the green columns - if there are none, you are good to go! (If there are highlighted cells, follow the instructions in the *Warning Handling* steps below. Correct the errors and then proceed.)
1.	Copy the data found under the green header and PASTE > VALUES into the blue header section of the spreadsheet. Erase the green header section after the formatted data has been copied over
1.   Rename the spreadsheet to match the campaign tag name
1.   Give `edit access` of the spreadsheet to the relevant MktgOps member
1.	Post a link to the spreadsheet in the list upload issue
1.   Apply the ~"List Upload: Ready" label to the issue

**Error Handling:**
* **Email Syntax:** If the syntax of the email is not met (meaning it includes @ and a relevant ending such as .com or .co.uk or .io) it will be listed as FALSE under the green column headers and the email can be updated to make it ready for upload. Note that Google Sheets does not understand all email domains, such as `.mil` or `.us`, and those can be ignored
* **GitLab emails:** If the person has @gitlab in their email address, they will be highlighted in red under the blue column header and should be removed
* **Duplicate Records:** If the person is a duplicate based on email address, they will appear red under the blue column header, and should be removed from the list.

Video of how this works tbd.

#### Best Practices
1. Remove inaccurate entries
     - `Job Title` **remove** "self", "me", "n/a", etc
     - `Phone` **remove** obvious junk numbers 0000000000, 1234567890, etc
1. **Blank fields** are better than junk data. We have enrichment tools that are designed to write to blank fields. Also we can run reports on the blank fields to find where our data gaps are.
1. If you do not have a CONTACT `Phone` **do not** substitute the ACCOUNT `Phone` and vice versa. Leave it blank.
1. Sort spreadsheet by `Email Address` and remove duplicates.
1. Only lead records from authorized sources -- meaning sources have legally obtained lead record data-- will be flagged as `Opted-in`. **No exceptions**
     - Pulling list of names out of LinkedIn and importing the records into SFDC **does not** qualify as compliant. In EMEA these lists *will not* be uploaded
     - Field events that have not gained consent from the attendees that their name will be shared **are not** compliant.
     - Getting someone's name and/or business card from a meetup **does not** qualify as compliant.
1. Remove all [embargoed country](https://about.gitlab.com/handbook/people-group/code-of-conduct/#trade-compliance-exportimport-control) records. 
1. `Washington DC` is a `State` value and is not to be split up between `City` `State`. 
1. `Zip Codes` contain five (5) numbers, States in US East may start with a `0`, make sure the `Zip/Postal Code` field is **plain text** and the leading `0` appears. 
1. If list contains non-Latin characters (ex. Asian languages), it must be uploaded to Marketo using UTF-8 and UTF-16. [Marketo instructions here](https://docs.marketo.com/display/public/DOCS/Import+a+Non-Latin+Characters+List). Salesforce Data Loader requires UTF-8 encoding, [instructions here](https://help.salesforce.com/articleView?id=faq_import_dataloader_specialchars.htm&type=5).

#### Required Data and Recommended Data

- For all uploads, there is mandatory data required for a successful upload. At a minimum, the following data must appear on the spreadsheet and **without this data an upload can be refused by MktgOps**:
     - First Name
     - Last Name
     - Company Name
     - Email Address
     - Country
     - State (United States and Canada only)
     - Campaign Member Status
- Additionally, there is data required for leads to be successfully routed to SDRs. While this information is not mandatory, it is strongly preferred and requested by the `Director of Marketing Department` to be included. GitLab employs tools that enrich leads and `Accounts`, but those tools are not guaranteed to work, so if the data can be found at the source it is preferred. Lastly, while it is less likely to have an upload refused due to missing this data, **missing this data is still considered grounds for refusal by the MktgOps team**. The recommended information is as follows:
     - Employee Bucket or Number of Employees
          - GitLab's segmentation standard for `Employees Bucket` includes the following groups: `1-99`, `100-499`, `500-1,999`, `2,000-9,999` and `10,000+`.
          - You can also enter an integer in for `Num Employees` and this will automatically update the `Employees Bucket` field if blank.
     - Opt-In status: `True`, `False`, or `leave blank` (determines if leads are **legally** signed up for GitLab's marketing emails)

### Campaign Templates - Info for Post-MktgOps Hand-off

At time of upload, a campaign should already exist in `Marketo` under the naming convention `YYYYMMDD_Event_Name`. Campaigns are to be created by the campaign's assigned `Marketing Program Manager` by copying a premade template in `Marketo`. MktgOps may need to assist in creating campaigns if the campaign type is brand new, specifically for `MQL scoring` reasons. As of September 2020, the following templates exist:
- [Conference](https://engage-ab.marketo.com/?munchkinId=194-VVC-221#/classic/ME5100A1)
     - [Conference Speaking Session](https://engage-ab.marketo.com/?munchkinId=194-VVC-221#/classic/ME5092A1)
- Direct Mail
     - [Direct Mail](https://engage-ab.marketo.com/?munchkinId=194-VVC-221#/classic/PG5392A1)
     - [Prinfection](https://engage-ab.marketo.com/?munchkinId=194-VVC-221#/classic/PG5386A1)
- [Field Event](https://engage-ab.marketo.com/?munchkinId=194-VVC-221#/classic/ME5083A1)
- [Content Marketing](https://engage-ab.marketo.com/?munchkinId=194-VVC-221#/classic/PG5111A1)
- [Content Syndication](https://engage-ab.marketo.com/?munchkinId=194-VVC-221#/classic/PG5149A1)
- [Pathfactory Asset](https://engage-ab.marketo.com/?munchkinId=194-VVC-221#/classic/PG3875A1)
- [Owned Events](https://engage-ab.marketo.com/?munchkinId=194-VVC-221#/classic/ME4722A1)
- [Survey](https://engage-ab.marketo.com/?munchkinId=194-VVC-221#/classic/PG6402A1)
- Virtual Events Folder
     - [Executive Roundtable](https://engage-ab.marketo.com/?munchkinId=194-VVC-221#/classic/ME6028A1)
     - [Livestream](https://engage-ab.marketo.com/?munchkinId=194-VVC-221#/classic/ME2919A1)
     - [Webcast by Region](https://engage-ab.marketo.com/?munchkinId=194-VVC-221#/classic/ME5512A1)
     - [Workshops folder](https://engage-ab.marketo.com/?munchkinId=194-VVC-221#/classic/MF5975A1)
     - [Self-service Events](https://engage-ab.marketo.com/?munchkinId=194-VVC-221#/classic/ME5143A1)
     - [Virtual Conference](https://engage-ab.marketo.com/?munchkinId=194-VVC-221#/classic/ME5121A1)
     - [Sponsored Webcasts](https://engage-ab.marketo.com/?munchkinId=194-VVC-221#/classic/PG5523A1)
     - [Vendor Arranged Meetings](https://engage-ab.marketo.com/?munchkinId=194-VVC-221#/classic/PG5698A1)

### Upload Process

In order to assure proper attribution of `MQL Scoring` and `Last Interesting Moments`, perform the following checks before any uploads occur:
- If a campaign does not exist, tag the `MPM` and or `Campaign Owner` on the `campaign epic` or `upload issue` to ask for campaign creation
- Check the MPM has filled in the campaign's `tokens`, which are found under the `My Tokens` tab in the main campaign  
     - `Tokens` are used via `Smart Campaigns` to apply `Last Interesting Moments` to all leads whom appear in the campaign. The minimum `tokens` that should be used relate to the campaign's `Event Name`, `Event Date` and `Landing Page URL`. Without these filled out, `Last Interesting Moments` will fill in permanently `blank`
- Review the components of the campaign. The needed components include:
     - `Static List(s)` in which to load lead list(s). The `static list(s)` should be renamed to resemble the program name. Depending on the campaign template, there may be more than one `static list` available. Some templates have been automated in a way that will fully launch relevant `Smart Campaigns` to append all relevant data, including `Campaign Member Statuses` and other important fields
     - `Smart List` for finding loading errors, or leads Marketo perceives as `duplicates`. If the `Smart List` list is not present, create a `Smart List` with the following filters: `Member of Program = current program name` and `SFDC Created Date = is empty`
     - `Smart Campaign` that triggers a `flow` when leads are added to the campiagn's static list(s). This flow should set to append data to all of the following fields **if the fields are empty ONLY**: `Acquisition Program`, `Acquisition Date` and `Person Source` (same as `Initial Source`). This `Smart Campaign` should end with a `Wait 5 Minutes` followed by `Change Program Status: Registered -> No Show`
     - `Smart Campaign` to add an `Interesting Moment`. Check there are enough `triggers` and `flows` to activate for each `Campaign Member Status` that appears on the list. Usually these include, but are not limited to: `Attended`, `Attended On-Demand`, `Visited Booth` and `No Show`. A genereal rule is to not include `Registered`, `Sales Nominated` or `Marketing Nominated`. The previously mentioned `tokens` will be used to apply the full event data of the `Interesting Moments` to the leads. Depending on the template, sometimes this `Smart Sampaign` and the previously mentioned campaign are one and the same

#### Best Practices and Procedure
1. Remove all unecessary data from `Job Title`, `Company`, `Names` and `Locations` columns, such as punctuation, `self`, etc, from the Google sheet before uploading. Check for any remaining duplicates and missing `Required Data`, pinging the `campaign owner` to fix, as needed
1. Only allow `Opt-in=TRUE` if the agreement to be contacted has been recorded in the list upload issue. Leave blank otherwise
1. Sort list by `Campaign Member Status` and then divide the whole list into separate tabs for the different statuses, eg. `Attended`, `Registered/No Show`, etc
1. Download the .csv file of the tabs to desktop
1. Load the corresponding .csv file to the corresponding `static list` and match up the fields on upload. These fields should mostly match automatically
     - If there is only `one static list` for the program, change the `Campaign Member Statuses` for each uploaded list before uploading the next. If all leads were uploaded at once and this is not possible, create a `Smart List` and filter by `Email Address` as a way to distinguish and change to the correct statuses
1. Always load `No Show` leads as `Registered` before setting them to `No Show`. Otherwise, they will not receive MQL scores. Check if a `Smart Campaign` changes the status to `No Show` before finalizing and if not, switch status from `Registered` to `No Show`
1. Depending on how the template has been set up, the remaining steps of appending data could be automated. If it is not, be sure to append the data listed above to the proper fields
1. After all steps of the needed `Smart Campaigns` have ran, including the often automated `Program Status: Registered -> No Show`, turn off the activated `Smart Campaigns` by "unscheduling" them
1. Check the `Loading Errors` smart list for any potential lead loading errors. 
     - Check the `Person Details` on any leads that show up on the smart list and correct the error. If Marketo indicates a `duplicate`, change the name on the lead by adding random but easily identifiable characters to the last name and manually force the lead to sync with SFDC. Find the lead in SFDC and merge it with the pre-existing duplicate. If there is a differing `email address` between the records, add the new `email address` as a secondary email. Add to SFDC campaign with the appropriate `Campaign Member Status`, if necessary
1. Once the Marketo --> Salesforce sync has completed, use the `[Upload checking template - do not erase](https://gitlab.my.salesforce.com/00Q?fcf=00B4M000004tTvd)` lead view to check data has been applied correctly, scoring has occurred and leads have routed. Note that routing will only occur if the adequate `MQL Score` has been met. Plug the `campaign tag`, or Marketo program name, into the lead view's `campaign name` field to view leads as a list
1. Ensure the number of leads present in the Salesforce campaign matches the total number of leads from the original spreadsheet
1. Use the `[Campaign Type and Progression Status](https://about.gitlab.com/handbook/marketing/marketing-operations/#campaign-type--progression-status)` page of the handbook and label the appropriate `Successful` leads with `Bizible Touchpoints`
1. Announce the upload in either the `event_list_upload` or `pub-sector-isr` Slack channels, depending on the campaign's intended `Sub-Region`. Include `Region` labels for private sector posts 
1. After verified completion of all tasks, remove ~"List Upload: Ready" label and notify in the issue of upload completion. Add ~"Lead Data::Active" label. Adjust the "MktgOps" label and apply a milestone
1. Close list upload issue 

<!--### Operations Upload Instructions 

* [Field & Corporate Event Import](#field-and-corporate-event-import)
* [Alliance Event Import](#alliance-event-import)
* [Ad Hoc Import](#ad-hoc-import)

#### Field and Corporate Event Import

##### Booth Leads
{:.no_toc}

- Create folder in corresponding Marketo program called “Lists”
- Add a static list to the folder title with the same Campaign_Name_Leads
- Check that Interesting Moments Smart Campaigns have been correctly activated
- Double check the lead list is cleaned to Marketing Ops standards for list import and load to static list in Marketo
- Leads are updated to  `Visited Booth`
-  `Follow Up Requested` is used if notes indicate a meeting request
- All leads `Visited Booth` or `Follow Up Requested` get Bizible touchpoints
- Update empty initial source by running a Smart Campaign with logic "If Person Source **is empty** change Person Source to `event type`"
- Update empty status/contact status of `Visited Booth` leads to `Inquiry` unless `Follow Up Requested` 
- If marked `Follow Up Requested`, Marketo scoring should automatically `MQL` lead 
- Post announcement to [`#event_list_upload`](https://gitlab.slack.com/archives/CQ8ADJMHT) Slack channel

##### Booth Leads - Received full attendee list
{:.no_toc}

- Create folder in corresponding Marketo program called “Lists”
- Add a static list to the folder title with the same Campaign_Name_Leads
- Check that Interesting Moments Smart Campaigns have been correctly activated
- Double check the lead list is cleaned to Marketing Ops standards for list import and load to static list in Marketo
- Full attendee list gets marked as `Attended` and X amount who visited our booth get marked `Visited Booth`
- Only `Visited Booth` and `Follow Up Requested` get Bizible touchpoints
- Update empty initial source by running a Smart Campaign with logic "If Person Source **is empty** change Person Source to `event type`"
- If attendee is not marked as `Visited Booth` or `Follow Up Requested`, update empty status/contact status to `Raw` 
- If attendee is marked `Visited Booth`, update empty status/contact status as `Inquiry`
- If marked `Follow Up Requested`, Marketo scoring should automatically `MQL` lead
- Post announcement to [`#event_list_upload`](https://gitlab.slack.com/archives/CQ8ADJMHT) Slack channel

##### Webcast and Virtual Sponsorship Leads
{:.no_toc}

- Create folder in corresponding Marketo program called “Lists”
- Add a static list to the folder title with the same Campaign_Name_Leads
- Check that Interesting Moments Smart Campaigns have been correctly activated
- Double check the lead list is cleaned to Marketing Ops standards for list import and load to static list in Marketo
- Update attendees campaign status to `Attended`
- Run a workflow to change left over `Registered` to `No Show`
- Only `Attended` get Bizible touchpoints
- Update empty initial source by running a Smart Campaign with logic "If Person Source **is empty** change Person Source to `event type`"
- Update empty status/contact status to `Inquiry` unless `Follow Up Requested`
- If marked `Follow Up Requested`, Marketo scoring should automatically `MQL` lead
- Post announcement to [`#event_list_upload`](https://gitlab.slack.com/archives/CQ8ADJMHT) Slack channel

##### Speaking session leads
{:.no_toc}

- Create folder in corresponding Marketo program called “Lists”
- Add a static list to the folder title with the same Campaign_Name_Leads
- Check that Interesting Moments Smart Campaigns have been correctly activated
- Double check the lead list is cleaned to Marketing Ops standards for list import and load to static list in Marketo
- Only leads who have attended one of our speakers get marked as `Attended`
- Only `Attended` get Bizible touchpoints
- Update empty initial source by running a Smart Campaign with logic "If Person Source `is empty` change Person Source to `event type`"
- Update empty status/contact status to `Inquiry` unless `Follow Up Requested`
- If marked `Follow Up Requested`, Marketo scoring should automatically `MQL` lead
- Post announcement to [`#event_list_upload`](https://gitlab.slack.com/archives/CQ8ADJMHT) Slack channel

##### Public Sector Leads
{:.no_toc}

- Create folder in corresponding Marketo program called “Lists”
- Add a static list to the folder title with the same Campaign_Name_Leads
- Check that Interesting Moments Smart Campaigns have been correctly activated
- Double check the lead list is cleaned to Marketing Ops standards for list import and load to static list in Marketo
- Leads are updated to `Visited Booth`
- All leads `Visited Booth` or `Follow Up Requested` get Bizible touchpoints
- Update empty initial source by running a Smart Campaign with logic "If Person Source **is empty** change Person Source to `event type`"
- If attendee is not marked as `Visited Booth` or `Follow Up Requested`, update empty status/contact status to `Raw`
- If attendee is marked `Visited Booth`, update empty status/contact status as `Inquiry`
- If marked `Follow Up Requested`, Marketo scoring should automatically `MQL` lead
- Post announcement to `#public-sector` and `#public-sector-isr` Slack channels

#### Gated Content - First and Third Party

- Create folder in corresponding Marketo program called “Lists”
- Add a static list to the folder title with the same Campaign_Name_Leads
- Check that Interesting Moments Smart Campaigns have been correctly activated and list the downloaded content
- Double check the lead list is cleaned to Marketing Ops standards for list import and load to static list in Marketo
- Leads are updated to `Downloaded`
- All leads `Downloaded` get Bizible touchpoints
- Update empty initial source by running a Smart Campaign with logic "If Person Source **is empty** change Person Source to `event type`" -->

#### Alliance Event Import

The Alliance list import follows the same guidelines as above

##### Process
{:.no_toc}   

1. Follow the instructions above. 
1. In **Marketo**, navigate to the static list file and `Select All` records. 
1. Under the `Person Actions` menu, navigate to `Marketing` -> `Change Data Value` 
1. In the lightbox, `Attribute` = `Alliance Record` / `New Value` = `true` -> then press `**Run**`
     * The `Alliance Record` checkbox activates: 
          * Correct ownership assignment in LeanData
          * Suppression of records in general Marketing communication


<!-- ##### Acceleration Team Monthly Import

The Acceleration Team has list import requests every month for their target patches. They presently are using a modified version of the Ad Hoc import template. 

**Key Differences**
- SLA of 5 business days *does not* apply to the monthly imports as there are multiple lists per issue & multiple issues per month
- Lists are raw data dumps from DiscoverOrg & not cleaned up 

In Marketo & SFDC there are two programs/campaigns set up to handle these imports. If you are coordinating efforts with another Ops team member be sure to clarify who is using which program/campaign to avoid commingling of records.

Please **do not** make any changes to the programs, campaigns or related workflows without talking to MktgOps first. 

##### Acceleration Upload - Ops 1
{:.no_toc}

* [Marketo Program](https://page.gitlab.com/#PG3938A1)
* [Salesforce Campaign](https://gitlab.my.salesforce.com/7014M000001lnDr)
* [CONTACT view](https://gitlab.my.salesforce.com/003?fcf=00B4M000004oVs8)
* [LEAD view](https://gitlab.my.salesforce.com/00Q?fcf=00B4M000004oVvM)

##### Acceleration Upload - Ops 2
{:.no_toc}

* [Marketo Program](https://page.gitlab.com/#PG4142A1)
* [Salesforce Campaign](https://gitlab.my.salesforce.com/7014M000001loEg)
* [CONTACT view](https://gitlab.my.salesforce.com/003?fcf=00B4M000004oXqs)
* [LEAD view](https://gitlab.my.salesforce.com/00Q?fcf=00B4M000004oXqn)

##### Process
{:.no_toc}

1. Verify that you have `Edit` access to all of the GSheets shared by the Acceleration team, if not ping the Sheet owner in the issue and request.
1. Clean up list to remove any columns not needed, update [`Field Names`](https://docs.google.com/spreadsheets/d/1dkh715tPngbY29PZis02dNPNd_Uc-xGbfV7LghsKWqE/edit?usp=sharing) to Marketo compatible values. 
     - Sort list by `Email Address` -> remove any lines without `Email Address` provided (we do not upload any record w/o `Email Address` it is our unique identifier across all systems)
     - Sort list by `Phone` -> check to ensure all values are correct format (plain text, XXX-XXX-XXXX or (XXX) XXX-XXXX), if there is an extension it should be obvious its an extension with either an `x` or `ext.` 
     - Sort list by `Country` -> if `Country` **does not** equal `United States` or `Canada` remove the value in `State`
     - Sort list by `Billing Country` -> if `Billing Country` **does not** equal `United States` or `Canada` remove the value in `Billing State` 
     - Update `State` and `Billing State` values to be full name not abbreviation
     - Select all -> **Data** Remove duplicates -> check "Data has header row" -> only select `Email Address` field as the duplicate value to analyze
1. Once list is clean in GSheet download as csv
1. **IMPORTANT** make sure both the SFDC & Marketo list are entirely empty & program has **NO** members *before* starting import. 
1. In **Marketo**, update the Smart Campaign - Flow Step 6 `Sync Person to SFDC`. **Assign to** needs to match the list owner as the campaign will trigger as soon as the list is uploaded.   
1. Click on the List in `List Actions` menu click **Import List**
1. In the lightbox that appears: 
     - Select `Browse:` and choose the csv list you just downloaded
     - Leave all other dropdowns with default values
     - Select `Next`
     - Review the `Marketo Field` matches
          - If there are any `--IGNORE--` use drop down to update selecting correct field, unless they are intentionally skipped
     - Select `Next`
     - `Aquisition Program` = `Acceleration Upload - Ops 1` or `Acceleration Upload - Ops 2` (we do not use Marketo Revenue Modeler but please fill in for accuracy)
     - Select `Import`
1. **Marketo** import will be running and associated Smart Campaign will immediately trigger. 
1. Wait for the sync between Marketo<>SFDC to finished processing list
1. In **SFDC**, the `Responses in Campaign` should MATCH the number of records uploaded into Marketo
1. Use the `Acceleration Upload` LEAD and CONTACT views to verify:
     - `Owner` matches the Acceleration SDR owning the list
     - `Person Source` value is not blank &/or is set to `DiscoverOrg`
     - `Status` equals `Raw` if net new record
1. From **SFDC** you will **Import to Outreach**
     - Select all records in **SFDC**
     - Click `Import to Outreach` button
     - **Outreach Everywhere** window will open - may ask to import records click "import" -> if errors see troubleshooting section
     - Select all records in **Outreach Everywhere**, if more than 50 you will need to click link to "apply to all" 
     - Click the `...` and select `Add tag` - first import you will need to paste requested tag from issue; all subsequent imports you can select the tag
     - Close window when done
1. Repeat above step for all records in both views 
1. Navigate to new tab with **Outreach** open
1. Click to `Prospects` and clear all default filters
1. In left side menu, navigate to `Tags` and select the appropriate tag for that list
1. Copy the **Outreach** URL and paste into the List Import issue.  
1. Repeat steps above for each list in the issue. -->

### About Long-term Lead Data Storage

Included on the `event-list-upload` issue template is the `Lead Data: Active` scoped label. This label will be used as of July 2020 to track leads' personal data that we have stored in G Drive, likely from the aforementioned list imports. After a soon-to-be-determined amount of time, MktgOps will be required to find the lead data and remove it from G Drive. Once the data has been removed from G Drive, the scoped label will be changed to the `Lead Data: Inactive` label to signal that lead data now lives in Salesforce only. During the transition period, MktgOps will need to proactively add the `Lead Data: Active` label to list import issues where it does not appear.

### Trusted vs Non-Trusted Imports
In Marketo there is a an option to choose trusted or non-trusted sources. Non-trusted sources are for list uploads that we are not confident in the data points given to us. For example, if we are loading a list with inferred country data from IP, we do not want it to overwrite our current location data that is more accurate. Blocking updates allows for a field to be updated if blank, but will not overwrite a field that already has a value.

Here is the list of fields that are blocked during a non-trusted import. If you would like to add more fields, please file an issue with the mops team.
- Country
- City
- State
- Postal Code