---
description: >-
  Atlas API verify flow for fare recheck, booking requirements, ancillary
  options, and session handling before order creation.
---

# Verify

{% include "../../.gitbook/includes/eva-help-hint.md" %}

Use this page after offer selection.

{% hint style="info" %}
Use `bookingRequirement` from the verify response as the source of truth for booking input.

It tells you which passenger and document fields are required for `order.do`.
{% endhint %}

Start here when you need to:

* recheck fare and routing before booking
* get the required passenger and document fields
* create a fresh `sessionId` for `order.do`

### FAQ

#### When should I call `verify.do`?

Call `verify.do` after `search.do` and before `order.do`.

Use it to refresh fare, routing, and booking requirements close to booking time.

#### What should I read from the verify response?

Read `sessionId`, latest fare details, ancillary options, and `bookingRequirement`.

Treat `bookingRequirement` as the source of truth for the order request.

### Main API

* `verify.do`

### Inputs

* `routingIdentifier` from search

### Key outputs

* `sessionId` for order creation
* Latest fare and routing details
* `bookingRequirement` for required passenger and document fields
* Ancillary options

### What should you keep from verify?

Keep:

* `sessionId` for `order.do`
* `bookingRequirement` for required input fields
* current ancillary options when baggage or seats matter before booking

Do not reuse an expired `sessionId`.

### Use this when you need

* Fare recheck before booking
* Final validation of routing details
* Required passenger and document rules for `order.do`

### What comes next?

Use [Create Order](create-order.md) with the returned `sessionId`.

If price, inventory, or ancillaries changed, use the verify result as the current source of truth.

### Related pages

* [Search](search.md)
* [Create Order](create-order.md)
* [Booking APIs](../../api-reference/booking-apis/)

### Full API reference

See endpoint-level details here:

* [Verify](../../api-reference/booking-apis/verify.md)
