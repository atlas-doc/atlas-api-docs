---
description: >-
  Atlas API webhook registration and incident query reference for endpoint
  setup, updates, and event reconciliation.
---

# Webhook Registration & Incidents

{% include "../../.gitbook/includes/eva-help-hint.md" %}

Use this page to register your webhook endpoint and query incident records from the API reference layer.

Start here when you need to:

* register or update the webhook URL before go-live
* query incidents after missed or unresolved events
* reconcile webhook delivery with incident records

### FAQ

#### When should we register the webhook URL?

Register the webhook URL before go-live, then update it whenever the receiving endpoint changes.

#### When should we query incidents?

Query incidents when webhook delivery, schedule-change handling, or operational follow-up needs deeper reconciliation.

Use incident lookup when the event trail is incomplete or still unclear after webhook processing.

### What this page covers

* `updateWebhookURL.do` for webhook registration
* `event/getPageList.do` for incident lookup

### What comes next?

Use [Webhook Overview](../../integration-guides/webhook-overview/) for the operating model and event coverage.

Use [Incident Query](../../integration-guides/webhook-overview/incident-query.md) and [Incident Notification](../../integration-guides/webhook-overview/incident-notification.md) when you need deeper incident follow-up.

### Typical flow

{% stepper %}
{% step %}
### Register your webhook URL

Save the endpoint that Atlas should call for webhook delivery.
{% endstep %}

{% step %}
### Receive webhook events

Handle ticketing, schedule change, airline status, email, and incident notifications.
{% endstep %}

{% step %}
### Query incidents when needed

Use incident lookup to reconcile missed or unresolved events.
{% endstep %}
{% endstepper %}

### Use this when you need

* initial webhook setup
* webhook endpoint updates
* incident reconciliation
* operational follow-up after schedule changes or cancellations

### Related pages

* [Webhooks](../../integration-guides/webhook-overview/)
* [Incident Query](../../integration-guides/webhook-overview/incident-query.md)
* [Incident Notification](../../integration-guides/webhook-overview/incident-notification.md)

{% openapi-operation spec="atlas-api" path="/updateWebhookURL.do" method="post" %}
[OpenAPI atlas-api](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/16d5f2d8196b3ef49a60acb409c448368fd1ff7b7e7d5d750ed7be17dd37bd3c.json?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260607%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260607T043812Z&X-Amz-Expires=172800&X-Amz-Signature=42ed1445cc22afaa4312262c7e8f41326d2a538faff7539598025f25603213e6&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

{% openapi-operation spec="atlas-api" path="/event/getPageList.do" method="post" %}
[OpenAPI atlas-api](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/16d5f2d8196b3ef49a60acb409c448368fd1ff7b7e7d5d750ed7be17dd37bd3c.json?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260607%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260607T043812Z&X-Amz-Expires=172800&X-Amz-Signature=42ed1445cc22afaa4312262c7e8f41326d2a538faff7539598025f25603213e6&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}
