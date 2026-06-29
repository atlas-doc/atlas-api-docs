---
description: >-
  Start here for onboarding, core booking flows, post-booking actions, and
  operational setup.
---

# Integration Guides

{% include ".gitbook/includes/eva-help-hint.md" %}

Use this section to complete your Atlas API integration from setup to go-live.

### Recommended reading order

1. [Quick Start](integration-guides/quick-start/)
2. [Atlas AI Assistant Skill](readme/quick-start/atlas-ai-assistant-skill.md)
3. [Sandbox Access](integration-guides/quick-start/making-requests.md)
4. [Sandbox Development](integration-guides/quick-start/sandbox-development.md)
5. [Booking Overview](integration-guides/booking-overview/)
6. [Webhook Overview](integration-guides/webhook-overview/)
7. [UAT Validation](integration-guides/quick-start/uat-submission-guide.md)
8. [Production Go-Live](integration-guides/quick-start/production-go-live.md)

### Choose the right path

#### New integration

Start with [Quick Start](integration-guides/quick-start/).

Use [Atlas AI Assistant Skill](readme/quick-start/atlas-ai-assistant-skill.md) if you want an importable AI helper during implementation.

Then move through:

* [Sandbox Access](integration-guides/quick-start/making-requests.md)
* [Sandbox Development](integration-guides/quick-start/sandbox-development.md)
* [UAT Validation](integration-guides/quick-start/uat-submission-guide.md)
* [Production Go-Live](integration-guides/quick-start/production-go-live.md)

#### Core booking flow

Use [Booking Overview](integration-guides/booking-overview/) for search, verify, order, payment, and order lookup.

#### Local pricing data

Use [Flight Data Feed](readme/flight-data-feed.md) when you need scheduled full and incremental fare delivery for your own database, AI retrieval, or low-latency display.

#### Post-booking operations

Use [Post-booking Overview](integration-guides/post-booking-overview/) and [Post-booking Operations](integration-guides/post-booking-overview/post-booking-operations/) for refunds, maintenance, ancillaries, and claims.

#### Special programs

Use [Special Integrations](integration-guides/special-integrations/) only when your business flow requires airline-specific or discounted fare logic.

#### Operational tools

Use [Utility API Overview](integration-guides/utility-api-overview/) for balance, email, export, and ATRIP access.

#### Shared test and reference data

Use [Integration Reference](integration-reference/) for shared values, sandbox test routes, and sandbox test cards.

### Typical integration flow

{% stepper %}
{% step %}
### Sandbox Access

Collect sandbox credentials and confirm required request headers.
{% endstep %}

{% step %}
### Sandbox Development

Build the booking flow in sandbox and validate webhook handling.
{% endstep %}

{% step %}
### UAT Validation

Submit the required UAT track with evidence.
{% endstep %}

{% step %}
### Production Go-Live

After UAT passes and your account is switched to `LIVE`, generate production credentials and switch to production endpoints for go-live.
{% endstep %}
{% endstepper %}

### When to use the API reference

Use [API Reference](api-reference/) when you need exact schemas, parameters, and endpoint-level examples.

### Browse endpoint groups

* [Booking APIs](api-reference/booking-apis/)
* [Post-booking APIs](api-reference/post-booking-apis/)
* [Webhook & Incident APIs](api-reference/webhook-and-incident-apis/)
* [Utility APIs](api-reference/utility-apis/)

### Need troubleshooting help

Use [Troubleshooting & Support](troubleshooting-and-support/) for FAQs, error codes, and escalation paths.
