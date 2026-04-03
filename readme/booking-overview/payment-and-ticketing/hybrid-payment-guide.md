---
description: >-
  Understand Atlas hybrid payment and switch between VCC and deposit when the
  order supports it.
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
tags:
  - tag: update
    primary: true
---

# Hybrid Payment Guide

Use this page when you need both the payment model and the fallback logic.

### What hybrid payment means

Atlas hybrid payment lets one booking flow use more than one supported payment path.

The main goal is continuity.

If one payment method cannot complete the order, you can move to another supported method instead of restarting the full process.

### Supported payment modes

The main modes in this guide are:

* **Deposit**
* **VCC pass-through**

In the most common hybrid payment flow:

* the first attempt uses VCC pass-through
* the fallback attempt uses deposit

The exact options still depend on airline, fare, and order capability.

{% hint style="info" %}
Hybrid payment is a controlled fallback model.

It does not mean every order can switch freely between all payment methods.
{% endhint %}

### Why to use hybrid payment

Use hybrid payment when you need a safer path to complete bookings under payment uncertainty.

This is especially useful when:

* `pay.do` fails for an unpaid order
* VCC pass-through is not accepted
* the order supports another payment method
* airline-side payment fails after the initial payment attempt

### What this page covers

This page explains:

* the hybrid payment concept
* when to keep the same order
* when to regenerate the order
* how to switch from VCC to deposit
* how to handle the ATRIP and API flows

### Core rule

Do not retry blindly.

Always confirm:

* the current order status
* whether the order is still payable
* which payment methods the order supports
* whether the same order can be reused or must be regenerated

### Recommended action order

1. Query the order status.
2. Check whether the order is still unpaid.
3. Check whether deposit is supported for that order.
4. Retry payment only when the order is still valid.
5. Regenerate the order when the original order is cancelled, expired, or no longer payable.

### Quick decision guide

{% stepper %}
{% step %}
### Check the current order

Confirm whether the order is still unpaid and payable.
{% endstep %}

{% step %}
### Check supported payment methods

Confirm whether the same order still supports deposit or another valid card path.
{% endstep %}

{% step %}
### Choose the next path

If the same order is still payable, switch payment method on the same order.

If the order is cancelled, expired, or no longer payable, regenerate the order first.
{% endstep %}
{% endstepper %}

### Hybrid payment paths

There are two common paths.

#### Path 1: same order, different payment method

Use this path when:

* the order is still unpaid
* the order is still payable
* deposit or another method is still supported on that order

#### Path 2: regenerate, then pay again

Use this path when:

* the original order was cancelled
* the payment window expired
* the order is no longer payable
* airline-side failure makes the original order unusable

### Scenario A: `pay.do` fails

If `pay.do` fails and the order is still not successfully paid, the usual next actions are:

1. retry the same payment when the issue is temporary
2. switch to deposit when the same order supports deposit
3. switch to another supported card when card-based payment is still allowed

This scenario stays on the same order only when the order is still payable.

#### Retry with deposit

Use deposit as a fallback when VCC pass-through fails and the same order still accepts payment.

This is the clearest hybrid payment case.

The order stays the same.

Only the payment method changes.

```json
{
  "orderNo": "XXXX",
  "paymentMethod": 1
}
```

#### Retry with another card

Use another card only when the order still supports card-based payment and the card type matches the order requirements.

### Scenario B: `pay.do` succeeds but airline payment fails

This scenario usually requires a different recovery path.

The payment request may succeed on the Atlas side, but the airline can still reject the payment later.

In that case, the original order may be cancelled or become unusable.

The usual sequence is:

1. confirm the final order status
2. treat the original order as unusable if it was cancelled
3. regenerate the order
4. pay the new order with deposit or another supported card

### Regenerate then pay

When the original order is cancelled or no longer payable, create a new order from the original order number.

```json
{
  "originalOrderNo": "{original order no}"
}
```

Then pay the new order:

```json
{
  "orderNo": "{new order no}",
  "paymentMethod": 1
}
```

This is also part of the hybrid payment model.

The payment path changes after the order is regenerated.

### Decision guide

Use the same order when:

* the order is unpaid
* the order is still valid for payment
* the fallback payment method is supported

Regenerate the order when:

* the order is cancelled
* the order is expired
* the order status no longer supports payment
* the airline-side failure invalidates the original order

<details>

<summary>Same order or regenerate order?</summary>

Use the **same order** when the order is still unpaid, still payable, and still supports the fallback payment method.

Use **regenerate order** when the order is cancelled, expired, locked by the previous payment flow, or no longer supports payment.

</details>

### ATRIP flow

{% stepper %}
{% step %}
### Open the order

Go to **My Orders** in ATRIP Flight Deck and find the affected order.
{% endstep %}

{% step %}
### Regenerate if needed

Use **Regenerate Order** when the original order is cancelled, expired, or no longer payable.
{% endstep %}

{% step %}
### Complete payment with the fallback method

Open the new or existing order and choose a supported fallback payment method.
{% endstep %}
{% endstepper %}

In the common ATRIP fallback flow:

1. open **My Orders**
2. locate the affected order
3. use **Regenerate Order** if the original order cannot be reused
4. open the new or existing order
5. complete payment with deposit or another supported method

### API flow

{% stepper %}
{% step %}
### Check the order first

Use order query before any retry.

Do not assume the previous payment attempt failed cleanly.
{% endstep %}

{% step %}
### Decide whether to reuse the order

Reuse the same order only when it is still unpaid and payable.

Regenerate the order when it is cancelled, expired, or locked by a failed flow.
{% endstep %}

{% step %}
### Retry with a supported payment method

Call `pay.do` with the fallback method.

Use deposit when VCC is blocked and deposit is supported.
{% endstep %}
{% endstepper %}

### Operational notes

* supported payment methods vary by airline and fare
* hybrid payment does not mean every order can switch freely between all methods
* payment success does not guarantee ticket issuance is complete
* avoid duplicate payment retries during in-flight processing
* use order status as the source of truth before every retry
* keep webhook handling in place for cancellation or payment-related follow-up

### Related pages

* [Payment & Ticketing](./)
* [Payments](../../../troubleshooting-and-support/faqs/atlas-api-payments.md)
* [Query Order](../../../integration-guides/booking-overview/query-order.md)
* [Payment Errors](../../../troubleshooting-and-support/errors-handing/payment-errors.md)
* [Order Maintenance](../../../integration-guides/post-booking-overview/post-booking-operations/order-maintenance.md)
* [Regenerate Order](../../../api-reference/post-booking-apis/regenerate-order.md)
