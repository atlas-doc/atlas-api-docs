---
description: >-
  Common payment-stage errors for expired orders, unsupported payment methods,
  passenger data, and VCC failures.
---

# Payment Errors

Use this page when `pay.do` fails.

### Highest-frequency codes

#### `401` Time out of payment

Payment was attempted after the payment deadline.

**Action**

* Regenerate the order or create a new booking

#### `402` / `404` Order status does not support payment or order already paid

The order is already paid, ticketing, or ticketed.

**Action**

* Query the order first
* Do not send duplicate payment requests

#### `403` Unsupported payment method

The chosen method is not allowed for this fare or airline.

**Action**

* Switch to another supported method
* Check supported payment fields before payment

#### `406` Payment operation is in progress

A previous payment request is still processing.

**Action**

* Wait and poll order status
* Avoid duplicate retries during in-flight payment

#### `407` Incorrect passenger information

The order data does not meet airline payment checks.

**Action**

* Check passenger fields
* Rebuild the order if required

#### `409` Additional baggage does not match the segment

Ancillary product selection is inconsistent with the order.

**Action**

* Re-check segment-specific `productCode`

#### `411` Generic payment error

Atlas could not complete payment due to account or settlement issues.

**Action**

* Check balance
* Check payment inputs
* Retry only after validation

#### `413` Card is not supported

Card type is not supported for this scenario.

**Action**

* Use a supported card brand

#### `414` Card mismatch

The payment card type does not match the card type used earlier in the flow.

**Action**

* Use a consistent card type across order and payment

#### `415` Order is not confirmed by user

Common in FR flow when `orderCommit.do` was not completed.

**Action**

* Complete order confirmation first
* Then retry payment

### Recommended troubleshooting order

1. Query the order before retrying payment
2. Check payment deadline and order status
3. Validate supported payment method
4. Validate passenger and ancillary data
5. Use deposit fallback when VCC is blocked

### Related pages

* [Payment & Ticketing](../../readme/booking-overview/payment-and-ticketing/)
* [Hybrid Payment Guide](../../readme/booking-overview/payment-and-ticketing/hybrid-payment-guide.md)
* [Payments](../faqs/atlas-api-payments.md)
* [Query Order](../../integration-guides/booking-overview/query-order.md)
