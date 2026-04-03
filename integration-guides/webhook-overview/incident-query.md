---
description: Query incident records and filter webhook-related events.
---

# Incident Query

{% include "../../.gitbook/includes/eva-help-hint.md" %}

Use this page to search incident records when webhook delivery or event state needs confirmation.

### Main API

* `event/getPageList.do`

### Use this when you need

* Reconcile missed webhook events
* Filter incidents by order, passenger, or airline
* Review event confirmation status
* Investigate schedule change or cancellation history

### Common query patterns

#### Find incidents for one order

Use:

* `orderNo`
* `pageSize`

#### Find schedule changes for one airline

Use:

* `eventType`
* `airline`
* `eventTimeStart`
* `eventTimeEnd`
* `pageSize`

#### Find unresolved incidents

Use:

* `eventStatus`
* `pageSize`

### Common filters

* `eventId`
* `orderNo`
* `eventType`
* `pnr`
* `paxName`
* `paxEmail`
* `airline`
* `eventStatus`
* `eventTimeStart`
* `eventTimeEnd`
* `pageIndex`
* `pageSize`

### Required field

* `pageSize`

### Response highlights

* `records`
* `pageIndex`
* `pageSize`
* `total`
* Event status and confirmation fields

### Tips

* always send `pageSize`
* start with `orderNo` when debugging one affected booking
* add time ranges when querying broad incident sets
* use this together with webhook payload logs and order query results

### Full API reference

See endpoint-level details here:

* [Webhook Registration & Incidents](../../api-reference/webhook-and-incident-apis/webhook-registration-and-incidents.md)

### Related pages

* [Incident Notification](incident-notification.md)
* [Schedule Change Notification](schedule-change-notification.md)
* [Query Order](../booking-overview/query-order.md)
