---
layout: handbook-page-toc
title: "GitLab with Git Basics Hands On Guide- Lab 3"
description: "This Hands On Guide Lab is designed to walk you through the lab exercises used in the GitLab with Git Basics course."
---
# GitLab with Git Basics Hands On Guide- Lab 3
{:.no_toc}

## LAB 3- USING GITLAB ISSUES TO PUSH CODE

### Create a new Project and Issue
1. Click the **New Project** button and name your project: ***Second Project***.  
2. Under Visibility Level, click the radio button for **Private**.  
3. Click **Initialize repository with a README** checkbox and then click the green **Create project** button.  
4. On the left-hand side of the screen, locate the **Issue** section on the taskbar and click on it.  
5. Click the green **New Issue** button.  
6. In the title field type, “***new issue***”.  Optionally, you can enter a comment in the Description dialog box.  
7. In the Assignee field, click the link for **Assign to me**. 
8. Click the **Submit** button to create the issue. 

### Create a Merge Request
1. On the bottom of the issue, click on the green **Create merge request** button. Note: this will create a new branch from the master branch using the default name of the issue. 
2. Click the **drop down arrow** to view that you can customize the branch name it will create, for this exercise, leave it at the default.  
3. Click the **Create** **merge request** button.

### Edit Files Inline on a Branch
1. On the Merge Request, click the **Open in Web IDE** button.
2. On the left-hand navigation pane, click on **README.md.** 
3. In the editor, on line 5 type, “***Edit my README.md file***” 
4. Click the blue **Commit** button on the bottom of the screen. 
5. In the commit message box, type “***Updated the README.md file***” and then click the **Commit** button. 

### Verify Changes in a Merge Request
1. On the very bottom of your browser window, locate the merge request message and the small exclamation point- Click on the blue hyperlinked number to open the request.
2. On the Merge Request window- locate the Assignee section in the upper right-hand corner. Ensure the Merge Request is assigned to yourself. 
3. On your Merge Request, click on the **Changes** tab directly below the Merge Request title.  
4. Click on **Changes** 
5. Hover over the left side of any line and a comment icon will appear. Hover over line 3 and click the **comment** icon. 
6. In the comment field type, “this code xyz will fix this!” and click the **Start a review** button. Then click the **Submit Review** button.
7. To mark that the comment has been looked at and the code adjusted, click the **Resolve Thread** icon to close the review.  

### Approve the Merge Request
1. To mark the Merge Request ready, click the **Mark as ready** button in the upper right hand corner.  
2. Click the **Overview** tab on the Merge Request.  
3. Click the **Merge** button and ensure the Delete source branch checkbox is enabled. 
4. If there were eligible approvers, the approval button would be in the View Eligible Approvers section.  

### SUGGESTIONS?

If you wish to make a change to our Hands on Guide for GitLab with Git Basics- please submit your changes via Merge Request!
