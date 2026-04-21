---
description: >-
  Verify fares, routing, booking requirements, and session data before order
  creation.
---

# Verify

{% include "../../.gitbook/includes/eva-help-hint.md" %}

Use this page after offer selection.

{% hint style="info" %}
Use `bookingRequirement` from the verify response as the source of truth for booking input.

It tells you which passenger and document fields are required for `order.do`.
{% endhint %}

### Main API

* `verify.do`

### Inputs

* `routingIdentifier` from search

### Key outputs

* `sessionId` for order creation
* Latest fare and routing details
* `bookingRequirement` for required passenger and document fields
* Ancillary options

### Use this when you need

* Fare recheck before booking
* Final validation of routing details
* Required passenger and document rules for `order.do`

### Related pages

* [Search](search.md)
* [Create Order](create-order.md)
* [Booking APIs](../../api-reference/booking-apis/)

### Full API reference

See endpoint-level details here:

* [Verify](../../api-reference/booking-apis/verify.md)
