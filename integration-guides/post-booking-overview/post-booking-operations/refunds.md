---
description: APIs for refund quotation, refund submission, and refund status queries.
---

# Refunds

{% include "../../../.gitbook/includes/eva-help-hint.md" %}

Use this section for the full refund lifecycle.

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

### Main APIs

* `refundQuotation.do`
* `refund.do`
* `queryRefundOrders.do`

### Use this when you need

* Voluntary refunds
* Involuntary refunds
* Void handling
* Refund status tracking

### Full API reference

See endpoint-level details here:

* [Refunds](../../../api-reference/post-booking-apis/refunds.md)

### Related pages

* [Finance](../../../troubleshooting-and-support/faqs/atlas-api-finance.md)
* [Post-booking](../../../troubleshooting-and-support/faqs/atlas-api-post-ticketing.md)
* [Error Codes](../../../troubleshooting-and-support/errors-handing/)
* [Post-booking APIs](../../../api-reference/post-booking-apis/)
