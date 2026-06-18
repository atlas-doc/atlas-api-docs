# integration scenarios

This reference helps identify which integration scenario a client fits into and provides sandbox test routes for each.

## 1. Client Scenario Identification

| Scenario             | Client Type           |               Recommended Flow              | Key Characteristics                                                                 |
| -------------------- | --------------------- | :-----------------------------------------: | ----------------------------------------------------------------------------------- |
| **Full Booking OTA** | Online Travel Agency  |       Flow A (Search→Verify→Order→Pay)      | Atlas is primary shopping source; needs full flight display + booking + ancillaries |
| **Get Offer Booker** | TMC / Aggregator      |         Flow B (GetOffer→Order→Pay)         | Has own flight data; needs Atlas for price confirmation & booking only              |
| **Price Comparison** | Flight Deck / Blogger | priceCompareSearch.do **only** (NO booking) | Only needs fare discovery; no ticketing required                                    |
| **Ancillary Only**   | Post-booking service  |       postBookingAncillarySearch→Order      | Already has ticketed orders; wants to add baggage post-ticketing                    |
| **Hybrid**           | Multi-channel client  |             Both Flow A + Flow B            | Uses search for some routes, getOffer for others                                    |

## 2. Sandbox Test Routes

### Flow A Test: Standard Search → Verify → Order → Pay

{% hint style="info" %}
Use future dates (at least 7 days from today). The dates below are **examples** — adjust the year/month/day to be a valid future date. Dates >= 45 days out are preferred for wider availability.
{% endhint %}

| Airline               | Route   | Example Date | Trip Type | Notes                                     |
| --------------------- | ------- | :----------: | :-------: | ----------------------------------------- |
| LS (Jet2)             | STN→ALC |  2026-09-15  |  One-way  | Good for testing seat selection + baggage |
| VY (Vueling)          | LON→BCN |  2026-09-20  |  One-way  | Budget carrier, varied fare families      |
| G4 (Allegiant)        | LAS→MEM |  2026-10-01  |  One-way  | US domestic LCC                           |
| A3 (Aegean)           | TLS→CAI |  2026-09-10  |  One-way  | Full-service carrier                      |
| 3U (Sichuan Airlines) | CAN→TFU |  2026-09-25  |  One-way  | Chinese domestic carrier                  |

### Quick Test Commands (for developer reference)

When a client asks for the fastest way to verify connectivity, provide a curl example:

```bash
# Quick ping test: search LS STN→ALC
curl -s -X POST "https://sandbox.atriptech.com/search.do" \
  -H "Content-Type: application/json" \
  -H "x-atlas-client-id: <sandbox_id>" \
  -H "x-atlas-client-secret: test" \
  -H "Accept-Encoding: gzip" \
  -H "Accept: application/json" \
  -d '{"tripType":"1","adultNum":1,"fromCity":"STN","toCity":"ALC","fromDate":"20260915","airlines":["LS"]}'
```

### Flow B Test: GetOffer → Order → Pay

| Airline                 | Route                   | Date   | Notes                                       |
| ----------------------- | ----------------------- | ------ | ------------------------------------------- |
| Same airlines as Flow A | Any known flight number | future | Call getOffers.do with specific flight info |

### FR (Ryanair) Special Flow Test

| Airline | Route   | Date   | Notes                                         |
| ------- | ------- | ------ | --------------------------------------------- |
| FR      | DUB→LON | future | FR requires `orderCommit.do` + `locale` field |
| FR      | STN→ALC | future | FR test; requires proper locale setting       |

## 3. Test Credentials

| Environment    | Base URL                        | Notes                                   |
| -------------- | ------------------------------- | --------------------------------------- |
| **Sandbox**    | `https://sandbox.atriptech.com` | Sandbox credential and `test` as secret |
| **Production** | Two URLs from ATRIP             | One for search, another for other APIs  |

Sandbox credentials are generated at: ATRIP Portal → Profile → My Profile → Company Information

## 4. Testing Checklist by Scenario

### Full Booking (Flow A)

* [ ] search.do returns results with routingIdentifier
* [ ] verify.do returns valid sessionId
* [ ] getLuggage.do returns baggage options (if applicable)
* [ ] seatAvailability.do returns seat map (if applicable)
* [ ] order.do creates order successfully (returns orderNo)
* [ ] pay.do completes payment
* [ ] queryOrderDetails.do confirms ticketed status

### Get Offer Booker (Flow B)

* [ ] getOffers.do returns offerId
* [ ] getLuggage.do using offerId returns baggage options
* [ ] seatAvailability.do using offerId returns seat map
* [ ] order.do with offerId creates order
* [ ] pay.do completes payment

### FR Specific

* [ ] orderCommit.do succeeds between order and pay
* [ ] locale parameter correctly set
