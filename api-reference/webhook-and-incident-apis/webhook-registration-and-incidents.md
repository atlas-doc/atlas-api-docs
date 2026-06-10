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

Register the webhook URL before go-live.

Then update it whenever the receiving endpoint changes.

The same URL receives all supported events, including `order.void`.

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

Handle ticketing, void, schedule change, airline status, email, and incident notifications.
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

### Registration scope

Register one webhook URL with `updateWebhookURL.do`.

Atlas uses that URL for all supported webhook event types.

That includes `order.void`.

### Related pages

* [Webhooks](../../integration-guides/webhook-overview/)
* [Incident Query](../../integration-guides/webhook-overview/incident-query.md)
* [Incident Notification](../../integration-guides/webhook-overview/incident-notification.md)

{% openapi-operation spec="atlas-api" path="/updateWebhookURL.do" method="post" %}
[OpenAPI atlas-api](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/c2c450b51656273efc99b5771c703cdf1e99923fa326d50b30f9bd2a7d1bdff6.json?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260610%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260610T164511Z&X-Amz-Expires=172800&X-Amz-Signature=3ee5ba33f9fbb01fcb748c4212e0fc79ac229c36d02a4439538e5a654c849c38&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

{% openapi-operation spec="atlas-api" path="/event/getPageList.do" method="post" %}
[OpenAPI atlas-api](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/c2c450b51656273efc99b5771c703cdf1e99923fa326d50b30f9bd2a7d1bdff6.json?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260610%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260610T164511Z&X-Amz-Expires=172800&X-Amz-Signature=3ee5ba33f9fbb01fcb748c4212e0fc79ac229c36d02a4439538e5a654c849c38&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}
