---
description: >-
  Common booking flow questions about search results, pricing, passenger count,
  and timing.
---

# Search & Booking

{% include "../../.gitbook/includes/eva-help-hint.md" %}

Use this page for search response, pricing, and booking timing questions.

### Can users switch display currency?

No.\
Pricing is returned in the agreed contractual currency.

### Why is tax breakdown missing in some search results?

Many LCCs do not provide tax split data during booking or in the PNR.\
Atlas can only expose the breakdown when the airline provides it.

### What does `TransactionFeePerPax` mean?

It is the Atlas technical service fee charged per passenger.\
It is separate from airfare and tax.\
It is non-refundable.

### Why are fields like `bookingclass` or `farebasis` missing?

Many LCCs do not return those values.\
Use `cabin` when available.\
Do not assume GDS-style fare data exists for every airline.

### How many results does search return?

Search returns all available offers by default.\
Default sorting is lowest fare first.

### When should we use `getOffers.do` instead of `search.do`?

Use `search.do` when Atlas is your main shopping entry point.\
Use `getOffers.do` when you already know the target itinerary or need an independent price check.

`getOffers.do` is a better fit for external shopping engines and final price validation flows.

### Why can search and verify return different prices?

Search may use cached data.\
Verify checks live fare and availability before order creation.

If the price changed, use the verify result as the current source of truth.\
For Get Offer flows, refresh the offer before ordering when needed.

### What does `seatCount` mean?

It is the remaining seat count for the fare.\
Atlas caps the practical maximum at 4 because larger LCC bookings fail more often.

### How long can we wait between search and verification?

Up to 2 hours is allowed.\
Shorter is better because prices may change.

### Does Atlas support fare families?

Yes.\
Enable `includeMultipleFareFamily` in search when you need fare-family results.

Availability still depends on airline support and current inventory.

### Can we filter baggage during search?

No.\
Choose the itinerary first.

Then query baggage options with `getLuggage.do` when baggage matters before booking.

### How long can we wait between verification and order?

Up to 30 minutes is allowed.\
Shorter is better because pricing and availability may change.

### Can passenger count change between search and order?

Yes, if there is still at least one adult traveler.\
But keeping the same count across search, verification, and order is safer.

Changing count after verification increases failure risk because verification checks live inventory.

### Does `getOffers.do` require `verify.do`?

Not in the standard Get Offer flow.\
That path is built around the returned `OfferId` and then continues to `order.do`.

Use the Get Offer guide and current API reference when implementing that path.

### When should we refresh a Get Offer result?

Refresh it when any booking-critical input changes.\
Examples include passenger count, target flight, expected fare, or long delays before order creation.

Avoid creating the order from stale offer assumptions.

### Related pages

* [Search](../../integration-guides/booking-overview/search.md)
* [Get Offer](../../integration-guides/booking-overview/get-offer.md)
* [Verify](../../integration-guides/booking-overview/verify.md)
* [Create Order](../../integration-guides/booking-overview/create-order.md)
