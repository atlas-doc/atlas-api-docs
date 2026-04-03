# Get Offer

{% include "../../.gitbook/includes/eva-help-hint.md" %}

Use this page for the endpoint details of the independent Get Offer flow.

{% hint style="info" %}
Use OpenAPI naming as the source of truth.

Use `getOffers.do` in implementation and documentation.
{% endhint %}

### Main API

* `getOffers.do`

### Use this when you need

* An offer lookup flow without standard search
* A real-time price check before order creation
* A lowest-price validation step before ticketing

### Best practice

* use `getOffers.do` when the target itinerary is already known
* keep the returned `OfferId` for downstream order creation
* refresh the offer if passenger mix, flight choice, or expected fare changes
* use `order.do` and `pay.do` as the standard downstream path
* query `getLuggage.do` or `seatAvailability.do` only when ancillaries matter before booking

### Related pages

* [Get Offer](../../integration-guides/booking-overview/get-offer.md)
* [Create Order](../../integration-guides/booking-overview/create-order.md)
* [Payment & Ticketing](../../readme/booking-overview/payment-and-ticketing/)
* [Search & Booking](../../troubleshooting-and-support/faqs/atlas-api-search-and-book.md)

{% openapi-operation spec="atlas-api" path="/getOffers.do" method="post" %}
[OpenAPI atlas-api](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/16d5f2d8196b3ef49a60acb409c448368fd1ff7b7e7d5d750ed7be17dd37bd3c.json?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20260403%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20260403T063739Z&X-Amz-Expires=172800&X-Amz-Signature=ffcf8f1d037929998378f4094a872aa8e18426ffc498a92505bcca93f8bfb6db&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}
