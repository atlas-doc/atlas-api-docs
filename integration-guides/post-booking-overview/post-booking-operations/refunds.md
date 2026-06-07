---
description: >-
  Atlas API refund flow for refund quotation, refund submission, and refund
  status tracking.
---

# Refunds

{% include "../../../.gitbook/includes/eva-help-hint.md" %}

Use this section for the full refund lifecycle.

Start here when you need to:

* check refundable amount and refund conditions
* submit a refund request
* track refund progress after submission

### FAQ

#### What is the standard Atlas API refund flow?

The standard flow is `refundQuotation.do` → `refund.do` → `queryRefundOrders.do`.

Use quotation first when you need the latest refundable amount and conditions before submission.

#### When can a refund request fail even before submission?

Refund requests can fail when ticketing is not complete, the refund offer expired, the order number is wrong, or the itinerary in the request is incomplete.

Check current order state and refund conditions first.

### What this section covers

* Request refund quotations
* Submit refund requests
* Query refund status and results

### Typical flow

{% stepper %}
{% step %}
### Refund Quotation

Get the latest refundable amount and refund conditions.
{% endstep %}

{% step %}
### Make a Refund

Submit the refund request with the quotation result or refund details.
{% endstep %}

{% step %}
### Query Refund Status

Track progress until the refund is completed, rejected, or closed.
{% endstep %}
{% endstepper %}

### What should you confirm before refund submission?

Confirm:

* the order is the correct original order
* ticketing is complete when required
* the itinerary in the refund request is complete
* the refund offer or quotation is still valid

The refund path and reconciliation timing can also depend on the payment mode.

### Main APIs

* `refundQuotation.do`
* `refund.do`
* `queryRefundOrders.do`

### Use this when you need

* Voluntary refunds
* Involuntary refunds
* Void handling
* Refund status tracking

### What comes next?

Use refund quotation to read current conditions.

Then submit the refund request.

After submission, use refund query until the case is completed, rejected, or closed.

### Full API reference

See endpoint-level details here:

* [Refunds](../../../api-reference/post-booking-apis/refunds.md)

### Related pages

* [Finance](../../../troubleshooting-and-support/faqs/atlas-api-finance.md)
* [Post-booking](../../../troubleshooting-and-support/faqs/atlas-api-post-ticketing.md)
* [Error Codes](../../../troubleshooting-and-support/errors-handing/)
* [Post-booking APIs](../../../api-reference/post-booking-apis/)
