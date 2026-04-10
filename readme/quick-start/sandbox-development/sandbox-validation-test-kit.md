---
description: >-
  Run a no-code happy path check to confirm sandbox credentials, network access,
  and core booking flow readiness.
---

# Sandbox Validation Test Kit

Use this page to validate your sandbox setup before development starts.

This check does not require any custom code.

It confirms that your credentials and network can complete the core booking flow.

### What this validates

The test kit runs the standard happy path in sandbox.

| Step     | What is checked                                     |
| -------- | --------------------------------------------------- |
| `Search` | Your credentials are valid and flights are returned |
| `Verify` | Price confirmation works and a session is created   |
| `Order`  | The order can be created successfully               |
| `Pay`    | Payment is accepted                                 |

If all four steps pass, your sandbox environment is ready for integration work.

### When to use it

Run this test:

* after you receive sandbox credentials
* before you start coding
* after network or IP changes
* when you want a quick environment health check

### Download the test kit

Use these files:

* `Atlas_UAT_HappyPath.postman_collection.json`

{% file src="../../../.gitbook/assets/Atlas_UAT_HappyPath.postman_collection.json" %}

* `Atlas_UAT_Environment.json`

{% file src="../../../.gitbook/assets/Atlas_UAT_Environment.json" %}

Download both files to the same local folder.

### How to run

{% stepper %}
{% step %}
### Fill in the environment file

Open `Atlas_UAT_Environment.json`.

Set:

* `client_id`
* `client_secret`
* `currency`
* `from_date`

Use `USD` for `currency` unless your test case requires a different value.

Update `from_date` to a future date before you run the collection.
{% endstep %}

{% step %}
### Install Newman

Install Newman and the HTML reporter.

{% code title="Install Newman" %}
```bash
npm install -g newman newman-reporter-htmlextra
```
{% endcode %}
{% endstep %}

{% step %}
### Run the collection

Run the happy path collection with the environment file.

{% code title="Run the test kit" %}
```bash
newman run Atlas_UAT_HappyPath.postman_collection.json -e Atlas_UAT_Environment.json --delay-request 10000 --reporters htmlextra --reporter-htmlextra-export report.html
```
{% endcode %}

If the command fails, run it with `npx` instead.

{% code title="Fallback with npx" %}
```bash
npx newman run Atlas_UAT_HappyPath.postman_collection.json -e Atlas_UAT_Environment.json --delay-request 10000 --reporters htmlextra --reporter-htmlextra-export report.html
```
{% endcode %}
{% endstep %}

{% step %}
### Review the result

Open `report.html` after the run completes.

Expected runtime is about 2 to 3 minutes.
{% endstep %}
{% endstepper %}

### Expected result

Your sandbox setup is ready when:

* `Search` passes
* `Verify` passes
* `Order` passes
* `Pay` passes

You can treat this as a sandbox go signal.

Move on to API integration after these checks pass.

### Known behavior

The final retrieve step may time out while polling for ticket issuance.

This is expected.

Ticketing is asynchronous.

A timeout on the final retrieve step does not affect sandbox environment validation.

{% hint style="info" %}
Focus on the four core steps: `Search`, `Verify`, `Order`, and `Pay`.

The final retrieve polling step is informational only.
{% endhint %}

### Common failure reasons

If the run fails early, check these items first:

* `client_id` or `client_secret` is missing or incorrect
* the wrong environment file is selected
* outbound network access is blocked
* the request source IP changed after allowlisting
* the collection or environment file name was changed locally
* Newman is installed but the reporter package is missing

#### Quick checks

Use this order:

1. confirm the credentials in the environment file
2. confirm the sandbox endpoint values
3. confirm your network can reach Atlas
4. rerun the collection without editing the request sequence
5. open `report.html` and check the first failed request

{% hint style="warning" %}
If `Search` fails, fix credentials or network first.

Do not continue to integration work until the happy path passes.
{% endhint %}

### What to do after it passes

After the test kit passes:

* start the API integration
* keep the same sandbox credentials for development
* continue with [Sandbox Development](../../../integration-guides/quick-start/sandbox-development.md)
