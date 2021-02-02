---
layout: handbook-page-toc
title: Billing, invoice and payments requests
category: General
description: Billing and invoicing requests require action from our Billing/Accounts Receivable team.
---

- TOC
{:toc .hidden-md .hidden-lg}

## Overview

Billing and invoicing requests require action from our Billing/Accounts
Receivable team.

The following information is helpful to provide to the AR team when transfering
tickets, but not required.

1. Subscription #
1. Subscription information - copy & paste from `Manage Purchases` in
   [CustomersDot](https://customers.gitlab.com/customers/sign_in)
1. Zuora ID - available in the [CustomersDot](https://customers.gitlab.com/customers/sign_in)
   under the `Edit` tab
1. Salesforce Account ID - available in the [CustomersDot](https://customers.gitlab.com/customers/sign_in)
   under the `Edit` tab

## Billing

### Zuora contact change

When a customer wants to change the contact for current and future purchases.

> **Note:** *Billing doesn't have a vetting process, so we need to vet the
customer as far as possible before passing the request*

1. Verify that they are associated with the account / authorised to make the
   request, by checking the following:
   - if they are a contact in SFDC
   - if their domain name matches the company/previous contact
   - getting permission from the old contact
   - checking if they are the owner of the group (for a SaaS subscription)
   - checking if they have access to the instance (via a screenshot)
   - checking if they have access to the account by asking for an invoice
1. Use the `Support::L&R::Zuora Contact Change` macro to transfer the ticket to AR to
   update the bill to and sold to contact in Zuora

Support will still generate a manual license if new contact wants an updated
license. Zuora update is primarily effective for future purchases.

NOTE: The `Sold to` contact in Zuora usually receives the license, renewal reminders and comms about changes to the subscription (e.g renewal success/fail). The `Bill to` contact in Zuora will receive invoices as well as renewal reminders.

### Billing processes to know about

#### Zuora entity change

When billing processes an [entity change](https://gitlab.com/gitlab-com/Finance-Division/finance/-/wikis/Process-for-change-of-entity),
billing creates a second Zuora account for the customer, with a different entity
than the original.

When an entity change happens at renewal, it can impact how licenses are
generated. If you are troubleshooting a license issue, check Zuora to see if
there are 2 accounts with different entities to confirm if an entity change took
place.

The issue that we will see more often is the renewal license not generated with
previous users or trueups. In the event of the license being impacted by the
entity change, we can assist with a manual license.

## Cancellations, Downgrades, and Refunds

### Cancellations

When a customer wishes to cancel their subscription and they are not interested
in waiting until the subscription expires.

1. Make sure that there aren't any other types of queries that would need the
   Support team's attention
1. Use the `General::Accounts Receivable` macro to transfer the ticket to AR to
   process the cancellation. They will reply to the customer once done and issue
   a refund if applicable.

### Downgrades

There is currently [no ability to downgrade a subscription from a self-service perspective](https://gitlab.com/gitlab-org/customers-gitlab-com/issues/368).

If a user wants to downgrade and they are within 45 days of the purchase, send
the request to the AR team by selecting the form `Accounts Receivable` in
Zendesk and advise the user to purchase the desired plan once cancelled/refunded.

If the user is outside of the 45 day period, advise them that we can cancel the
purchase but the subscription will not be refunded. In this case you can also
consider passing the issue to the assigned Account Manager in sales if the deal
is midmarket or higher.

### Refunds

When a customer wants a refund and their purchase is [eligible for a refund](/terms/)
(within the 45 day refund period).

> **Note:** *There may be special circumstances where we may be able to request
a refund outside of the eligibility window - if you believe a case qualifies for
this, CC a manager for approval.*

1. Determine the reason that they're cancelling and requesting a refund.
1. Make sure that there aren't any other types of queries that would need the
   Support team's attention
1. Use the `General::Accounts Receivable` macro to transfer the ticket to AR to
   process the refund. They will reply to the customer once done.

Note: we cannot do partial refunds, so when a refund is requested, the whole
subscription will have to be cancelled and refunded. See `Renewal reversal` for
accidental renewal scenarios.

## Invoice

### Request copy of invoice

Check first if the invoice is available in [CustomersDot](https://customers.gitlab.com/customers/sign_in).

* If yes: walk the customer through locating the invoices under Payment History for future self-service ability.
* If no: Use the `General::Accounts Receivable` macro to transfer the ticket to AR to
  process the request. They will reply to the customer once done.

### Invoice modification

When a customer wishes to modify their invoice for tax or administration purposes.

1. Verify that the invoice exists in the system
1. Make sure that there aren't any other types of queries that would need the
   Support team's attention
1. Use the `General::Accounts Receivable` macro to transfer the ticket to AR to
   process the request. They will reply to the customer once done.

## Payments

### Requests to make a payment/payment failed

Use the `General::Accounts Receivable` macro to transfer the ticket to AR to
process the request. They will reply to the customer once done.

### Credit card removal

When a customer wishes to remove their credit card from their CustomersDot
account.

1. Make sure that there aren't any other types of queries that would need the
   Support team's attention.
1. Use the `General::Accounts Receivable` macro to transfer the ticket to AR to
   process the request. They will reply to the customer once done.


### Renewal reversal

When a customer has accidentally renewed twice or mistakenly.

1. Determine the reason that the renewal has to be reversed
1. Use the `General::Accounts Receivable` macro to transfer the ticket to AR,
   they will reverse the renewal so that the subscription is in the same state
   as before the renewal and refund the renewal if applicable

### Requests for split payments

When a customer has a payment limit on their card, preventing a single payment for the full amount of their purchase, Billing is able to charge the card in "batches".

1. Get information on the limit and the total cost of the purchase the customer wishes to make.
1. Use the `General::Accounts Receivable` macro to transfer the ticket to AR to
   process the request. They will reply to the customer once done.

Note that in some cases, the total amount is too large to charge in 2 batches and Billing might request that a sales-assisted order is done instead. If you're unsure whether this would be the case, you can tag [at]Billing-ops in Chatter on the Account or Opportunity in SFDC to double-check with them.
