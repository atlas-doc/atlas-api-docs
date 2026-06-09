---
description: >-
  Latest Atlas API documentation updates, new integration guides, and
  recommended next reads.
---

# 📣 Atlas API Documentation Updates

{% include ".gitbook/includes/eva-help-hint.md" %}

Use this page to track the latest Atlas API documentation updates.

{% hint style="success" %}
Latest update: `seatAvailability.do` now requires a valid `sessionId` or `OfferId`.
{% endhint %}

It highlights new guides, major troubleshooting improvements, and the next pages to read by use case.

Start here if you need to:

* find the newest Atlas API guides
* see what changed for sandbox, booking, payment, or troubleshooting
* choose the right page to read next

### Latest Atlas API documentation updates

#### SeatAvailability call rules update

Updated the seat-selection guidance to reflect the current `seatAvailability.do` calling rules.

What changed:

* independent mode is no longer available
* `seatAvailability.do` now requires `sessionId` from `verify.do` or `OfferId` from `getOffers.do`
* flight-only seat quote requests are not supported

Read next:

* [Inflow Seat & Baggage](api-reference/booking-apis/inflow-seat-and-baggage.md)
* [Seats & Baggage](integration-guides/booking-overview/seats-and-baggage.md)
* [Verify](integration-guides/booking-overview/verify.md)

#### MCP-Assisted Development

Read [MCP-Assisted Development](readme/quick-start/mcp-assisted-development.md) when you want to use GitBook MCP during Atlas API integration.

Best for:

* teams starting a sandbox build
* developers mapping the booking flow
* teams routing implementation questions faster

Read next:

* [Quick Start](integration-guides/quick-start/)
* [API Reference](api-reference/)

#### Sandbox Validation Test Kit

Read [Sandbox Validation Test Kit](readme/quick-start/sandbox-development/sandbox-validation-test-kit.md) when you need a no-code sandbox validation run before development or after environment changes.

Best for:

* validate sandbox credentials before coding
* confirm network access and core booking flow readiness
* teams rechecking sandbox health after credential or IP changes

Read next:

* [Sandbox Development](integration-guides/quick-start/sandbox-development.md)
* [UAT Validation](integration-guides/quick-start/uat-submission-guide.md)

#### Error Codes improvements

[Error Codes](troubleshooting-and-support/errors-handing/) now works better as the main troubleshooting entry point.

Best for:

* teams handling high-frequency integration failures
* developers defining safe retry behavior
* operations teams checking likely root causes

Read next:

* [Common & Access Errors](troubleshooting-and-support/errors-handing/common-and-access-errors.md)
* [Verify, Order & Ticketing Errors](troubleshooting-and-support/errors-handing/verify-order-and-ticketing-errors.md)

### Start here by use case

#### New Atlas API integration

Start with:

* [Quick Start](integration-guides/quick-start/)
* [MCP-Assisted Development](readme/quick-start/mcp-assisted-development.md)
* [Booking Overview](integration-guides/booking-overview/)

#### Sandbox validation

Start with:

* [Sandbox Access](integration-guides/quick-start/making-requests.md)
* [Sandbox Validation Test Kit](readme/quick-start/sandbox-development/sandbox-validation-test-kit.md)
* [Sandbox Development](integration-guides/quick-start/sandbox-development.md)

#### Booking and payment flow

Start with:

* [Booking Overview](integration-guides/booking-overview/)
* [Payment & Ticketing](readme/booking-overview/payment-and-ticketing/)
* [Hybrid Payment Guide](readme/booking-overview/payment-and-ticketing/hybrid-payment-guide.md)

#### Troubleshooting and support

Start with:

* [Error Codes](troubleshooting-and-support/errors-handing/)
* [FAQs](troubleshooting-and-support/faqs/)
* [Webhook Overview](integration-guides/webhook-overview/)

### FAQ

#### What changed in the Atlas API docs recently?

Recent updates changed `seatAvailability.do` call rules, added [MCP-Assisted Development](readme/quick-start/mcp-assisted-development.md), published [Sandbox Validation Test Kit](readme/quick-start/sandbox-development/sandbox-validation-test-kit.md), and improved [Error Codes](troubleshooting-and-support/errors-handing/) as a troubleshooting entry point.

#### Which guide should I read first for sandbox integration?

Start with [Quick Start](integration-guides/quick-start/). Then use [Sandbox Validation Test Kit](readme/quick-start/sandbox-development/sandbox-validation-test-kit.md) to confirm readiness before coding.

#### Where should I start for booking, payment, or troubleshooting?

Use [Booking Overview](integration-guides/booking-overview/) for the main flow, [Payment & Ticketing](readme/booking-overview/payment-and-ticketing/) for payment and polling, and [Error Codes](troubleshooting-and-support/errors-handing/) for failure handling.

### Full change log

{% updates format="full" %}
{% update date="2026-06-09" %}
## Updated SeatAvailability call rules

Updated seat-selection documentation to reflect the latest `seatAvailability.do` requirements.

What changed:

* independent mode is no longer available
* use `sessionId` from `verify.do` or `OfferId` from `getOffers.do`
* flight-only seat quote requests are not supported

Updated pages:

* [Inflow Seat & Baggage](api-reference/booking-apis/inflow-seat-and-baggage.md)
* [Seats & Baggage](integration-guides/booking-overview/seats-and-baggage.md)
* [Verify](integration-guides/booking-overview/verify.md)
* [Get Offer](integration-guides/booking-overview/get-offer.md)
* [Booking Overview](integration-guides/booking-overview/)
* [Search & Booking](troubleshooting-and-support/faqs/atlas-api-search-and-book.md)
{% endupdate %}

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
