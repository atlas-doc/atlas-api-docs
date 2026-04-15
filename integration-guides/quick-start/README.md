---
description: Four-phase integration path from sandbox access to production go-live.
---

# Quick Start

{% include "../../.gitbook/includes/eva-help-hint.md" %}

Use this guide to move from Atlas sandbox access to live launch.

{% include "../../.gitbook/includes/sandbox-search-currency-note.md" %}

<figure><img src="../../.gitbook/assets/FlowChart_1_QuickStart.png" alt=""><figcaption><p>End-to-end integration flow from sandbox access to go-live</p></figcaption></figure>

### Integration flow

{% stepper %}
{% step %}
### Sandbox Access

Generate sandbox credentials and confirm the request basics.
{% endstep %}

{% step %}
### Sandbox Development

Build and validate the full integration in sandbox.
{% endstep %}

{% step %}
### UAT Validation

Complete the required UAT track after sandbox development is stable.
{% endstep %}

{% step %}
### Production Go-Live

After UAT passes and your account is switched to `LIVE`, generate production credentials and switch to production endpoints for go-live.
{% endstep %}
{% endstepper %}

### How the full flow works

#### 1. Sandbox Access

This is the starting point of the integration.

Generate your sandbox client ID and client secret in ATRIP.

Before moving forward, confirm:

* standard headers
* request format
* identifier handling
* gzip handling

You are ready for the next phase when sandbox requests can be sent successfully.

Use [Sandbox Access](making-requests.md) for this setup.

#### 2. Sandbox Development

Use sandbox to complete the actual integration work.

This phase usually includes:

* sandbox environment setup
* search, verify, order, and payment
* order query and ticketing follow-up
* webhook registration and event handling
* sandbox test data and failure simulation

The goal is not only to call APIs successfully.

The goal is to complete the end-to-end business flow in sandbox.

Use these pages during development:

* [Sandbox Development](sandbox-development.md)
* [MCP-Assisted Development](../../readme/quick-start/mcp-assisted-development.md)
* [Booking Overview](../booking-overview/)
* [Webhook Overview](../webhook-overview/)

During this phase, keep these identifiers for later steps:

* Search: `routingIdentifier`
* Verify: `sessionId`
* Order: `orderNo`

Move to UAT only after the sandbox flow is stable and repeatable.

#### 3. UAT Validation

UAT is the validation phase before production.

Use this phase to prove that your integration is ready for go-live.

Prepare:

* the correct UAT template
* end-to-end evidence
* webhook samples when required
* relevant order numbers or request IDs

The main output of this phase is UAT approval.

Use [UAT Validation](uat-submission-guide.md) for the submission steps.

#### 4. Production Go-Live

Start this phase when your sandbox work is complete and you are ready for production.

Then:

* complete the required UAT work
* wait for your customer manager to switch the account to `LIVE`
* generate production credentials
* replace sandbox endpoints
* run a controlled smoke test
* monitor the first live orders and webhooks
* go live in production

This completes the move from test integration to live operation.

Use [Production Go-Live](production-go-live.md) for the go-live checklist.

### What each phase produces

* Sandbox Access → sandbox client ID and client secret
* Sandbox Development → stable sandbox booking and webhook flow
* UAT Validation → approved validation result
* Production Go-Live → production-ready environment

### First end-to-end test resource

If you want a no-code environment check first, use [Sandbox Validation Test Kit](../../readme/quick-start/sandbox-development/sandbox-validation-test-kit.md).

Then use this Postman collection during sandbox development:

{% file src="../../.gitbook/assets/TheAtlas UAT Test Shopping & Ticketing Services Only Postman Collection.zip" %}
