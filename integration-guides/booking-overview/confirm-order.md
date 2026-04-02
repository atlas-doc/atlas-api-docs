---
description: Confirm orders that require a commit step before payment.
---

# Confirm Order

Use this page for airlines that need order confirmation before ticketing.

This page uses `Confirm Order` as the primary name.

You may also see this step called `Order Commit`.

### Main API

* `orderCommit.do`

### Use this when you need

* FR confirmation flow
* Popup or iframe confirmation
* User confirmation before payment

### Notes

* This step is airline-specific
* It is required for FR flows
* Payment should follow only after confirmation is complete
* `Confirm Order` and `Order Commit` refer to the same API step

### Related pages

* [Create Order](create-order.md)
* [Payment & Ticketing](payment-and-ticketing.md)
* [FR Integration](../special-integrations/fr-integration.md)
* [Booking APIs](../../api-reference/booking-apis/)

### Full API reference

See endpoint-level details here:

* [Confirm Order](../../api-reference/booking-apis/confirm-order.md)
