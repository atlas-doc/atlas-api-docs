---
description: Build and validate the sandbox integration before UAT.
---

# Sandbox Development

{% include "../../.gitbook/includes/eva-help-hint.md" %}

Use this page to build and validate the full Atlas integration in sandbox.

{% hint style="info" %}
Before you build the integration, run the [Sandbox Validation Test Kit](../../readme/quick-start/sandbox-development/sandbox-validation-test-kit.md).

Use it to confirm credentials, network access, and the core happy path without writing code.
{% endhint %}

### Goal of this phase

Build the end-to-end integration flow in sandbox.

This phase should cover both API execution and webhook follow-up.

### Fast setup check

Use the [Sandbox Validation Test Kit](../../readme/quick-start/sandbox-development/sandbox-validation-test-kit.md) before full development work.

It validates `Search`, `Verify`, `Order`, and `Pay`.

If the final retrieve step times out, treat that as expected during ticketing polling.

### What sandbox can validate

Use sandbox to validate:

* request format and headers
* search, verify, order, payment, and query flow
* webhook handling and follow-up logic
* failure handling and edge cases
* UAT readiness

### What sandbox does not prove

Sandbox does **not** prove:

* live inventory quality
* production pricing accuracy
* real card charging behavior
* final airline-side behavior in all cases

Treat sandbox fares and outcomes as test-only.

### Before you start

Make sure you already have:

* sandbox credentials from ATRIP
* the correct sandbox endpoint
* request headers configured
* a basic server-side integration ready to test

### Use MCP during development

Use [MCP-Assisted Development](../../readme/quick-start/mcp-assisted-development.md) when you need help finding the right flow, page, or next API step.

It works well for:

* mapping `Search` to `Pay`
* checking which identifier to keep and reuse
* routing errors to the right troubleshooting page

### Development checklist

Complete these items in sandbox:

* configure authentication and headers
* point your client to sandbox
* implement search, verify, order, payment, and query
* register and validate webhooks
* test failure handling and edge cases

During this phase, keep and reuse:

* `routingIdentifier`
* `sessionId`
* `orderNo`

### Test mode

In test mode:

* bookings are simulated
* tickets are not issued with live airlines
* fares are sandbox fares
* test credentials only work in sandbox
* live credentials only work in production

Use test mode to validate:

* request construction
* booking state transitions
* payment and ticketing logic
* expected error handling
* webhook and follow-up behavior

### Sandbox fare behavior

Sandbox search results come from Atlas sandbox data.

Coverage and pricing are not the same as production.

Do not use sandbox prices for commercial comparison.

### Payment failure simulation

You can trigger common VCC error paths in `pay.do`.

#### Trigger payment decline

Use:

* Cardholder first name: `Reject`

Expected result:

* `604` — Payment declined by airline

#### Trigger 3DS error

Use:

* Cardholder first name: `Three DS`

Expected result:

* `616` — 3DS Authentication

Any card number and last name can be used for this specific failure simulation.

### Reference data for sandbox

Use these shared reference pages when you need published sandbox inputs:

* [Booking Overview](../booking-overview/)
* [Webhook Overview](../webhook-overview/)
* [Sandbox Test Routes](../../integration-reference/sandbox-test-data/sandbox-test-routes.md)
* [Sandbox Test Cards](../../integration-reference/sandbox-test-data/sandbox-test-cards.md)
* [Integration Reference](../../integration-reference/)

### Complete this phase when

You can do all of these reliably in sandbox:

* run the booking flow end to end
* keep and reuse `routingIdentifier`, `sessionId`, and `orderNo`
* validate the required payment path
* receive and process the required webhook events
* reproduce expected success and failure cases

### Output of this phase

* stable sandbox booking flow
* validated webhook handling
* evidence ready for UAT

### Next step

Move to [UAT Validation](uat-submission-guide.md) after the sandbox flow is stable.
