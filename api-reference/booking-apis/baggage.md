# Baggage

{% include "../../.gitbook/includes/eva-help-hint.md" %}

Use this page for the endpoint details of inflow baggage lookup.

### GetLuggage call rules

Use `getLuggage.do` inside a valid booking chain.

Supported request context:

* `sessionId` returned by `verify.do`, sent as `offerId`
* `OfferId` returned by `getOffers.do`

### What to do with the response

`getLuggage.do` returns baggage products for the current itinerary.

Each product has a `productCode`.

Use that `productCode` in `order.do` when baggage is selected.

### Notes

* query baggage after the target itinerary is confirmed
* keep baggage mapping consistent for the current booking context
* for connecting flights, keep baggage selection consistent across connected segments in the same direction

{% openapi-operation spec="atlas-api" path="/getLuggage.do" method="post" %}
[OpenAPI atlas-api](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/4edb8a3042d0894360cf76978724aeb9cb325bfe857f4e134d8c0e87ae544be6.json?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260610%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260610T121513Z&X-Amz-Expires=172800&X-Amz-Signature=338e34a37d0c35870a3f27fd479680c1e3c2d6419af0ad61cdf7e2510271e6ee&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}
