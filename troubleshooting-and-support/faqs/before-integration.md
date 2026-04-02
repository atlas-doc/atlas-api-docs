---
description: >-
  High-priority questions to settle before kickoff, development, and go-live
  planning.
---

# Before Integration

Use this page before kickoff, solution review, or integration planning.

It covers the questions teams usually need answered before development starts.

{% hint style="info" %}
Need a meeting-ready version of this page?

Use [Kickoff Checklist](kickoff-checklist.md).
{% endhint %}

### What should be decided before kickoff?

Settle these points first:

* which shopping flow you will use
* when you refresh price before booking
* which payment mode you will support
* how you will track ticketing completion
* whether baggage and seat selection are required before purchase
* who owns refund and change follow-up
* whether webhook is supplemental or central in your design

If these points stay open, kickoff usually becomes slow and repetitive.

### Quick alignment checklist

Use this checklist in the first solution review:

* Atlas is the main shopping source, or only the final pricing source
* `search.do` or `getOffers.do` is chosen for the core flow
* price refresh point is defined before `order.do`
* payment mode is defined by airline and business model
* order polling is implemented after `pay.do`
* webhook is not treated as the only source of truth
* post-booking changes are routed to ATRIP service requests
* UAT owner and evidence format are agreed

### Pricing integrity

The main risk in flight booking is stale price or stale availability.

Use these rules:

* use `verify.do` before `order.do` in the standard flow
* use `getOffers.do` when you need an independent real-time price check
* treat the latest verify or offer result as the current source of truth
* avoid long delays between pricing and booking

Do not treat search output as a final booking promise.

### How do we get sandbox credentials?

Generate them in ATRIP under `Profile` → `My Profile` → `Company Information`.

Use:

* `x-atlas-client-id`
* `x-atlas-client-secret`

Use them on every sandbox request.

See [Sandbox Access](../../integration-guides/quick-start/making-requests.md).

### Is there a Postman collection for first tests?

Yes.

Use the collection in [Quick Start](../../integration-guides/quick-start/) for first end-to-end tests.

Use the UAT collections later for validation evidence.

### Which booking flow should we use?

Use `search.do` when Atlas is your main shopping entry point.

Use `getOffers.do` when you already know the itinerary or need an independent price check.

Use `verify.do` before `order.do` in the standard search flow.

See:

* [Booking Overview](../../integration-guides/booking-overview/)
* [Get Offer](../../integration-guides/booking-overview/get-offer.md)
* [Verify](../../integration-guides/booking-overview/verify.md)

### Why can search and verify return different prices?

Search may use cached data.

Verify checks live fare and availability before order creation.

If the price changed, use the latest verify result.

### What is the safest pricing pattern?

Use this pattern when price integrity matters most:

1. search or get the target offer
2. refresh price close to booking time
3. create the order immediately
4. pay without unnecessary delay

This reduces mismatch caused by cache age, inventory drift, or airline updates.

### How long can we wait between steps?

Current guidance is:

* search → verify: up to 2 hours
* verify → order: up to 30 minutes

Shorter is safer.

### Booking status and ticketing

Ticketing is not always immediate.

Design for an async flow:

* payment can succeed before final ticketing details appear
* airline PNR can appear after the order is created
* ticket numbers are returned only after ticketing completes
* polling is required for final confirmation

Build your status handling around `queryOrderDetails.do`.

### Does Atlas support fare families?

Yes.

Enable `includeMultipleFareFamily` in search when you need fare-family results.

Support still depends on airline and inventory.

### Can we filter baggage during search?

No.

Choose the itinerary first.

Then query baggage or seat options only when they affect the booking decision.

See [Seats & Baggage](../../integration-guides/booking-overview/seats-and-baggage.md).

### Ancillaries and fare content

Confirm early whether your product needs:

* fare family display
* baggage upsell before booking
* seat map before booking
* post-ticketing baggage or seat sales

Keep ancillary queries optional unless they are critical to conversion.

### Which payment methods are supported?

The main options are:

* **Deposit**
* **VCC pass-through**

Support still depends on airline and ticketing channel.

See [Payments](atlas-api-payments.md).

### How should we choose between deposit and VCC?

Use **deposit** when you want a simpler payment path and Atlas-balance settlement.

Use **VCC pass-through** when your business needs direct airline card charging.

Still confirm support per airline and per order before building the final payment path.

### Does Atlas issue VCC cards?

No.

Atlas supports VCC pass-through only.

You provide the card details in `pay.do`.

### Do we need to poll after payment?

Yes.

Payment and ticket issuance are not always the same event.

Use `queryOrderDetails.do` until ticketing reaches the final state.

Webhook helps, but it should not be your only confirmation path.

See [Query Order](../../integration-guides/booking-overview/query-order.md).

### What should our system store for later follow-up?

Keep these values in your booking chain:

* `routingIdentifier`
* `sessionId` or `OfferId`
* `orderNo`
* `pnrCode`
* airline PNR when available
* payment method used

This makes ticketing, refund, and support follow-up much easier.

### Is `pnrCode` the airline PNR?

No.

`pnrCode` is the Atlas booking reference.

The airline PNR appears later after ticketing and can be read from order query.

### Payment and refund model

Align refund expectations before go-live.

The refund path depends on payment mode:

* VCC refunds usually return to the original card
* deposit refunds are credited back after Atlas receives airline funds

Do not present one refund path as universal.

### Where do refunds go?

For **VCC**, refunded funds usually return to the original card.

For **deposit**, Atlas credits your balance after airline funds are received.

See [Post-booking](atlas-api-post-ticketing.md).

### Are booking changes handled by API?

Not as a general self-service flow.

Use a Service Request in ATRIP for name correction, flight change, and similar requests.

### Post-booking ownership

Confirm who owns these tasks after launch:

* refund initiation
* refund follow-up
* schedule change monitoring
* urgent departure-day handling
* manual change requests

If ownership is unclear, operations issues usually surface after the first live orders.

### Are webhooks guaranteed?

No.

Webhook delivery is best effort.

Use airline email, incident flows, and order query for final reconciliation.

See [Webhook Overview](../../integration-guides/webhook-overview/).

### When should we start UAT?

Start UAT only after the sandbox flow is stable end to end.

Prepare:

* the correct UAT template
* evidence for each scenario
* webhook evidence when required
* relevant order numbers or request IDs

See [UAT Validation](../../integration-guides/quick-start/uat-submission-guide.md).

### What should be confirmed before go-live?

Confirm all of these:

* sandbox flow is stable
* UAT is approved
* production credentials are generated
* production IP whitelist is ready
* endpoints are switched correctly
* first live orders can be monitored

See [Production Go-Live](../../integration-guides/quick-start/production-go-live.md).

### Related pages

* [Quick Start](../../integration-guides/quick-start/)
* [Kickoff Checklist](kickoff-checklist.md)
* [FAQs](./)
* [Booking Overview](../../integration-guides/booking-overview/)
* [Post-booking Overview](../../integration-guides/post-booking-overview/)
* [Webhook Overview](../../integration-guides/webhook-overview/)
