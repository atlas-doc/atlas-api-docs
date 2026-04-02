---
description: >-
  Common onboarding questions about coverage, access, pricing, performance, and
  escalation.
---

# Getting Started

Use this page for commercial, onboarding, performance, and support basics.

### Which airlines can we sell through Atlas?

Atlas connects to 150+ airlines.\
You can review the current list on the [airline list](https://www.atriptech.com/#/airline/list) and in ATRIP.

### Can we test before signing?

Yes. Submit the [get started form](https://atlaslovestravel.com/get-started/).\
Atlas will review your company, complete NDA steps, and then issue test credentials.

### Where do we get sandbox credentials?

Generate them in ATRIP under `Profile` → `My Profile` → `Company Information`.\
Use `x-atlas-client-id` and `x-atlas-client-secret` on every sandbox call.

### Is there a Postman collection for first tests?

Yes.\
Use the Postman collection in [Quick Start](../../integration-guides/quick-start/).

Use the UAT collections when you prepare validation evidence.

### How do we start UAT?

Start UAT only after the sandbox flow is stable end to end.\
Pick the correct UAT track, complete the template, attach evidence, and submit through Eva in ATRIP.

### Are airline capabilities always the same?

No. Capability depends on what each airline supports.\
Atlas exposes supported functions per airline and flow.

### How is Atlas priced?

Pricing depends on market, currency, and commercial terms.\
Use the [contact form](https://atlaslovestravel.com/contact/) to get local pricing details.

### Does Atlas support promo fares or promo codes?

General promotional fare support is available.\
Promo code support is planned, but not generally available yet.

### What is the L2B ratio?

The look-to-book ratio is defined in your commercial agreement.

### Does Atlas use cache?

Yes. Atlas uses a shared cache pool for search traffic.\
Client-specific cache can also be supported.

### What should we do during API failure?

Use support channels for immediate help.\
Atlas also plans a fallback portal for booking, ticketing, and post-booking operations.

### Does Atlas provide fare guarantee?

Yes, after payment is completed in **deposit** mode.\
Ticketing usually completes within 10 minutes.\
Rare cases can take up to 1 hour.

Fare guarantee does **not** apply to VCC pass-through payments.

### What are the standard timeout limits?

* `search.do`: not fixed
* `realTimeSearch.do`: `120s`
* `verify.do`: `15s`
* `order.do`: `15s` for normal booking, `120s` for real-time booking
* `pay.do`: not fixed

### What are the typical response times?

* `search.do`: under `500ms` for 98% of responses
* `verify.do`: about `8s` for 95% of responses
* `order.do`: about `14s` for 95% of responses
* `pay.do`: about `2s` for 95% of responses

### How do we escalate unresolved issues?

Escalations can be sent to **customerfeedback@atlaslovestravel.com**.

Use this for unresolved service issues related to:

* ticket orders
* post-booking operations
* refunds

Atlas may first ask you to open or reference a Service Request in ATRIP.
