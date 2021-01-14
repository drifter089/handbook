---
layout: handbook-page-toc
title: Support Engineer Resources
description: If you want to learn more about what support engineers do and how they do it, this is the place.
---

### A Day in the life of a Support Engineer

As a Support Engineer at GitLab, the majority of your time will be focused on helping customers solve problems. This happens mostly through tickets, but can also happen through issues, screensharing calls, and emergencies.

### Getting Help

Working through various customer problems you may need help. We have a wide and talented team that can help you at many levels:

- Managers: If your problem is related to process, or understanding direction, or cross-team collaboration, consider talking to your direct manager, or another manager whom may be working more directly on that problem. Managers in Support Engineering should be able to point you in the right direction and enable you to find the right help.
- Senior/Staff Support engineers: If your problem is debugging related, consider reaching out to a Senior+ Engineer. At the Senior+ level, engineers are expected to be acting as mentors,teachers, and techincal experts. See our [Mentoring page for more information about how Senior+ Engineers are expected to help](/handbook/support/engineering/mentorship)

### Zendesk Instances
At GitLab, the Support Team currently manages 2 different [Zendesk Instances](/handbook/support/workflows/zendesk-instances.html):

- GitLab Support Instance:  [gitlab.zendesk.com](https://gitlab.zendesk.com)
- GitLab US Federal Support Instance: [gitlab-federal-support.zendesk.com](https://gitlab-federal-support.zendesk.com)

The customer URL for the Federal Support Instance is [federal-support.gitlab.com](https://federal-support.gitlab.com) which is a CNAME for [gitlab-federal-support.zendesk.com](https://gitlab-federal-support.zendesk.com)

All our Support Engineers have access to the GitLab Support Instance, whereas only Support Engineers who are US Citizens inside of the US have access to the GitLab US Federal Support Instance.

### Ticketing Style Guide
A collection of best practices and suggestions for [styling and responding to Zendesk tickets](/handbook/support/workflows/how-to-respond-to-tickets.html).

### What if I Feel Threatened or Harassed While Handling a Support Request?
Just as Support Team are expected to adhere to GitLab's [Code of Conduct](/handbook/people-group/code-of-conduct), we also expect customers to treat the Support Team with the same level of respect. The [GitLab Community Code of Conduct](https://about.gitlab.com/community/contribute/code-of-conduct/) outlines the standards to which we hold the wider GitLab Community.

If you notice a threatening or hostile ticket, please tag the [Manager On-Call](/handbook/support/on-call/#manager-on-call) to respond with the following guidelines in our [Statement of Support](/support/#please-dont-use-language-intended-to-threaten-or-harass).

### Support Team Contributions

We encourage all engineers to contribute to the product to help improve the customer experience directly. When working on merge requests (on the gitlab-org group) for code or for documentation, apply the
`Support Team Contributions` label so that we can track product contributions by support team
members.

Additionally, if the code change is specifically to improve the team's efficiency
(such as changes to admin for faster support), then add the `~"Support Efficiency"` label.

An issue is created in the `support-team-meta` issue tracker at the
end of each week with a list of support team contributions merged in the past week. View the
[list of summary issues here](https://gitlab.com/gitlab-com/support/support-team-meta/issues?label_name%5B%5D=Support%20Team%20Contributions).


### Internal tools

- [Support Toolbox](https://gitlab.com/gitlab-com/support/toolbox) - Includes tools such as `json_stats` (analyze JSON logs), `strace_parser` (analyze `strace` output), `gitlabsos` (get all logs and other data from customers), etc.
- [Dev Resources](https://gitlab.com/gitlab-com/dev-resources) - Create a test instance
- [GitLab Development Kit](https://gitlab.com/gitlab-org/gitlab-development-kit)
- [LicenseDot](https://license.gitlab.com/) - Details of all licenses
- [CustomersDot admin](https://customers.gitlab.com/admins)
- [GitLab Regressions](https://regressions.gitlab.io/)

### External tools

- [ExplainShell](https://explainshell.com/) - Break down a terminal command

### Useful Browser Extensions

- Copy As Markdown - Used to copy the element in current page as markdown format ([Chrome](https://chrome.google.com/webstore/detail/copy-as-markdown/dgoenpnkphkichnohepecnmpmihnabdg?hl=en)/[Firefox](https://addons.mozilla.org/en-US/firefox/addon/copy-as-markdown/))
- Zendesk Download Router - Automatically routes Zendesk downloads into separate folders by ticket number ([Chrome](https://chrome.google.com/webstore/detail/zendesk-download-router/pgfhacdbkdeppdjgighdeejjfneifkml)/[Firefox](https://addons.mozilla.org/en-GB/firefox/addon/zendesk-download-router/)/[Opera](https://addons.opera.com/en-gb/extensions/details/zendesk-download-router/))
- GitLab Web Debugger - Aides in identifying the root cause of page load errors on GitLab.com and internal GitLab instances ([Chrome](https://gitlab.com/gitlab-com/gl-infra/gitlab-web-debugger))
- Zendesk Quicktab - Opens Zendesk tickets in a single browser tab ([Chrome](https://chrome.google.com/webstore/detail/zendesk-quicktab/imgmkpifcfhbfdklogcpdnkohifklebb))
  - Note: Zendesk Quicktab was [removed from the Chrome marketplace in July 2020](https://support.tymeshift.com/hc/en-us/articles/360003993613-Install-Zendesk-Quicktab-Chrome-Extension) while ownership of the extension was in negiations. Please read the [Zendesk support forum thread](https://support.zendesk.com/hc/en-us/community/posts/360001108948/comments/360012160754) for information on the current state of the extension and installing Zendesk Quicktab from the GitHub project.
- Calendly Meeting Scheduling Software - ad-hoc meetings, one-click booking ([Chrome](https://chrome.google.com/webstore/detail/calendly-meeting-scheduli/cbhilkcodigmigfbnphipnnmamjfkipp))
- GitLab Screenshare mode - allows to hide confidential information on your GitLab screen ([Chrome](https://gitlab.com/leipert-projects/gitlab-screenshare-mode#chrome)/[Firefox](https://gitlab.com/leipert-projects/gitlab-screenshare-mode#firefox))
