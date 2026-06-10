---
description: >-
  Atlas API booking flow overview for search, verify, order creation, payment,
  ticketing, and order follow-up.
---

# Booking Overview

{% include "../../.gitbook/includes/eva-help-hint.md" %}

Use this section for the end-to-end booking flow.

<figure><img src="../../.gitbook/assets/FlowChart_2_IssueTicket.png" alt=""><figcaption><p>Booking flow from search to payment and follow-up</p></figcaption></figure>

Start here when you need to:

* understand the standard Atlas API booking flow
* choose between `search.do` and `getOffers.do`
* see which identifier to keep at each step

### FAQ

#### What is the standard Atlas API booking flow?

The standard flow is `search.do` → `verify.do` → `order.do` → `pay.do` → `queryOrderDetails.do`.

If the airline is FR, add `orderCommit.do` before payment.

#### When should I use `getOffers.do` instead of `search.do`?

Use `search.do` when Atlas is your main shopping entry point.

Use `getOffers.do` when you already know the target itinerary or need an independent price check.

### Pages in this section

* [Search](search.md)
* [Get Offer](get-offer.md)
* [Verify](verify.md)
* [Create Order](create-order.md)
* [Confirm Order](confirm-order.md)
* [Payment & Ticketing](../../readme/booking-overview/payment-and-ticketing/)
* [Query Order](query-order.md)
* [Seats](seats-and-baggage.md)
* [Baggage](../../readme/booking-overview/baggage.md)

### Key identifiers in the booking flow

Keep and reuse the right identifier at each stage:

* `routingIdentifier` from `search.do`
* `sessionId` from `verify.do`
* `orderNo` from `order.do`
* airline PNR and `ticketNos` from `queryOrderDetails.do` after ticketing

For the Get Offer path, keep `OfferId` from `getOffers.do`.

For seat queries, keep `sessionId` from `verify.do` or `OfferId` from `getOffers.do`.

### What this section covers

* Search for flight offers
* Retrieve offers through an independent Get Offer flow
* Verify fares and routing
* Create orders
* Confirm FR orders when required
* Pay and issue tickets
* Retrieve booking details
* Run advanced search flows
* Query seats
* Query baggage

### Which flow should you choose?

#### Standard search flow

Use this when Atlas is your main shopping and booking layer.

This path uses `search.do` first, then `verify.do` before booking.

#### Get Offer flow

Use this when the itinerary is already known or when you need an independent price check before order creation.

This path starts with `getOffers.do` and uses `OfferId`.

### Typical flow

{% stepper %}
{% step %}
### Standard search path

Search for available offers and keep the returned identifiers.
{% endstep %}

{% step %}
### Verify

Recheck fare, routing, and booking requirements before order creation.
{% endstep %}

{% step %}
### Order

Create the booking with passenger, contact, and ancillary details.
{% endstep %}

{% step %}
### Optional FR confirmation

Most airlines skip this step.

If the airline is FR, call `orderCommit.do` and wait for user confirmation before payment.
{% endstep %}

{% step %}
### Pay

Complete payment and wait for ticketing to finish.
{% endstep %}
{% endstepper %}

#### How to include seats and baggage

Recommend `getLuggage.do` and `seatAvailability.do` in the booking flow when the product supports ancillary upsell.

Use them before payment to improve traveler clarity and order conversion.

Call `seatAvailability.do` only with a valid `sessionId` or `OfferId`.

Do not call it from flight data alone.

### Alternate flow

Use this path when you already know the target itinerary or need an independent price check.

{% stepper %}
{% step %}
### Get Offer

Call `getOffers.do` and keep the returned `OfferId`.
{% endstep %}

{% step %}
### Seats and baggage

Query `getLuggage.do` and `seatAvailability.do` before booking when ancillary upsell is part of the product.

Use the returned `OfferId` for `seatAvailability.do` when seat lookup is needed in this flow.
{% endstep %}

{% step %}
### Order

Create the booking with `order.do`.
{% endstep %}

{% step %}
### Pay

Complete payment with `pay.do`.
{% endstep %}
{% endstepper %}

#### What happens after `pay.do`?

Do not assume payment and final ticketing happen at the same moment.

Use `queryOrderDetails.do` until the order reaches the final ticketed state.

Webhook can help, but it should not be your only confirmation path.

### Main APIs

* `search.do`
* `getOffers.do`
* `verify.do`
* `order.do`
* `orderCommit.do`
* `pay.do`
* `queryOrderDetails.do`
* `smartSearch.do`
* `seatAvailability.do`
* `getLuggage.do`

### Recommended next pages by task

#### Build the standard flow

Use:

* [Search](search.md)
* [Verify](verify.md)
* [Create Order](create-order.md)

#### Build payment and follow-up

Use:

* [Payment & Ticketing](../../readme/booking-overview/payment-and-ticketing/)
* [Query Order](query-order.md)

#### Build the alternate offer path

Use:

* [Get Offer](get-offer.md)
* [Seats](seats-and-baggage.md)
* [Baggage](../../readme/booking-overview/baggage.md)

### Use this when you need

* A standard search-to-ticket flow
* An independent offer lookup and price-check flow
* FR order confirmation support when applicable
* Seat and baggage upsell
* Real-time or smart search options

### Full API reference

Use endpoint-level details here:

[Booking APIs](../../api-reference/booking-apis/)

### Related pages

* [Quick Start](../quick-start/)
* [Get Sandbox Credentials](../quick-start/making-requests.md)
* [Error Codes](../../troubleshooting-and-support/errors-handing/)
