---
layout: markdown_page
title: "Token Management Working Group"
description: "The charter of this working group is to drive improvements for token management."
canonical_path: "/company/team/structure/working-groups/token-management/"
---

## On this page
{:.no_toc}

- TOC
{:toc}

## Attributes

| Property        | Value           |
|-----------------|-----------------|
| Date Created    | August 16, 2022   |
| Date Ended      | TBD  |
| Slack           | [#wg_token]() (only accessible from within the company) |
| Google Doc      | [Token Management Working Group Agenda](https://docs.google.com/document/d/17X-P9vnKDa6WZ6m-0Hxf5aIFkEhmArUN069GgQ-6Dss/edit) (only accessible from within the company) |

## Direction

Out of due diligence and responsibility to GitLab users, the Token Management Working Group will
work towards building a foundation and path forward for future token management security
enhancements. This will be accomplished through the creation and publication of a token management
security policy and proposed fixes for the high risk and low effort token management issues. With
this, the Token Management Working Group will set up the fast follow on mid to long term token
management security enhancement effort for success. For additional detail please visit our 
[Token Leaks internal handbook page](https://internal-handbook.gitlab.io/handbook/engineering/security/token-leaks/).
All the tokens will be stored in GitLab the application as we ship it to users and customers. By
dogfooding these enhancements and making improvements to meet our own security needs, we will
improve token management and protection of secrets for all users, becoming better stewards of our
user's secrets. 

## Exit Criteria

The Token Management Working Group will deliver:
* Publish the first iteration of an official token and secrets management policy that is based on the [Token Standard](https://gitlab.com/gitlab-com/gl-security/security-research/cryptographic-standards/-/blob/main/token-standard.md) previously created
    * Status: Complete
    * Results: [GitLab Token Management Standard](https://about.gitlab.com/handbook/security/token-management-standard.html)
* Proposed fixes, with risk assessments, for each identified low effort high risk item
    * Status: On track with no blockers or risks
* Propose possible out-of-product workaround mitigations for the top 2 high effort high risk items
    * Status: On track with no blockers or risks

## Roles and Responsibilities

| Working Group Role              | Person                | Title                                                        |
|---------------------------------|-----------------------|--------------------------------------------------------------|
| Facilitator                     | James Ritchey        |  Sr. Security Engineering Manager |
| Executive Stakeholder | Laurence Bierner          | Director Security Engineering                         |
| Member         | Joaquin Fuentes   | Director Security Operations           |
| Member         | Valentine Mairet   | SIRT Manager           |
| Member         | Philippe Lafoucrière    | Security Architect           |
| Member         | Andrew Kelly    | AppSec Manager            |
| Member         | Chris Moberly   | Red Team Manager          |
| Member         | Connor Gilbert  | Sr. Product Manager, Secure:Static Analysis |
| Member         | Grzegorz Bizon  | Principal Engineer, Ops   |
| Member         | Stan Hu         | Engineering Fellow        |
| Member         | Michelle Gill   | Senior Engineering Manager, Manage |
| Member         | Hannah Sutor    | Senior Product Manager, Manage:Auth |
| Member         | Alex Hanselka   | Senior Site Reliability Engineer |
| Member         | Dominic Couture | Staff Security Engineer, Application Security |
| Member         | Thomas Woodham  | Senior Engineering Manager, Secure |
| Member         | Amar Patel      | Engineering Manager, Secure:Static Analysis |
| Member         | Zach Rice       | Senior Backend Engineer, Secure:Static Analysis |
| Member         | Lucas Charles   | Staff Backend Engineer, Secure:Static Analysis |
| Member         | Dennis Appelt   | Staff Security Engineer, Security Research |
| Member         | Mark Loveless   | Staff Security Engineer, Security Research |
