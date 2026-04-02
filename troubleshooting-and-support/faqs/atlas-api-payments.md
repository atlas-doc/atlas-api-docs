---
description: >-
  Common payment questions about deposit, VCC, card data, and payment
  limitations.
---

# Payments

Use this page for payment mode, VCC, and card data questions.

### Which payment methods does Atlas support?

The main options are:

* **Deposit**
* **VCC pass-through**

Supported options still depend on airline and ticketing channel.

### How does VCC pass-through work?

Send card details in the `pay.do` request.\
Atlas passes the card data to the airline.\
The airline charges you directly.\
Atlas then deducts the technical service fee from your Atlas account.

Check payment support in the search or verification response before you build the payment flow.

### Does Atlas issue VCC cards?

No.\
Atlas supports VCC pass-through only.

You provide the card details in `pay.do`.

### Where do refunds go for each payment mode?

For **VCC**, refunded funds usually return to the original card.\
For **deposit**, Atlas credits your balance after airline funds are received.

### Why is VCC pass-through unavailable on some mixed-airline bookings?

Atlas does not support multiple VCCs in one `pay.do` request.

When outbound and inbound segments require different ticketing channels, two separate payments may be needed.\
If Atlas cannot support that split in one payment flow, the payment mode falls back to **deposit**.

### When is cardholder address data required?

Some airlines require full billing address details.\
Use the matrix below when you send VCC or card-based payments.

Cardholder country, province, city, postcode and address are required only for a select few airlines as per the table provided below:

| Airline Code | Airline Name                       | cardHolderCountry | cardHoldProvince | cardHolderCity | cardHolderPostCode | cardHolderAddress |
| ------------ | ---------------------------------- | ----------------- | ---------------- | -------------- | ------------------ | ----------------- |
| 4N           | Air North                          | Required          | Required         | Required       | Required           | Required          |
| 5J           | Cebu Pacific Air                   | Required          | Required         | Required       | Required           | Required          |
| 8P           | Pacific Coastal                    | Required          | Required         | Not Required   | Required           | Required          |
| 9M           | Central Mountain Air               | Required          | Required         | Not Required   | Required           | Required          |
| A3           | Aegean Airlines                    | Required          | Required         | Required       | Required           | Required          |
| AN           | Advanced Airlines                  | Required          | Required         | Required       | Required           | Required          |
| AS           | Alaska Airlines                    | Not Required      | Required         | Required       | Required           | Required          |
| BT           | Air Baltic                         | Required          | Not Required     | Required       | Required           | Required          |
| BV           | TOKI AIR                           | Required          | Required         | Required       | Required           | Required          |
| D8           | Norwegian Air Sweden               | Required          | Not Required     | Required       | Required           | Required          |
| DE           | Condor                             | Not Required      | Not Required     | Required       | Not Required       | Not Required      |
| DG           | Cebgo                              | Required          | Required         | Required       | Required           | Required          |
| DI           | Cebu Pacific Air                   | Not Required      | Not Required     | Required       | Not Required       | Not Required      |
| DM           | Arajet                             | Required          | Required         | Required       | Required           | Required          |
| DY           | Norwegian Air Shuttle ASA          | Not Required      | Required         | Required       | Required           | Required          |
| E6           | Eurowings Europe                   | Required          | Required         | Required       | Required           | Required          |
| EI           | Aer Lingus                         | Required          | Required         | Required       | Required           | Required          |
| EW           | Eurowings                          | Required          | Required         | Required       | Required           | Required          |
| F9           | Frontier Airlines (US Address)     | Required          | Not Required     | Required       | Required           | Required          |
| F9           | Frontier Airlines (Non-US Address) | Not Required      | Not Required     | Not Required   | Not Required       | Not Required      |
| FA           | Fly Safair                         | Required          | Required         | Required       | Required           | Required          |
| G4           | Allegiant Air                      | Required          | Required         | Required       | Required           | Required          |
| GE           | Lift Airline                       | Required          | Required         | Required       | Required           | Required          |
| GQ           | Skyexpress                         | Required          | Required         | Required       | Required           | Required          |
| H4           | HiSky                              | Required          | Not Required     | Not Required   | Not Required       | Not Required      |
| H7           | HiSky                              | Required          | Not Required     | Not Required   | Not Required       | Not Required      |
| JV           | Perimeter                          | Required          | Required         | Required       | Not Required       | Not Required      |
| KM           | AirMalta                           | Required          | Not Required     | Required       | Not Required       | Required          |
| LJ           | Jin Air                            | Required          | Required         | Not Required   | Required           | Required          |
| MM           | Peach Aviation                     | Not Required      | Not Required     | Required       | Required           | Required          |
| MO           | Calm Air                           | Not Required      | Not Required     | Not Required   | Not Required       | Required          |
| NK           | Spirit Airlines                    | Required          | Required         | Required       | Required           | Required          |
| OA           | Olympic Air                        | Required          | Required         | Required       | Required           | Required          |
| OG           | PLAY                               | Required          | Required         | Required       | Required           | Required          |
| P6           | Pascan                             | Required          | Required         | Required       | Required           | Required          |
| PB           | PAL Airlines                       | Required          | Required         | Required       | Required           | Required          |
| RW           | Royal Air Philippines              | Not Required      | Not Required     | Not Required   | Not Required       | Required          |
| SY           | Sun Country Airlines               | Required          | Required         | Required       | Required           | Required          |
| TR           | Scoot Tiger Air                    | Required          | Not Required     | Required       | Required           | Required          |
| VY           | Vueling Airlines                   | Required          | Not Required     | Required       | Required           | Required          |

### Related pages

* [Payment & Ticketing](../../readme/booking-overview/payment-and-ticketing/)
* [Error Codes](../errors-handing/)
* [Finance](atlas-api-finance.md)
