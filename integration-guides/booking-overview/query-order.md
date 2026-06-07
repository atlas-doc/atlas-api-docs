---
description: >-
  Atlas API order query flow for booking status, ticketing progress, airline
  PNR, and final order follow-up.
---

# Query Order

{% include "../../.gitbook/includes/eva-help-hint.md" %}

Use this page to check the latest booking state.

Start here when you need to:

* track ticketing after `pay.do`
* confirm whether an order is already paid or ticketed
* read airline PNR and ticket details after fulfillment

### FAQ

#### When should I call `queryOrderDetails.do`?

Call it after `order.do` or `pay.do` when you need the latest order state.

Use it as the main follow-up API until the booking reaches the final state.

#### What should I check in the order query response?

Check `orderStatus`, `ticketStatus`, airline PNR details, and ticket numbers.

Use these fields to confirm whether ticketing is still in progress or already complete.

### Main API

* `queryOrderDetails.do`

### Use this when you need

* Poll ticketing progress
* Retrieve booking and passenger details
* Confirm airline PNR and final status

### Common checks

* `orderStatus`
* `ticketStatus`
* Airline PNR details
* Ancillary and fare data

### What does order query help you decide?

Use it to decide:

* whether payment should be retried or not
* whether ticketing is still processing
* whether airline PNR and ticket numbers are already available
* whether post-booking actions can start

### Best practice

Use `queryOrderDetails.do` as the main status source after payment.

Webhook can help, but it should not be your only confirmation path.

If payment may already be in progress or completed, query the order before any retry.

### Related pages

* [Payment & Ticketing](../../readme/booking-overview/payment-and-ticketing/)
* [Post-ticketing Ancillaries](../post-booking-overview/post-booking-operations/post-ticketing-ancillaries.md)
* [Webhook Overview](../webhook-overview/)
* [Booking APIs](../../api-reference/booking-apis/)

### Full API reference

See endpoint-level details here:

* [Query Order](../../api-reference/booking-apis/query-order.md)
