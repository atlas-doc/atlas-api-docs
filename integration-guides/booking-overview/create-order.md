---
description: Create bookings with passenger, contact, and ancillary data.
---

# Create Order

{% include "../../.gitbook/includes/eva-help-hint.md" %}

Use this page to place the booking after verification.

{% hint style="info" %}
Before calling `order.do`, read `bookingRequirement` from the verify response.

Use it to decide which passenger and document fields are required for this booking.
{% endhint %}

### Main API

* `order.do`

### Inputs

* `sessionId` from verify
* `bookingRequirement` from verify
* Passenger details
* Contact details
* Ancillary selections when needed

### Key outputs

* `orderNo`
* Initial booking status
* Airline and pricing details tied to the order

### Use this when you need

* Standard order creation
* FR order creation before commit
* Booking with ancillaries

### Related pages

* [Verify](verify.md)
* [Payment & Ticketing](../../readme/booking-overview/payment-and-ticketing/)
* [Booking APIs](../../api-reference/booking-apis/)

### Full API reference

See endpoint-level details here:

* [Create Order](../../api-reference/booking-apis/create-order.md)
