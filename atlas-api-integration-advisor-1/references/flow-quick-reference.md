# flow quick reference

Quick reference of the key endpoints used in each booking flow.

{% hint style="info" %}
📖 **For complete ancillary service guidance (prerequisites, response parsing, data chaining to order.do), see SKILL.md §8b — Ancillary Services.**

📖 **For post-booking flows, see SKILL.md §9c — Post-Booking.**
{% endhint %}

***

## Flow A: Search → Verify → Order → Pay

{% stepper %}
{% step %}
## search.do — Search Flights

```
POST {base}/search.do
Headers: x-atlas-client-id, x-atlas-client-secret, Accept-Encoding: gzip
```

```json
{
    "tripType": "1",
    "adultNum": 1,
    "childNum": 0,
    "infantNum": 0,
    "fromCity": "STN",
    "toCity": "ALC",
    "fromDate": "20261018",
    "airlines": ["LS"]
}
```
{% endstep %}

{% step %}
## verify.do — Verify Price

```
POST {base}/verify.do
```

```json
{
    "routingIdentifier": "<from search response>"
}
```
{% endstep %}

{% step %}
## \[Optional] getLuggage.do — Query Baggage

```
POST {base}/getLuggage.do
```

```json
{"offerId": "<sessionId from verify>"}
```
{% endstep %}

{% step %}
## \[Optional] seatAvailability.do — Query Seat Map

```
POST {base}/seatAvailability.do
```

```json
{
    "sessionId": "<sessionId from verify>",
    "carrier": "LS",
    "outboundSegments": [{
        "flightNumber": "LS1411",
        "segmentIndex": 1,
        "depAirport": "STN",
        "arrAirport": "ALC",
        "cabinClass": "1",
        "depTime": "202610180835"
    }]
}
```
{% endstep %}

{% step %}
## order.do — Create Booking

```
POST {base}/order.do
```

```json
{
    "sessionId": "<sessionId from verify>",
    "passengers": [{
        "name": "LastName/GivenName",
        "passengerType": 0,
        "birthday": "20050606",
        "gender": "F",
        "nationality": "GB",
        "ancillaries": [
            {"productCode": "<baggage_or_seat_code>", "segmentIndex": 1}
        ]
    }],
    "contact": {
        "name": "LastName/GivenName",
        "email": "test@example.com",
        "mobile": "0086-13928109091"
    }
}
```
{% endstep %}

{% step %}
## \[FR only] orderCommit.do

```
POST {base}/orderCommit.do
```
{% endstep %}

{% step %}
## pay.do — Payment

```
POST {base}/pay.do
```

```json
{
    "orderNo": "<from order.do>",
    "paymentMethod": 1
}
```
{% endstep %}

{% step %}
## queryOrderDetails.do — Check Status

```
POST {base}/queryOrderDetails.do
```

```json
{"orderNo": "<from order.do>"}
```
{% endstep %}
{% endstepper %}

***

## Flow B: GetOffer → Order → Pay

{% stepper %}
{% step %}
## getOffers.do — Get Price Quote

```
POST {base}/getOffers.do
```
{% endstep %}

{% step %}
## \[Optional] getLuggage.do — using offerId

```
POST {base}/getLuggage.do
Body: {"offerId": "<offerId from getOffers>"}
```
{% endstep %}

{% step %}
## \[Optional] seatAvailability.do — using offerId

```
POST {base}/seatAvailability.do
Body: (same as Flow A but use "offerId" instead of "sessionId")
```
{% endstep %}

{% step %}
## order.do — using offerId

```
POST {base}/order.do
Body: {"offerId": "<offerId from getOffers>", "passengers": [...], "contact": {...}}
```
{% endstep %}

{% step %}
## pay.do — Payment

```
POST {base}/pay.do
Body: (same as Flow A)
```
{% endstep %}
{% endstepper %}

***

## Price Compare (NOT a booking flow)

```
POST {base}/priceCompareSearch.do
```

Same request format as `search.do`. Returns routing data for comparison only. **Do NOT use for production booking.**

***

## Post-Booking Quick Reference

### Post-Booking Ancillary

{% stepper %}
{% step %}
## Search available ancillaries

```
POST {base}/postBookingAncillarySearch.do
Body: {"ticketOrderNo": "<orderNo>", "ancillaryCategory": "BAGGAGE"}
```
{% endstep %}

{% step %}
## Submit ancillary order

```
POST {base}/postBookingAncillaryOrder.do
Body: {
    "sessionId": "<sessionId>",
    "ticketOrderNo": "<orderNo>",
    "passengers": [{"name": "...", "passengerType": 0, "ancillaries": [...]}]
}
```
{% endstep %}
{% endstepper %}

### Refund

{% stepper %}
{% step %}
## Query refund rules

```
POST {base}/queryRefundRules.do
Body: {"orderNo": "<orderNo>"}
```
{% endstep %}

{% step %}
## Submit refund

```
POST {base}/refund.do
Body: {"orderNo": "<orderNo>", "passengers": [...], "refundReason": "..."}
```
{% endstep %}

{% step %}
## Query refund status

```
POST {base}/queryRefundStatus.do
Body: {"orderNo": "<orderNo>"}
```
{% endstep %}
{% endstepper %}

### Void

{% stepper %}
{% step %}
## Query void status

```
POST {base}/queryVoidOrders.do
Body: {"orderNo": "<orderNo>"}
```
{% endstep %}

{% step %}
## Execute void

```
POST {base}/voidOrder.do
Body: {"orderNo": "<orderNo>"}
```
{% endstep %}
{% endstepper %}

### Cancel Order

```
POST {base}/cancelOrder.do
Body: {"orderNo": "<orderNo>"}
```

***

## Data Chaining Summary

```
search.do ────── routingIdentifier ──────→ verify.do ── sessionId ──┐
                                                                     │
priceCompareSearch.do ── fid/routingIdentifier ──→ order.do (no verify) ──→ pay.do
                                                                     │
getOffers.do ────────── offerId ─────────────────→ order.do ─────────→ pay.do
                                                                    │
                                              sessionId/offerId ────┤
                                              (for luggage/seat)     │
                                                                    │
                                                              post-booking
                                                              ancillary APIs
```
