---
layout: handbook-page-toc
title: CustomerDot Account Related Problems
category: CustomersDot
description: Using the customer console for internal requests is only for special cases where the existing tools won't allow us to complete the task at hand.
---

## On this page
{:.no_toc .hidden-md .hidden-lg}

- TOC
{:toc .hidden-md .hidden-lg}


## Overview

Sometime customers would have trouble accessing their account. This page would help you troubleshoot the problem.

### Customer cannot sign in even after password reset

This could be due to the following reasons:

#### 1. The subscription was purchased through reseller

This can be identified through the CustomerDot account edit page, the account would have `Login activated` unchecked.

Customers purchasing through reseller would not have access to their [customers portal](https://customers.gitlab.com/customers/sign_in) account. Future adjustment must be done through reseller.

#### 2. Password reset email was requested from https://gitlab.com

It's possible that customer request password reset email from https://gitlab.com/users/password/new.
We can confirm this by searching through the mailgun log. To locate the password reset email:

1. You can find the mailgun log in credential in 1password for support team.
1. On the left panel, expand `Sending` and go to `Logs`
1. On the top left, click the `Domain` dropdown and choose `customers.gitlab.com` and enter the customer email to search for recent email. You can also search in `mg.gitlab.com` domain to confirm whether the password reset email was requested on GitLab.com or on customers.gitlab.com
1. If no password reset was sent, we can issue a password reset email or ask the customer to request a password reset email from https://customers.gitlab.com/customers/password/new

#### 3. The CusotmerDot account has not been confirmed

When the account is not confirmed, the customer cannot log in. To view whether an account is confirmed:

1. Sign into CustomerDot with your admin account
1. Find the customer account
1. Click on the `i` icon on the customer account or `Show` if you're already viewing the account
1. The confirmation is shown in `Confirmed at` field

If the customer has not confirmed their email. We can resend the confirmation email from https://customers.gitlab.com/customers/confirmation/new and get back to the customer.

