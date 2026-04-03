---
description: Search APIs for flight offers, real-time search, and request polling.
---

# Search

{% include "../../.gitbook/includes/eva-help-hint.md" %}

Use this page to start the booking flow.

{% hint style="warning" %}
`Smart Search` (`smartSearch.do`) will be deprecated soon.

Do not use it for new integrations. Prefer the standard `search.do` flow.
{% endhint %}

### What this page covers

* Standard offer search
* Independent Get Offer lookup
* Advanced or smart search flows
* Offer polling and request follow-up

### Main APIs

* `search.do`
* `getOffers.do`
* `smartSearch.do`

### Key outputs

* `routingIdentifier` for standard verify flow
* `OfferId` for Get Offer order flow
* `requestId` for smart search follow-up
* Offer data for downstream selection

### Use this when you need

* A standard search-to-book flow
* An independent offer lookup without standard search
* Smart or asynchronous search behavior
* Offer refresh after smart search

### Related pages

* [Get Offer](get-offer.md)
* [Verify](verify.md)
* [Authentication & Request Basics](../quick-start/making-requests.md)
* [Booking APIs](../../api-reference/booking-apis/)

### Full API reference

See endpoint-level details here:

* [Search](../../api-reference/booking-apis/search.md)
* [Smart Search](../../api-reference/booking-apis/smart-search.md)
* [Get Offer](../../api-reference/booking-apis/get-offer.md)
