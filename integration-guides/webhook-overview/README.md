---
description: Webhook setup, event coverage, and incident follow-up guidance.
---

# Webhook Overview

Use this section to register webhook endpoints and consume event notifications.

### Overview

Webhooks will automatically notify you on airline changes that affect your customers’ bookings. For example, when an airline has changed the flight schedule affecting one of your orders, the Atlas API will send a notification about this event to your server, and you can process it. For example, you may take actions by updating your database or emailing the customer.

> Atlas provides the webhook functionality on the “best possible basis”. Atlas does not take the responsibility for providing all the notifications. For any schedule changes please always refer to the email sent by the airline to the email id provided in the booking request.

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
