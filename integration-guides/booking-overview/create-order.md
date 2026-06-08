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

### Key outputs

* `orderNo`
* Initial booking status
* Airline and pricing details tied to the order

### Common build rules

Use `bookingRequirement` to decide which passenger and document fields are mandatory.

Keep ancillary mapping consistent with the current verify response.

Do not use a `sessionId` older than 2 hours.

Do not build the order from stale verify data.

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
