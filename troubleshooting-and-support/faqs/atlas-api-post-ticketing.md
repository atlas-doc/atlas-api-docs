---
description: >-
  Common post-booking questions about notifications, refunds, service requests,
  and urgent operations.
---

# Post-booking

{% include "../../.gitbook/includes/eva-help-hint.md" %}

Use this page for refund, schedule change, and operational follow-up questions.

### Do we get notified about schedule changes?

Yes, but not always through a single channel.\
Airlines may notify the booking contact directly.\
Atlas webhook and incident flows should also be configured.

### Does Atlas guarantee webhook delivery?

No.\
Webhook delivery is best effort.

Use airline emails, incident flows, and order queries for final confirmation.

### How should post-booking operations be handled?

Use Atlas APIs and ATRIP based on the action:

* refunds and cancellations
* ancillary add-ons
* service requests for changes
* incident follow-up

### Do you provide urgent post-sale support?

For urgent cases within 24 hours of departure, use the airline’s **Manage My Booking** flow where possible.

### Where should we check refund and cancellation policy?

Always use the airline’s latest policy as the source of truth.

### How long do refunds take?

Atlas usually submits refund requests to the airline within 4 hours.\
Final confirmation and fund return still depend on the airline.

After Atlas receives the funds, reconciliation and balance credit follow.

### How should booking changes be requested?

Create a Service Request in ATRIP for name correction, flight change, or similar post-booking action.

### Are booking changes supported through API?

Not as a general self-service API flow.\
Use a Service Request in ATRIP for change handling.

### How are involuntary changes handled?

For airline schedule changes or similar involuntary cases, use the refund flow in ATRIP.\
This is handled free of charge.

### Can baggage or seat be added after ticketing?

Yes, when the airline and order support it.\
Use the post-ticketing ancillary flow for supported cases.

### What happens in case of booking or service failure?

If Atlas causes incorrect booking or ticketing, Atlas will compensate with a replacement ticket when applicable.\
Refund delays remain dependent on airline processing.

### What support or training is provided for operations teams?

Atlas provides a go-live walkthrough after UAT completion.\
That includes ATRIP process guidance and follow-up Q\&A.

### How does refund handling differ by payment mode?

#### Deposit

* Atlas tracks refunds initiated through Atlas
* If the passenger or agency refunds directly with the airline, notify Atlas through ATRIP when required
* Atlas credits your Atlas balance after airline funds are received

#### VCC

Refunded funds usually go back to the original VCC account.\
Do not use the ATRIP **Agent and Passenger Initiated Refund** flow for VCC refunds.

### What refund initiation options are available in ATRIP?

#### Atlas-initiated refund

Use either:

* the **Refund** button
* a **Cancel & Refund** service request

#### Agency or passenger initiated refund

Use either:

* an **Agency & Passenger Initiated Refund** service request
* batch upload in the refund module

### How should refund follow-up be handled?

Wait at least 21 days after refund submission before follow-up.\
Then use the existing service request, or create a new refund follow-up request in ATRIP.

### Related pages

* [Refunds](../../integration-guides/post-booking-overview/post-booking-operations/refunds.md)
* [Post-booking Overview](../../integration-guides/post-booking-overview/)
* [Webhook Overview](../../integration-guides/webhook-overview/)
