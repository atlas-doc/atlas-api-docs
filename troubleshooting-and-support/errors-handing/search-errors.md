---
description: >-
  Common search-stage errors for request limits, route restrictions, search
  timeout, and unsupported conditions.
---

# Search Errors

{% include "../../.gitbook/includes/eva-help-hint.md" %}

Use this page when `search.do`, `smartSearch.do`, or `getOffers.do` fails.

### Highest-frequency codes

#### `102` Illegal request param

One or more search fields are invalid.

**Typical causes**

* No adult passenger
* Too many passengers
* Invalid city code
* Missing `fromDate` or `retDate`
* Bad date format

**Action**

* Validate trip type
* Validate passenger counts
* Validate city and airport codes
* Use `YYYYMMDD` for dates

#### `107` Insufficient balance

Account balance is below the required threshold.

**Action**

* Top up the account
* Re-run the search after balance is updated

#### `108` Route restricted / system limitations

Atlas has closed sales for this route or flow.

**Action**

* Retry later
* Check with Atlas if this route should be available

#### `110` Too many concurrent requests

Search QPS is above the allowed limit.

**Action**

* Throttle request bursts
* Add retry and queue control
* Contact Atlas if higher throughput is required

#### `112` or `127` Search timeout

The search did not complete in time.

**Action**

* Retry the search
* Reduce burst load
* Use smart search or polling when applicable

#### `123` Too many requests but too few paid orders

Search volume is high compared to paid orders.

**Action**

* Reduce unnecessary search traffic
* Avoid synthetic or duplicate search bursts

#### `124` Unsupported settlement currency

The currency is not allowed for settlement.

**Action**

* Switch to the account settlement currency

#### `126` `requestId` does not exist or has already ended

The smart search `requestId` is invalid or expired.

**Action**

* Start a new smart search
* Use the new `requestId`

### Quick troubleshooting checklist

1. Validate required fields and date format
2. Check balance and settlement currency
3. Confirm the route is supported
4. Check concurrency and retry behavior
5. Re-run smart search if `requestId` expired

### Related pages

* [Search](../../integration-guides/booking-overview/search.md)
* [Booking APIs](../../api-reference/booking-apis/)
* [Finance](../faqs/atlas-api-finance.md)
