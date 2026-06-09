# Inflow Seat & Baggage

{% include "../../.gitbook/includes/eva-help-hint.md" %}

{% hint style="warning" %}
`seatAvailability.do` no longer supports independent mode.

Call it only with a valid `sessionId` from `verify.do` or `OfferId` from `getOffers.do`.

Do not call it with flight data alone.
{% endhint %}

### SeatAvailability call rules

Use `seatAvailability.do` only inside a valid booking chain.

Supported request context:

* `sessionId` returned by `verify.do`
* `OfferId` returned by `getOffers.do`

Unsupported request context:

* flight information alone

### Regional handling

#### Global customers

Keep the current flow.

Use `sessionId` or `OfferId` as before.

#### China OTA scenarios

Some upstream seat requests contain only flight information.

For this case, keep the `sessionId` returned by `verify.do`.

When the seat request arrives, match the flight to the cached `sessionId`.

If the match succeeds, call `seatAvailability.do` with that `sessionId`.

If no match exists, treat it as a pure quote request.

Atlas does not support that case.

### Why this changed

This rule keeps seat pricing and fulfillment aligned with the real booking chain.

It also reduces invalid airline-side queries.

{% openapi-operation spec="atlas-api" path="/seatAvailability.do" method="post" %}
[OpenAPI atlas-api](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/16d5f2d8196b3ef49a60acb409c448368fd1ff7b7e7d5d750ed7be17dd37bd3c.json?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260609%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260609T013804Z&X-Amz-Expires=172800&X-Amz-Signature=1acc44fc61c40d1bd7a0764ad0093f79eae4e845c1354df2eaa5dceffc9a0d49&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

{% openapi-operation spec="atlas-api" path="/getLuggage.do" method="post" %}
[OpenAPI atlas-api](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/16d5f2d8196b3ef49a60acb409c448368fd1ff7b7e7d5d750ed7be17dd37bd3c.json?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260609%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260609T013804Z&X-Amz-Expires=172800&X-Amz-Signature=1acc44fc61c40d1bd7a0764ad0093f79eae4e845c1354df2eaa5dceffc9a0d49&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}
