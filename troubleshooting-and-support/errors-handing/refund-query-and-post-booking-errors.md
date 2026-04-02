---
description: >-
  Common errors for refund quotation, refund submission, refund query, order
  query, and post-booking ancillaries.
---

# Refund, Query & Post-booking Errors

Use this page when issues happen after ticketing.

### Refund quotation and submission

#### `801` Order does not exist

The order number is wrong.

**Action**

* Check the original ticket order number

#### `809` Order not ticketed

Refund was requested before ticketing completed.

**Action**

* Wait until ticketing finishes
* Retry refund later

#### `811` Completed itineraries are not entered

The refund request does not include the required full itinerary.

**Typical causes**

* Missing one segment of a connection
* Partial refund on a round trip that must be handled together
* Sector already flown

**Action**

* Submit the full required itinerary
* Contact the airline or Atlas for partially flown cases

#### `814` Refund submission is in progress

A previous refund submission is still processing.

**Action**

* Wait before retrying

#### `816` / `817` / `818` Refund already submitted

A matching refund or claim already exists.

**Action**

* Do not resubmit
* Query refund status instead

### Query order

#### `703` No order found

The lookup parameters do not match an existing order.

**Action**

* Re-check `orderNo`, `airlinePNR`, and carrier values

#### `705` Timeout

The order retrieval request timed out.

**Action**

* Retry after a short wait

### Post-booking ancillaries

#### `117` Order is not in ticketed status

Ancillary search was attempted too early.

**Action**

* Wait until the original order is ticketed

#### `118` Ancillary not supported for this airline

Atlas cannot support this ancillary flow for the airline.

**Action**

* Check direct airline flow or open a service request

#### `502` Price changed during ancillary order

Ancillary price changed after search.

**Action**

* Search ancillary options again

#### `504` / `505` Additional baggage not allowed

The baggage was already added in the booking flow or in a previous post-booking order.

**Action**

* Do not submit duplicate baggage orders

### Related pages

* [Refunds](../../integration-guides/post-booking-overview/post-booking-operations/refunds.md)
* [Post-booking Operations](../../integration-guides/post-booking-overview/post-booking-operations/)
* [Post-ticketing Ancillaries](../../integration-guides/post-booking-overview/post-booking-operations/post-ticketing-ancillaries.md)
* [Order Maintenance](../../integration-guides/post-booking-overview/post-booking-operations/order-maintenance.md)
