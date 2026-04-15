---
description: Track recent documentation updates and newly published guides.
---

# 📣 What's New

{% include ".gitbook/includes/eva-help-hint.md" %}

Check this page first for recent documentation updates.

{% hint style="success" %}
Latest update: [MCP-Assisted Development](readme/quick-start/mcp-assisted-development.md) is now available under **Quick Start**.
{% endhint %}

{% hint style="info" %}
New: [MCP-Assisted Development](readme/quick-start/mcp-assisted-development.md) explains where GitBook MCP fits in Atlas API development.
{% endhint %}

### Latest highlight

#### MCP-Assisted Development

Published [MCP-Assisted Development](readme/quick-start/mcp-assisted-development.md) under **Quick Start**.

Use it when you need to:

* find the right workflow faster
* understand the next API step in the booking flow
* route issues to the right troubleshooting page

#### Sandbox Validation Test Kit

Published [Sandbox Validation Test Kit](readme/quick-start/sandbox-development/sandbox-validation-test-kit.md) under **Quick Start**.

Use it when you need to:

* validate sandbox credentials before coding
* confirm network access and core booking flow readiness
* run `Search`, `Verify`, `Order`, and `Pay` with a ready-made test kit
* recheck sandbox health after credential or IP changes

### Change log

{% updates format="full" %}
{% update date="2026-04-15" %}
## Added MCP-Assisted Development

Published [MCP-Assisted Development](readme/quick-start/mcp-assisted-development.md) for teams using GitBook MCP during Atlas API integration.

Use it when you need to:

* find the correct workflow before coding
* understand which identifier or API comes next
* jump from development questions to the right reference or troubleshooting page

The guide also includes prompt patterns and usage boundaries for production-safe development.
{% endupdate %}

{% update date="2026-04-09" %}
## Added Sandbox Validation Test Kit

Published [Sandbox Validation Test Kit](readme/quick-start/sandbox-development/sandbox-validation-test-kit.md) for a no-code sandbox validation run.

Use it when you need to:

* confirm credentials and network access before development
* run the core sandbox happy path with Newman
* verify `Search`, `Verify`, `Order`, and `Pay` in one pass
* quickly check sandbox readiness after environment changes

The page also explains the expected final retrieve timeout during ticketing polling.
{% endupdate %}

{% update date="2026-04-08" %}
## Improved Error Codes landing page

Updated [Error Codes](troubleshooting-and-support/errors-handing/) with:

* retry policy guidance
* a quick decision table for high-frequency codes
* high-risk mistakes to avoid during retry
* pattern-based checks for common integration issues

This makes the page more useful as the main troubleshooting entry point.
{% endupdate %}

{% update date="2026-04-03" %}
## Added Hybrid Payment Guide

Published [Hybrid Payment Guide](readme/booking-overview/payment-and-ticketing/hybrid-payment-guide.md) under **Payment & Ticketing**.

Use it when you need to:

* switch from VCC pass-through to deposit
* decide whether to reuse or regenerate an order
* handle hybrid payment fallback in ATRIP and API flows
{% endupdate %}
{% endupdates %}
