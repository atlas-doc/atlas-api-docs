---
description: >-
  Atlas API utility overview for balance checks, email query, route export, and
  ATRIP token generation.
---

# Utility API Overview

{% include "../../.gitbook/includes/eva-help-hint.md" %}

Use this section for non-transactional APIs used by operations teams.

Start here when you need to:

* check balance or finance-related status
* query operational email records
* export route data
* generate ATRIP access tokens

### FAQ

#### What are Atlas API utility APIs used for?

They support non-transactional workflows such as finance checks, email lookup, route export, and ATRIP access.

They are not part of the main search-to-ticket booking chain.

#### Which utility page should I open first?

Use **Balance** for finance checks, **Email Query** for captured email lookup, **Route Export** for route data extraction, and **ATRIP Token** for token generation.

### Pages in this section

* [Balance](balance.md)
* [Email Query](email-query.md)
* [Route Export](route-export.md)
* [ATRIP Token](atrip-token.md)

### What this section covers

* Balance and finance checks
* Email lookups for operational workflows
* Route exports for reporting
* ATRIP token generation

### Main APIs

* `balance.do`
* `route/export.do`
* `queryMail.do`
* `getAtripToken.do`

### Use this when you need

* Operations and finance workflows
* Export route data
* Query email records
* Access ATRIP with generated tokens

### What comes next?

After you identify the utility task, open the matching page in this section for the exact request and response details.

### Full API reference

Use endpoint-level details here:

[Utility APIs](../../api-reference/utility-apis/)

### Related pages

* [Integration Guides](<../../README (1).md>)
* [Post-booking Overview](../post-booking-overview/)
* [Webhook Overview](../webhook-overview/)
