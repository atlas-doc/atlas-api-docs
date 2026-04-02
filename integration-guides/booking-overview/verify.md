---
description: >-
  Verify fares, routing, booking requirements, and session data before order
  creation.
---

# Verify

Use this page after offer selection.

### Main API

* `verify.do`

### Inputs

* `routingIdentifier` from search

### Key outputs

* `sessionId` for order creation
* Latest fare and routing details
* Booking requirements and ancillary options

### Use this when you need

* Fare recheck before booking
* Final validation of routing details
* Required passenger and document rules

### Related pages

* [Search](search.md)
* [Create Order](create-order.md)
* [Booking APIs](../../api-reference/booking-apis/)

### Full API reference

See endpoint-level details here:

* [Verify](../../api-reference/booking-apis/verify.md)
