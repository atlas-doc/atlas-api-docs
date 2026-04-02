---
description: >-
  Independent real-time price check flow for offer retrieval, optional
  ancillaries, order creation, and ticketing.
---

# Get Offer

Use this page when you need an independent offer lookup flow.

{% hint style="info" %}
Use OpenAPI naming as the source of truth.

Use `getOffers.do` in docs and integration.
{% endhint %}

### Main API

* `getOffers.do`

### Inputs

* Accurate itinerary details
* Passenger mix when required by the request
* Any fields required by the current API reference

### Key outputs

* Latest bookable fare
* Inventory status
* `OfferId` for downstream order creation

### How this differs from standard search

#### Standard search flow

Use `search.do` when Atlas is your primary shopping entry point.

That flow is best when you want Atlas to return available offers first.

#### Get Offer flow

Use `getOffers.do` when you already know the target itinerary.

This flow is better for direct price checks, independent validation, and external shopping paths.

#### Practical difference

The standard search flow usually continues through `verify.do`.

The Get Offer flow is designed around the returned `OfferId` for downstream order creation.

### Use this when you need

* An offer lookup flow without standard search
* A secondary price check before order creation
* Lowest-price validation before ticketing
* A flow driven by your own flight data source

### Common scenarios

#### Use your own flight data source

Use `getOffers.do` when flight selection happens outside the standard Atlas search flow.

This lets you fetch the latest bookable fare and `OfferId` directly.

#### Run a final price check before order creation

Use `getOffers.do` to re-check the latest bookable price before you create the order.

This helps reduce fare drift between quote and booking.

#### Compare channels before ticketing

Use `getOffers.do` when you need a real-time validation point before sending the order into ticketing.

This is useful when you optimize for the latest available price before completion.

### Recommended business chain

#### Minimal chain

Use this path when you only need fare retrieval and ticketing:

1. Call `getOffers.do`
2. Keep the returned `OfferId`
3. Call `order.do`
4. Call `pay.do`

#### Chain with ancillaries

Use this path when baggage or seat selection is required:

1. Call `getOffers.do`
2. Confirm the fare and target flight
3. Query `getLuggage.do` or `seatAvailability.do` if needed
4. Create the order with `order.do`
5. Complete payment with `pay.do`

#### When to stop and re-check

Stop and refresh the offer if any of these change:

* target flight
* passenger mix
* expected fare
* ancillary requirement that affects the booking decision

### Typical flow

{% stepper %}
{% step %}
### Get Offer

Call `getOffers.do` with the target itinerary.

Keep the returned `OfferId`.
{% endstep %}

{% step %}
### Optional ancillaries

If needed, query `getLuggage.do` or `seatAvailability.do`.

Use this only after the offer matches your target flight and price.
{% endstep %}

{% step %}
### Create Order

Call `order.do` with the returned `OfferId` and required booking data.
{% endstep %}

{% step %}
### Pay and ticket

Call `pay.do` to complete ticketing.
{% endstep %}
{% endstepper %}

### When to use ancillary queries

#### Use `getLuggage.do`

Use it when baggage price or baggage options affect conversion.

Run it after you confirm the target offer.

#### Use `seatAvailability.do`

Use it when seat availability or paid seat selection matters before booking.

Airline support and session rules may vary by carrier.

#### Keep ancillaries optional

Do not make ancillary queries part of the base flow unless the business needs them.

The shortest production path is still `getOffers.do` → `order.do` → `pay.do`.

### Implementation guidance

#### Best fit

This flow fits partners who already control shopping logic.

It also fits flows where a final Atlas-side price check is needed before booking.

#### Data to retain

Retain the exact itinerary context used for `getOffers.do`.

Retain the returned `OfferId` until order creation is completed.

#### Suggested validation

Before `order.do`, confirm:

* flight matches the intended itinerary
* fare matches the expected sell logic
* passenger mix is still correct
* ancillary selection is complete when required

### Operational notes

#### Source of truth

Use the OpenAPI schema as the source of truth for request fields and response fields.

#### Naming

Use `getOffers.do` in implementation material, support replies, and customer-facing guidance.

#### Error handling

If the order or payment step fails because fare or availability changed, restart from a fresh offer lookup.

Use the latest returned data instead of retrying with stale assumptions.

### FAQ

#### Does `getOffers.do` replace `search.do`?

No.

Use `search.do` when Atlas is the main shopping entry point.

Use `getOffers.do` when you already know the target itinerary or need an independent price check.

#### Do I still need `verify.do` in this flow?

Not in the standard Get Offer path described on this page.

This flow is centered on `OfferId` and downstream order creation.

#### Is ancillary lookup mandatory?

No.

Use `getLuggage.do` or `seatAvailability.do` only when seat or baggage choice matters before booking.

#### When should I refresh the offer?

Refresh the offer when any booking-critical input changes.

Typical triggers:

* passenger count changes
* target flight changes
* expected fare changes
* booking is delayed and current pricing may be stale

#### Can I use Get Offer with my own shopping engine?

Yes.

This is one of the main use cases for this flow.

Keep your itinerary mapping consistent with the request fields defined in OpenAPI.

### Failure handling

#### If `getOffers.do` fails

Check request completeness first.

Then confirm itinerary data, passenger data, and any required fields defined in OpenAPI.

If the issue is transient, retry with controlled backoff.

#### If `order.do` fails after Get Offer

Do not assume the returned offer is still valid.

If the failure points to fare, inventory, or booking-state drift, call `getOffers.do` again and rebuild the order request from fresh data.

#### If `pay.do` fails

Check whether the order was already paid or is still processing.

Do not send duplicate payment blindly.

Query order state when needed before retrying.

#### When not to retry immediately

Avoid instant retries when the issue may be caused by:

* stale fare data
* unsupported payment method
* invalid passenger or contact data
* airline-side restrictions

Fix the root cause first.

### Logging and support guidance

#### Keep these values in logs

Capture the minimum fields needed for troubleshooting:

* request timestamp
* itinerary summary
* passenger mix
* `OfferId`
* `orderNo` after order creation
* payment method type
* final response status and message

#### Keep request linkage clear

Log the Get Offer request and the downstream order request as one business chain.

This makes fare drift and state mismatch easier to trace.

#### Escalation readiness

When escalating, provide:

* API name
* request time
* key identifier such as `OfferId` or `orderNo`
* response code
* response message

This speeds up support review.

### Notes

* This flow does not start from the standard `search.do` path.
* Use the current API reference as the source of truth for required fields.
* Use OpenAPI naming as the source of truth for interface names.
* Use `getOffers.do` as the official interface name in implementation material.

### Related pages

* [Search](search.md)
* [Create Order](create-order.md)
* [Payment & Ticketing](payment-and-ticketing.md)
* [Seats & Baggage](seats-and-baggage.md)

### Full API reference

See endpoint-level details here:

* [Get Offer](../../api-reference/booking-apis/get-offer.md)
* [Inflow Seat & Baggage](../../api-reference/booking-apis/inflow-seat-and-baggage.md)
* [Create Order](../../api-reference/booking-apis/create-order.md)
* [Payment & Ticketing](../../api-reference/booking-apis/payment-and-ticketing.md)
