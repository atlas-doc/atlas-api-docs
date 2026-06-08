---
description: >-
  Atlas API seat and baggage flow for seat availability, luggage lookup, and
  ancillary decisions before booking.
---

# Seats & Baggage

{% include "../../.gitbook/includes/eva-help-hint.md" %}

Use this page when seat or baggage selection is needed.

Start here when you need to:

* check baggage options before booking
* query seat availability when seat choice matters
* decide whether ancillaries belong in the base booking flow

### Service scope

Atlas supports seat selection for these scenarios:

* airlines that support Atlas API seat capability
* Atlas-issued orders
* seat selection purchased with the ticket in the booking flow

Atlas does not support seat selection for these scenarios:

* non-Atlas-issued orders
* post-ticketing seat selection

A non-Atlas-issued order is ticketed by another party.

In this case, Atlas is only used to add seat service after ticketing.

### FAQ

#### When should I query baggage or seat data?

Query baggage or seat data only when it affects the booking decision.

Do not add ancillary calls to every booking flow by default.

#### Which APIs are used for inflow ancillaries?

Use `getLuggage.do` for baggage options.

Use `seatAvailability.do` for seat availability and seat-selection support.

### Main APIs

* `seatAvailability.do`
* `getLuggage.do`

### What should you confirm first?

Confirm that the airline supports the required ancillary flow.

Confirm that the current session or offer context is still valid for the ancillary request.

### Use this when you need

* Seat map and seat selection support
* Baggage option lookup
* Ancillary decisions before payment

### Best practice

Choose the itinerary first.

Then query baggage or seats only when those choices affect conversion, policy, or traveler experience.

Keep ancillary mapping consistent with the current booking context before `order.do`.

### Notes

* Availability depends on airline support
* Session validity matters for seat queries
* Baggage and seat rules may vary by carrier

### What comes next?

Use [Create Order](create-order.md) to send the selected ancillary data with the booking when required.

### Related pages

* [Verify](verify.md)
* [Create Order](create-order.md)
* [Post-ticketing Ancillaries](../post-booking-overview/post-booking-operations/post-ticketing-ancillaries.md)

### Full API reference

See the complete endpoint schemas and samples here:

[Inflow Seat & Baggage](../../api-reference/booking-apis/inflow-seat-and-baggage.md)
