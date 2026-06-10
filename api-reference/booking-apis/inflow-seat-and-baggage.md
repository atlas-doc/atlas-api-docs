# Seat

{% include "../../.gitbook/includes/eva-help-hint.md" %}

Use this page for the endpoint details of inflow seat lookup.

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

### Related page

For baggage endpoint details, use [Baggage](baggage.md).

{% openapi-operation spec="atlas-api" path="/seatAvailability.do" method="post" %}
[OpenAPI atlas-api](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/4edb8a3042d0894360cf76978724aeb9cb325bfe857f4e134d8c0e87ae544be6.json?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260610%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260610T121514Z&X-Amz-Expires=172800&X-Amz-Signature=7f497d4a79494dc8574074bfa7f80943ac77e4a66aeb747c949bb06c0b6f0698&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}
