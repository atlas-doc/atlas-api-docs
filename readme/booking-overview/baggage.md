---
description: >-
  Atlas API baggage flow for luggage lookup, baggage quotes, and
  conversion-focused booking decisions.
---

# Baggage

{% include "../../.gitbook/includes/eva-help-hint.md" %}

Use this page to build baggage selection into the booking flow.

Start here when you need to:

* show baggage options before booking
* get exact baggage quotes for the current itinerary
* add baggage choice to the booking experience

### FAQ

#### When should I call `getLuggage.do`?

Call `getLuggage.do` as a recommended step before payment.

Baggage display helps reduce hesitation and improve conversion.

Call it after `verify.do` or `getOffers.do`.

#### Which identifier should I use?

Send `offerId` in `getLuggage.do`.

Use `sessionId` from `verify.do` as `offerId`.

Use `OfferId` from `getOffers.do` directly.

### Main API

* `getLuggage.do`

### What should you check first?

Confirm that the airline supports baggage upsell for the current flow.

Confirm that the current verify or offer context is still valid.

Confirm that the returned baggage products still match the itinerary you plan to book.

### What does `getLuggage.do` return?

It returns baggage products for the current itinerary.

Each product has its own `productCode`.

Use that `productCode` in `order.do` when baggage is selected.

### Use this when you need

* Baggage option lookup
* Exact baggage pricing before booking
* Baggage upsell mapping for `order.do`

### Best practice

Choose the itinerary first.

Then query baggage as a recommended conversion step before payment.

Clear baggage pricing helps improve traveler confidence and attachment rate.

Keep baggage mapping consistent across the current booking context before `order.do`.

For connecting flights, keep the baggage selection consistent across connected segments in the same direction.

### Notes

* Availability depends on airline support
* Baggage rules vary by carrier
* Use the current verify or offer context for accurate pricing

### What comes next?

Use [Create Order](../../integration-guides/booking-overview/create-order.md) to send the selected baggage `productCode` when required.

If seat selection is also needed, use [Seats](../../integration-guides/booking-overview/seats-and-baggage.md).

### Related pages

* [Verify](../../integration-guides/booking-overview/verify.md)
* [Get Offer](../../integration-guides/booking-overview/get-offer.md)
* [Create Order](../../integration-guides/booking-overview/create-order.md)
* [Post-ticketing Ancillaries](../../integration-guides/post-booking-overview/post-booking-operations/post-ticketing-ancillaries.md)

### Full API reference

See the complete endpoint schemas and samples here:

[Baggage](../../api-reference/booking-apis/baggage.md)
