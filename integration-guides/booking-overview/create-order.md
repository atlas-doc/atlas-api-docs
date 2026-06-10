---
description: >-
  Atlas API order creation flow for passenger, contact, ancillary, and booking
  requirement handling.
---

# Create Order

{% include "../../.gitbook/includes/eva-help-hint.md" %}

Use this page to place the booking after verification.

{% hint style="info" %}
Before calling `order.do`, read `bookingRequirement` from the verify response.

Use it to decide which passenger and document fields are required for this booking.
{% endhint %}

Start here when you need to:

* create the booking after verify
* build the request from `sessionId` and `bookingRequirement`
* capture the `orderNo` for payment and follow-up

### FAQ

#### What do I need before `order.do`?

You need a fresh `sessionId` from verify, the current `bookingRequirement`, passenger details, contact details, and ancillary selections when required.

Use the `sessionId` within 2 hours after `verify.do`.

If seat selection is included, decide the seat fulfillment handling mode before `order.do`.

#### What should I keep after `order.do`?

Keep the returned `orderNo`.

Use it for payment, order query, and later follow-up.

### Main API

* `order.do`

### Inputs

* `sessionId` from verify, valid for up to 2 hours
* `bookingRequirement` from verify
* Passenger details
* Contact details
* Ancillary selections when needed
* Seat fulfillment handling mode when seat selection is included

### Key outputs

* `orderNo`
* Initial booking status
* Airline and pricing details tied to the order

### Common build rules

Use `bookingRequirement` to decide which passenger and document fields are mandatory.

Keep ancillary mapping consistent with the current verify response.

Do not use a `sessionId` older than 2 hours.

Do not build the order from stale verify data.

If seat selection is included, pass the seat fulfillment handling mode in the order request.

Use the same order request to define how Atlas should handle seat fulfillment failure.

Supported modes:

* `STOP_TICKET` — stop ticket issuance, cancel the whole order, and refund it
* `STOP_SEAT` — issue the ticket, remove the seat, and refund the seat amount
* `SIMILAR_SEAT` — issue the ticket with a similar seat selected by operations

For deposit customers, `STOP_SEAT` may require a split fund order and a `credit note`.

### Use this when you need

* Standard order creation
* FR order creation before commit
* Booking with ancillaries

### What comes next?

#### Standard payment path

Continue to [Payment & Ticketing](../../readme/booking-overview/payment-and-ticketing/) with `orderNo`.

#### FR flow

If the airline is FR, complete [Confirm Order](confirm-order.md) before payment.

### Related pages

* [Verify](verify.md)
* [Payment & Ticketing](../../readme/booking-overview/payment-and-ticketing/)
* [Booking APIs](../../api-reference/booking-apis/)

### Full API reference

See endpoint-level details here:

* [Create Order](../../api-reference/booking-apis/create-order.md)
