---
description: >-
  Atlas API webhook setup, event coverage, delivery expectations, and incident
  follow-up guidance.
---

# Webhook Overview

{% include "../../.gitbook/includes/eva-help-hint.md" %}

Use this section to register webhook endpoints and consume event notifications.

Start here when you need to:

* register webhook delivery before go-live
* understand which booking events Atlas can notify
* decide how webhook fits with order query and airline email

### FAQ

#### Are Atlas webhooks guaranteed?

No.

Webhook delivery is best effort.

Use order query, airline email, and incident follow-up for final reconciliation.

#### What should webhook be used for?

Use webhook to speed up event handling for ticketing completion, schedule changes, airline status updates, email capture, and incident follow-up.

Do not treat webhook as the only source of truth for booking state.

### Overview

Webhooks will automatically notify you on airline changes that affect your customers’ bookings. For example, when an airline has changed the flight schedule affecting one of your orders, the Atlas API will send a notification about this event to your server, and you can process it. For example, you may take actions by updating your database or emailing the customer.

> Atlas provides the webhook functionality on the “best possible basis”. Atlas does not take the responsibility for providing all the notifications. For any schedule changes please always refer to the email sent by the airline to the email id provided in the booking request.

### Recommended webhook model

Use webhook as a near-real-time signal.

Then confirm the final state with order query, incident query, or airline email when needed.

### Typical flow

{% stepper %}
{% step %}
### Register your endpoint

Use [Webhook Registration & Incidents](../../api-reference/webhook-and-incident-apis/webhook-registration-and-incidents.md) to save the webhook URL before go-live.
{% endstep %}

{% step %}
### Receive and process events

Handle ticketing, schedule, airline, email, and incident notifications. Currently, we send out webhook notifications in four scenarios:

1. Ticket booked: [Ticketing Complete Notification](ticketing-complete-notification.md)
2. Change in flight schedule: [Schedule Change Notification](schedule-change-notification.md)
3. Airline status update: [Airline Status Update Notification](airline-status-update-notification.md)
4. Email received: [Email Notification](email-notification.md)
{% endstep %}

{% step %}
### Reconcile when needed

Use incident queries and order APIs to confirm final state.

1. Incident notification: [Incident Notification](incident-notification.md)
2. Incident query: [Incident Query](incident-query.md)
{% endstep %}
{% endstepper %}

### What webhook should not replace

Webhook should not replace:

* `queryOrderDetails.do` for final ticketing confirmation
* airline email for schedule-change awareness
* incident query for deeper incident reconciliation
