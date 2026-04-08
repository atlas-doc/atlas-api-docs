---
description: Track recent documentation updates and newly published guides.
---

# 📣 What's New

{% include ".gitbook/includes/eva-help-hint.md" %}

Check this page first for recent documentation updates.

{% hint style="success" %}
Latest update: [Error Codes](troubleshooting-and-support/errors-handing/) now includes retry guidance and a quick decision table.
{% endhint %}

### Latest highlight

#### Error Codes landing page update

Updated the main [Error Codes](troubleshooting-and-support/errors-handing/) entry page.

Use it when you need to:

* decide whether an error is safe to retry
* quickly identify high-risk no-retry cases
* route to the correct error section by flow
* check common next actions for search, verify, order, payment, query, and refund failures

### Change log

{% updates format="full" %}
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
