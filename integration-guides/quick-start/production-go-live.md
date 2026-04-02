---
description: >-
  Switch from sandbox integration to production credentials, endpoints, and live
  launch.
---

# Production Go-Live

Use this page when you are ready to move from sandbox to production.

### Goal of this phase

Move the integration from sandbox to production.

This is the final step in the overall onboarding flow.

### When to start

Start this step after:

* the required UAT work is complete
* your booking flow is stable
* webhook handling is ready
* your team can monitor the first live orders

Do not start production setup before your go-live checklist is ready.

You can generate production credentials only after UAT passes and your customer manager switches your account to `LIVE` status.

### What changes in production

Move these items from sandbox to production:

* credentials
* endpoints
* payment handling
* operational monitoring

Header rules stay the same.

Live bookings and payments are real transactions.

### Go-live checklist

{% stepper %}
{% step %}
### Confirm UAT completion

Make sure the required UAT work is complete and any remaining issues are closed.
{% endstep %}

{% step %}
### Wait for LIVE status

After UAT passes, your customer manager changes your account status to `LIVE`.

You cannot generate production credentials before this status update is complete.
{% endstep %}

{% step %}
### Generate production credentials

After your account is in `LIVE` status, generate the production client ID and client secret in ATRIP.

Set up your IP whitelist in the same production setup flow.

<figure><img src="../../.gitbook/assets/image (1).png" alt=""><figcaption><p>Production credential generation and IP whitelist setup in ATRIP</p></figcaption></figure>

Customers can generate these values directly only after the account is set to `LIVE`.
{% endstep %}

{% step %}
### Switch your environment

Replace sandbox credentials and sandbox endpoints in your server configuration.
{% endstep %}

{% step %}
### Run a controlled smoke test

Verify the first live API calls, webhook delivery, and ticketing follow-up.
{% endstep %}

{% step %}
### Monitor the first live orders

Track order status, payment results, and webhook events closely after launch.
{% endstep %}
{% endstepper %}

### Complete this phase when

You have all of these in production:

* working production credentials
* account status updated to `LIVE`
* correct production endpoints
* successful smoke test results
* monitored first live orders and webhooks

### Output of this phase

* production-ready environment
* live booking capability
* initial post-launch validation completed

### Important notes

* Do not use sandbox cards in production.
* Do not use sandbox fares for production checks.
* Keep production credentials server-side.
* Confirm that your production IP whitelist stays up to date.
* UAT completion alone does not unlock production credentials. Your customer manager must switch the account to `LIVE`.

### Related pages

* [Quick Start](./)
* [UAT Validation](uat-submission-guide.md)
* [Webhook Overview](../webhook-overview/)
