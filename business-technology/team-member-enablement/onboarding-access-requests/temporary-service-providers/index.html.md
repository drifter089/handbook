---
layout: handbook-page-toc
title: "Temporary Service Providers Access Requests, Onboarding and Offboarding"
---

## On this page
{:.no_toc .hidden-md .hidden-lg}

- TOC
{:toc .hidden-md .hidden-lg}

Similar to our Access Request process for team members, we have an access request process for consultants or professional services providers. We track issues related to consultants/professional service providers in the [Temporary Service Providers group](https://gitlab.com/gitlab-com/temporary-service-providers). Temporary Service Providers need to go through the [Professional Services Procurement process](https://about.gitlab.com/handbook/finance/procurement/vendor-contract-professional-services/) before they can be onboarded.

## Access Requests and Orientation issues

If the vendor requires access to systems to complete work, the vendor manager (ie. the GitLab team member who will manage the relationship with the temporary service provider, generally a people manager) is responsible for creation of a Vendor Access Request and Orientation issue.

   * **Access Request**: These issues aren't created in the same location as access requests for team members. Please use the following link to create an AR using the [access request template](https://gitlab.com/gitlab-com/contingent-workers/lifecycle/-/issues/new?issuable_template=access-request) and assign it to yourself and the relevant [provisioner(s)](https://gitlab.com/gitlab-com/www-gitlab-com/-/blob/master/data/tech_stack.yml) for the tools that the professional services provider requires access to. The AR should include [**only systems that are necessary**](/handbook/engineering/security/access-management-policy.html#access-management) to the work that the vendor will be performing.

   * **Orientation Issue**: To support the service provider through the set up of the most common tools used at GitLab, an **[orientation issue](https://gitlab.com/gitlab-com/contingent-workers/lifecycle/-/issues/new?issuable_template=orientation-issue) must be created**. Assign to yourself and the professional services provider if they have a GitLab account with the required access.

### Access Request deep dive

Please read instructions on how to request access to the following applications (managed by IT):

- **GitLab:** Temporary Service Providers can follow [the instructions on how to get started with GitLab](https://about.gitlab.com/get-started/) to create a GitLab account. From there, the manager can include their username information in their access request along with the minimum groups/projects they need to complete job duties.
- **GSuite/Google Workspace**: Google Workspace access (including a @gitlab.com email address) will not be provided unless there are reasons why Temporary Service Providers would require it. Documents and shared drives within G Suite/Google Workspace can be shared outside of GitLab so a @gitlab.com email address isn't required for that purpose. Situations where we would provide access are:

    - Temporary Service Providers are _required_ to send emails from a @gitlab.com email (justification on why it is required needs to be provided)
    - Temporary Service Providers require access to a system that can only be accessed with Google OAuth (such as Kibana)
    - Temporary Service Providers require access to Infrastructure systems via Google Identity-Aware Proxy (IAP) and GCP access.
    - Temporary Service Providers will handle sensitive data (i.e. RED or ORANGE data as defined by GitLab's [Data Classification Standard](https://about.gitlab.com/handbook/engineering/security/data-classification-standard.html))

- **Okta**: Access to Okta can be provisioned depending on the systems they require access to and whether those systems can only be accessed using Okta.
- **1Password**: More details on 1password access coming soon.
- **Slack:** Single or multi channel guest access only, unless there is a situation where this wouldn't work. Inefficiency in adding people to many channels isn't a good enough justification as we are risking providing access to confidential topics being discussed in Slack to non-GitLab team members.
- **Zoom:** Temporary service providers can create a Zoom account with their personal/work email (Non GitLab) and be invited to any meetings. No need to provide a Zoom account unless there is a situation where this wouldn't work.

### Offboarding

- Managers of Temporary Service Providers will be need to be sure to open an offboarding issue in order to ensure Access Removal. 
- Should the Temporary Service Provider become a Team Member, an offboarding issue will need to be completed at least one business day before their start date in order to ensure they have updated permissions and access.

