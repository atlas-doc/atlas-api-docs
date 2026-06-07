---
description: >-
  Atlas API UAT validation guide for templates, execution scope, evidence,
  submission, and approval before go-live.
---

# UAT Validation

{% include "../../.gitbook/includes/eva-help-hint.md" %}

Use this page when your sandbox integration is ready for go-live validation.

Start here when you need to:

* choose the correct UAT track
* prepare the right evidence before submission
* understand what must be approved before go-live

### FAQ

#### When should we start UAT?

Start UAT only after the sandbox flow is stable end to end.

Your team should be able to run the required test scenarios reliably before formal submission.

#### What does UAT approval prove?

It proves the validated sandbox integration is ready for production transition.

It does not replace the production credential switch or go-live monitoring steps.

### Goal of this phase

Validate that the sandbox integration is ready for production.

This phase converts a completed sandbox integration into an approved go-live result.

### When to start UAT

Start UAT after:

* sandbox credentials are working
* the core booking flow is integrated
* request headers and authentication are stable
* webhook handling is ready if full integration UAT is required
* your team can execute test cases end to end

{% hint style="info" %}
Before UAT, run the [Sandbox Validation Test Kit](../../readme/quick-start/sandbox-development/sandbox-validation-test-kit.md).

Use it to confirm credentials, network access, and the basic booking path before formal validation starts.
{% endhint %}

### UAT tracks

There are two UAT tracks.

#### 1. Shopping and Ticketing UAT

Use this track when you need to validate the standard search-to-ticket flow.

This usually covers:

* search
* verify
* order
* payment
* ticketing result

#### 2. Full Integration UAT

Use this track when you need to validate the end-to-end integration between Atlas and your booking platform.

This usually covers:

* passenger type combinations
* trip type combinations
* direct and connecting itineraries
* payment methods
* ancillaries
* webhooks
* operational follow-up flows

### How do you choose the right UAT track?

Use **Shopping and Ticketing UAT** for the standard search-to-ticket path.

Use **Full Integration UAT** when you need broader coverage across passenger combinations, trip types, ancillaries, webhook handling, and operational follow-up.

### What to prepare before submission

Prepare these items before submitting UAT:

* completed UAT template
* test evidence for each scenario
* expected and actual results
* relevant order numbers or request IDs
* webhook evidence when full integration is tested
* the Postman collection used by your team, if needed

### Best practice

Record expected and actual results clearly for every scenario.

Keep order numbers, request IDs, screenshots, and webhook samples linked to the same test case.

### Recommended execution order

{% stepper %}
{% step %}
### Download the correct template

Pick the UAT track that matches your integration scope.
{% endstep %}

{% step %}
### Run all required scenarios

Execute every scenario in sandbox and record the result clearly.
{% endstep %}

{% step %}
### Attach evidence

Include request outcomes, screenshots, webhook samples, and order references where relevant.
{% endstep %}

{% step %}
### Submit via ATRIP

Submit the completed UAT result through Eva in ATRIP.
{% endstep %}

{% step %}
### Wait for review feedback

Atlas reviews the submission and may request clarification or retesting.
{% endstep %}
{% endstepper %}

### Download resources

#### Shopping and Ticketing UAT template

{% file src="../../.gitbook/assets/Atlas UAT Test Shopping & Ticketing Services Only Template.xlsx" %}

#### Shopping and Ticketing Postman collection

{% file src="../../.gitbook/assets/Atlas UAT Test Shopping & Ticketing Services Only Postman Collection.zip" %}

#### Full Integration UAT template

{% file src="../../.gitbook/assets/Atlas UAT Test Full Integration Template.xlsx" %}

#### Full Integration Postman collection

{% file src="../../.gitbook/assets/Atlas UAT Test Full Integration Postman Collection 20230424 (1).zip" %}

### Submission path

After you complete the relevant template, submit the results through Eva in ATRIP.

![](<../../.gitbook/assets/image (3).png>) <mark style="color:$info;">**==>**</mark> ![](<../../.gitbook/assets/image (6).png>)

### Common reasons a submission is sent back

* missing scenarios
* incomplete expected or actual results
* no supporting evidence
* unclear passenger or trip type coverage
* webhook flow not demonstrated for full integration UAT

### What comes next?

After approval, continue with [Production Go-Live](production-go-live.md).

At that point, ask for `LIVE` status, generate production credentials, switch endpoints, and run a controlled smoke test.

### Complete this phase when

You have all of these:

* submitted the correct UAT track
* attached the required evidence
* resolved any review feedback
* received UAT approval

### Output of this phase

* approved UAT result
* confirmed go-live readiness

### Next step

After UAT passes:

* ask your customer manager to switch the account to `LIVE`
* generate production credentials
* set up the production IP whitelist
* replace sandbox endpoints
* run a controlled smoke test
* monitor the first live orders and webhook events

### Related pages

* [Sandbox Development](sandbox-development.md)
* [Sandbox Validation Test Kit](../../readme/quick-start/sandbox-development/sandbox-validation-test-kit.md)
* [Quick Start](./)
* [Production Go-Live](production-go-live.md)
* [Webhook Overview](../webhook-overview/)
