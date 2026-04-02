---
description: >-
  High-frequency shared errors for authentication, request format, and account
  access.
---

# Common & Access Errors

Use this page when a request fails before business processing starts.

### What this page covers

* Missing fields
* Invalid request format
* Credential and access failures
* Generic system errors

### Common codes

#### `100` Missing required request data

A mandatory field is missing.

**Action**

* Check required parameters
* Rebuild the request body
* Retry after validation

#### `900` Unauthorized access

Credentials are wrong, account status is invalid, or the request targets data outside your scope.

**Action**

* Check `x-atlas-client-id`
* Check `x-atlas-client-secret`
* Confirm the account is active

#### `901` Illegal request data

The request format is invalid.

**Action**

* Send JSON
* Check field types and nesting
* Validate required structure before retry

#### `902` Access denied

The request is blocked due to permission or account scope.

**Action**

* Re-check credentials
* Confirm the account can access this capability
* Contact Atlas if the request should be allowed

#### `9999` System error

Unexpected platform-side failure.

**Action**

* Retry once
* If it repeats, capture request IDs and escalate

#### `-1` Common error

Fallback error used when a more specific code is not returned.

**Action**

* Check the request context
* Retry if transient
* Escalate if repeated

### Recommended troubleshooting order

1. Confirm credentials and account status
2. Validate JSON format and required fields
3. Retry once for transient failures
4. Escalate with request context if the error repeats

### Related pages

* [Authentication & Request Basics](../../integration-guides/quick-start/making-requests.md)
* [Help & Support](../)
