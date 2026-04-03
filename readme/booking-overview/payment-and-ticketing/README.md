---
description: Pay orders and track ticketing completion.
---

# Payment & Ticketing

{% include "../../../.gitbook/includes/eva-help-hint.md" %}

Use this page to complete payment and wait for ticket issuance.

### Main API

* `pay.do`

### Use this when you need

* Deposit payment
* VCC pass-through payment
* BYOA payment
* MoR payment
* Ticket issuance tracking after payment

### Before you call

Confirm these points first:

* the order already exists
* the order is still unpaid
* the order supports the selected payment method
* card data is ready if you use card-based payment

For standard flows, call `order.do` before `pay.do`.

### Payment methods

* `1`: Deposit
* `3`: VCC passthrough
* `4`: BYOA
* `5`: MoR

### Key inputs

Always send:

* `orderNo`
* `paymentMethod`

Send `creditCard` when using:

* VCC passthrough
* MoR

`threeDS.ip` is only relevant for MoR.

### What to watch

* supported payment methods vary by airline and fare
* card brand must match the order requirements
* payment can fail if the booking is past deadline
* payment success does not always mean ticketing is already finished
* you still need order follow-up until the final ticketing state is confirmed

### Best practice

* read supported payment methods from the booking flow before payment
* use deposit when you need fare guarantee after payment
* use VCC only when the fare supports it
* poll order status after payment until ticketing completes
* handle payment retries carefully to avoid duplicate charges

### Common failure cases

Common payment response failures include:

* invalid request data
* payment after deadline
* unsupported payment method
* order already paid
* payment already in progress
* missing passenger data
* card not supported
* card mismatch
* order not confirmed in FR flow

Use the API response `status` as the source of truth.

### Related pages

* [Create Order](../../../integration-guides/booking-overview/create-order.md)
* [Confirm Order](../../../integration-guides/booking-overview/confirm-order.md)
* [Query Order](../../../integration-guides/booking-overview/query-order.md)
* [Hybrid Payment Guide](hybrid-payment-guide.md)
* [Error Codes](../../../troubleshooting-and-support/errors-handing/)
* [Booking APIs](../../../api-reference/booking-apis/)

### Full API reference

See endpoint-level details here:

* [Payment & Ticketing](../../../api-reference/booking-apis/payment-and-ticketing.md)
