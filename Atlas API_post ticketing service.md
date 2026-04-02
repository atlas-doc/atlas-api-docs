---
title: Default module
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - ruby: Ruby
  - python: Python
  - php: PHP
  - java: Java
  - go: Go
toc_footers: []
includes: []
search: true
code_clipboard: true
highlight_theme: darkula
headingLevel: 2
generator: "@tarslib/widdershins v4.0.30"

---

# Default module

Base URLs:

# Authentication

# Post Ticketing Service

## POST Search Ancillary

POST /postBookingAncillarySearch.do

**Dependency:**
No preceding function needs to be carried out. The order should be ticketed and the departure date should be in the future.

> Please note the below "Rules & Restrictions" while initiating a post-ticketing transaction.
>   1. **Single Booking Limit**: Check-in baggage and Carry-on baggage can be added to the segment of passenger either in-booking or post-booking phase altogether or separately, but each type of baggage can only be added one time for the given segment throughout the whole flow. This rule aims to simplify the baggage booking flow for customers by sending the query only one time to book multiple baggages.
>   2. **Product Code**: "Product code" contains various baggage offerings in aspects of baggage pieces and weights for each airline.
>   3. **Restrictions for Infants**: Baggage ancillary is not allowed to be booked for infant passenger.
>   4. **Post-Booking Baggage Additions**: It is not allowed to add the same type of post-booking baggage to a ticketed order the second time unless the first purchase fails in payment. Please refer to the below scenarios:
>      a. When the post-booking order is in "ticket-in-process" and "ticketed" status, it's not allowed to order another one. If any query is called, API will respond with an error message.
>      b. When the post-booking order is in "cancelled" status, the customer can create another order.
>      c. When the post-booking order is in "unpaid" status, the customer can create another order. However, if one of the orders completes the payment and moves to "ticketing-in-process" status, the other orders will stop processing the payment.
>   5. **Existing Baggage Policies**: In case the air ticket order already contains free baggage, it’s subject to airline’s ancillary policy whether additional baggage is allowed to be purchase either at the booking flow or the post-booking flow.
>   6. **Consistent Product Codes in Connecting Flights**: Same “product code” for baggage is mandatory to be added to each segment in connecting flights. If the "product code" is different for each of the segment (in the same direction) or not added for all the sectors, the API will respond with an error message.
>   7. **Round-Trip Baggage Rule**: Rule No.6 doesn't work for round trip flights. This means that the outbound and inbound segments can have different product codes. For example, outbound journey may have a product code of 1PC and 10KG while the inbound journey may have a product code of 20KG. This is allowed.
>   8. **API Request Information**: The details of only the passenger for whom the ancillary needs to be added must be sent in the API RQ.

**Endpoint:**
https://sandbox.atriptech.com/postBookingAncillarySearch.do

> Body 请求参数

```json
{
  "ticketOrderNo": "TESTA20240618162411631",
  "ancillaryCategory": "BAGGAGE"
}
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|Accept|header|string| 是 |none|
|Content-Type|header|string| 是 |none|
|Accept-Encoding|header|string| 是 |none|
|x-atlas-client-id|header|string| 是 |none|
|x-atlas-client-secret|header|string| 是 |none|
|body|body|object| 否 |none|
|» ticketOrderNo|body|string¦null| 否 |Order number. It is the original order number.|
|» ancillaryCategory|body|string| 是 |Ancillary Category. Different categories of ancillaries need to be separately requested. Currently we only support`BAGGAGE`.|
|» paymentMethod|body|integer¦null| 否 |The payment method you prefer to use. If you specify a payment method (provided that the fare supports it), then you can only use that method for payment.|
|» fromSegments|body|[object]¦null| 否 |Outbound segments|
|»» carrier|body|string| 是 |IATA code of the marketing airline|
|»» flightNumber|body|string| 是 |The value denotes the marketing flight number.|
|»» depAirport|body|string| 是 |IATA code of the departure airport.|
|»» arrAirport|body|string| 是 |IATA code of the arrival airport.|
|»» depTime|body|string| 是 |Departure time of the flight. Format:`yyyyMMddHHmm`|
|»» arrTime|body|string¦null| 否 |Arrival time of the flight. Format:`yyyyMMddHHmm`|
|»» stopCities|body|string¦null| 否 |Name of cities from where the passengers will take connecting flights. Include IATA code of cities and use a comma in case of multiple cities to separate if transfer airports count is higher than 1. For example: CGK, SUB. Blank means non-stop flight.|
|»» codeShare|body|integer¦null| 否 |- 1: code share|
|»» operatingCarrier|body|string¦null| 否 |Operating carrier. It is blank when codeshare=false|
|»» operatingFlightNumber|body|string¦null| 否 |Operating flight number. It is blank when codeshare=false|
|»» depTerminal|body|string¦null| 否 |Departure Terminal|
|»» arrTerminal|body|string¦null| 否 |Arrival Terminal|
|»» cabinClass|body|[CabinClass](#schemacabinclass)¦null| 否 |Service grade of the fare|
|»» fareFamily|body|string¦null| 否 |Fare Family as per the information received from the airline.|
|»» duration|body|integer¦null| 否 |The flying duration in minutes.|
|» retSegments|body|[[PNRClaimFlight](#schemapnrclaimflight)]¦null| 否 |Inbound segments|
|»» carrier|body|string| 是 |IATA code of the marketing airline|
|»» flightNumber|body|string| 是 |The value denotes the marketing flight number.|
|»» depAirport|body|string| 是 |IATA code of the departure airport.|
|»» arrAirport|body|string| 是 |IATA code of the arrival airport.|
|»» depTime|body|string| 是 |Departure time of the flight. Format:`yyyyMMddHHmm`|
|»» arrTime|body|string¦null| 否 |Arrival time of the flight. Format:`yyyyMMddHHmm`|
|»» stopCities|body|string¦null| 否 |Name of cities from where the passengers will take connecting flights. Include IATA code of cities and use a comma in case of multiple cities to separate if transfer airports count is higher than 1. For example: CGK, SUB. Blank means non-stop flight.|
|»» codeShare|body|integer¦null| 否 |- 1: code share|
|»» operatingCarrier|body|string¦null| 否 |Operating carrier. It is blank when codeshare=false|
|»» operatingFlightNumber|body|string¦null| 否 |Operating flight number. It is blank when codeshare=false|
|»» depTerminal|body|string¦null| 否 |Departure Terminal|
|»» arrTerminal|body|string¦null| 否 |Arrival Terminal|
|»» cabinClass|body|[CabinClass](#schemacabinclass)¦null| 否 |Service grade of the fare|
|»» fareFamily|body|string¦null| 否 |Fare Family as per the information received from the airline.|
|»» duration|body|integer¦null| 否 |The flying duration in minutes.|

#### 详细说明

**»» flightNumber**: The value denotes the marketing flight number.
Format: CA123 or TR021 or FR1290. The letters denote the carrier and the three/four-digit number that follows is the flight number.

**»» codeShare**: - 1: code share
- 0: Not code share

**»» flightNumber**: The value denotes the marketing flight number.
Format: CA123 or TR021 or FR1290. The letters denote the carrier and the three/four-digit number that follows is the flight number.

**»» codeShare**: - 1: code share
- 0: Not code share

#### 枚举值

|属性|值|
|---|---|
|»» cabinClass|1|
|»» cabinClass|2|
|»» cabinClass|3|
|»» cabinClass|4|
|»» cabinClass|1|
|»» cabinClass|2|
|»» cabinClass|3|
|»» cabinClass|4|

> 返回示例

> 200 Response

```json
{
  "status": 0,
  "msg": "success",
  "sessionId": "90223f62-fd87-45b4-9a32-68f03f9f85c8",
  "ticketOrderNo": "TESTA20240618162411631",
  "supportCreditTransPayment": "0",
  "currency": "USD",
  "fromSegments": [
    {
      "segmentIndex": 1,
      "carrier": "5F",
      "flightNumber": "5F617",
      "depAirport": "RMO",
      "depTime": "202408200810",
      "arrAirport": "LTN",
      "arrTime": "202408200940",
      "stopCities": "",
      "duration": 210,
      "codeShare": false,
      "cabin": "",
      "cabinClass": 1,
      "seatCount": 4,
      "aircraftCode": "",
      "depTerminal": "",
      "arrTerminal": "",
      "operatingCarrier": "5F",
      "operatingFlightnumber": "",
      "fareFamily": "LOYAL"
    }
  ],
  "retSegments": [
    {
      "segmentIndex": 2,
      "carrier": "5F",
      "flightNumber": "5F618",
      "depAirport": "LTN",
      "depTime": "202408251040",
      "arrAirport": "RMO",
      "arrTime": "202408251550",
      "stopCities": "",
      "duration": 190,
      "codeShare": false,
      "cabin": "",
      "cabinClass": 1,
      "seatCount": 4,
      "aircraftCode": "",
      "depTerminal": "",
      "arrTerminal": "",
      "operatingCarrier": "5F",
      "operatingFlightnumber": "",
      "fareFamily": "LOYAL"
    }
  ],
  "ancillaryProductElements": [
    {
      "segmentIndex": 1,
      "endSegmentIndex": null,
      "productCode": "SCI_BAG_1PC_10KG",
      "canPurchaseWithTicket": 0,
      "canPurchasePostTicket": 1,
      "price": 22.88,
      "currency": "USD",
      "vendorPrice": null,
      "vendorCurrency": null,
      "clientTechnicalServiceFee": 0,
      "clientTechnicalServiceFeeMode": "PER_PAX",
      "auxBaggageElement": {
        "piece": 1,
        "weight": 10,
        "isAllWeight": true,
        "size": ""
      },
      "offerId": null,
      "maxQty": 1,
      "minQty": 1,
      "categoryCode": "StandardCheckInBaggage",
      "ancillaryCode": "SCI_BAG_1PC_10KG",
      "auxSeatElement": null
    },
    {
      "segmentIndex": 1,
      "endSegmentIndex": null,
      "productCode": "SCI_BAG_1PC_20KG",
      "canPurchaseWithTicket": 0,
      "canPurchasePostTicket": 1,
      "price": 46.2,
      "currency": "USD",
      "vendorPrice": null,
      "vendorCurrency": null,
      "clientTechnicalServiceFee": 0,
      "clientTechnicalServiceFeeMode": "PER_PAX",
      "auxBaggageElement": {
        "piece": 1,
        "weight": 20,
        "isAllWeight": true,
        "size": ""
      },
      "offerId": null,
      "maxQty": 1,
      "minQty": 1,
      "categoryCode": "StandardCheckInBaggage",
      "ancillaryCode": "SCI_BAG_1PC_20KG",
      "auxSeatElement": null
    },
    {
      "segmentIndex": 1,
      "endSegmentIndex": null,
      "productCode": "SCI_BAG_1PC_30KG",
      "canPurchaseWithTicket": 0,
      "canPurchasePostTicket": 1,
      "price": 34.54,
      "currency": "USD",
      "vendorPrice": null,
      "vendorCurrency": null,
      "clientTechnicalServiceFee": 0,
      "clientTechnicalServiceFeeMode": "PER_PAX",
      "auxBaggageElement": {
        "piece": 1,
        "weight": 30,
        "isAllWeight": true,
        "size": ""
      },
      "offerId": null,
      "maxQty": 1,
      "minQty": 1,
      "categoryCode": "StandardCheckInBaggage",
      "ancillaryCode": "SCI_BAG_1PC_30KG",
      "auxSeatElement": null
    },
    {
      "segmentIndex": 1,
      "endSegmentIndex": null,
      "productCode": "SCI_BAG_2PC_20KG",
      "canPurchaseWithTicket": 0,
      "canPurchasePostTicket": 1,
      "price": 74.58,
      "currency": "USD",
      "vendorPrice": null,
      "vendorCurrency": null,
      "clientTechnicalServiceFee": 0,
      "clientTechnicalServiceFeeMode": "PER_PAX",
      "auxBaggageElement": {
        "piece": 2,
        "weight": 20,
        "isAllWeight": true,
        "size": ""
      },
      "offerId": null,
      "maxQty": 1,
      "minQty": 1,
      "categoryCode": "StandardCheckInBaggage",
      "ancillaryCode": "SCI_BAG_2PC_20KG",
      "auxSeatElement": null
    },
    {
      "segmentIndex": 1,
      "endSegmentIndex": null,
      "productCode": "SCI_BAG_2PC_40KG",
      "canPurchaseWithTicket": 0,
      "canPurchasePostTicket": 1,
      "price": 49.81,
      "currency": "USD",
      "vendorPrice": null,
      "vendorCurrency": null,
      "clientTechnicalServiceFee": 0,
      "clientTechnicalServiceFeeMode": "PER_PAX",
      "auxBaggageElement": {
        "piece": 2,
        "weight": 40,
        "isAllWeight": true,
        "size": ""
      },
      "offerId": null,
      "maxQty": 1,
      "minQty": 1,
      "categoryCode": "StandardCheckInBaggage",
      "ancillaryCode": "SCI_BAG_2PC_40KG",
      "auxSeatElement": null
    },
    {
      "segmentIndex": 1,
      "endSegmentIndex": null,
      "productCode": "SCI_BAG_2PC_60KG",
      "canPurchaseWithTicket": 0,
      "canPurchasePostTicket": 1,
      "price": 124.11,
      "currency": "USD",
      "vendorPrice": null,
      "vendorCurrency": null,
      "clientTechnicalServiceFee": 0,
      "clientTechnicalServiceFeeMode": "PER_PAX",
      "auxBaggageElement": {
        "piece": 2,
        "weight": 60,
        "isAllWeight": true,
        "size": ""
      },
      "offerId": null,
      "maxQty": 1,
      "minQty": 1,
      "categoryCode": "StandardCheckInBaggage",
      "ancillaryCode": "SCI_BAG_2PC_60KG",
      "auxSeatElement": null
    },
    {
      "segmentIndex": 1,
      "endSegmentIndex": null,
      "productCode": "SCI_BAG_3PC_30KG",
      "canPurchaseWithTicket": 0,
      "canPurchasePostTicket": 1,
      "price": 105.16,
      "currency": "USD",
      "vendorPrice": null,
      "vendorCurrency": null,
      "clientTechnicalServiceFee": 0,
      "clientTechnicalServiceFeeMode": "PER_PAX",
      "auxBaggageElement": {
        "piece": 3,
        "weight": 30,
        "isAllWeight": true,
        "size": ""
      },
      "offerId": null,
      "maxQty": 1,
      "minQty": 1,
      "categoryCode": "StandardCheckInBaggage",
      "ancillaryCode": "SCI_BAG_3PC_30KG",
      "auxSeatElement": null
    },
    {
      "segmentIndex": 1,
      "endSegmentIndex": null,
      "productCode": "SCI_BAG_3PC_60KG",
      "canPurchaseWithTicket": 0,
      "canPurchasePostTicket": 1,
      "price": 132.01,
      "currency": "USD",
      "vendorPrice": null,
      "vendorCurrency": null,
      "clientTechnicalServiceFee": 0,
      "clientTechnicalServiceFeeMode": "PER_PAX",
      "auxBaggageElement": {
        "piece": 3,
        "weight": 60,
        "isAllWeight": true,
        "size": ""
      },
      "offerId": null,
      "maxQty": 1,
      "minQty": 1,
      "categoryCode": "StandardCheckInBaggage",
      "ancillaryCode": "SCI_BAG_3PC_60KG",
      "auxSeatElement": null
    },
    {
      "segmentIndex": 1,
      "endSegmentIndex": null,
      "productCode": "SCI_BAG_3PC_90KG",
      "canPurchaseWithTicket": 0,
      "canPurchasePostTicket": 1,
      "price": 184.19,
      "currency": "USD",
      "vendorPrice": null,
      "vendorCurrency": null,
      "clientTechnicalServiceFee": 0,
      "clientTechnicalServiceFeeMode": "PER_PAX",
      "auxBaggageElement": {
        "piece": 3,
        "weight": 90,
        "isAllWeight": true,
        "size": ""
      },
      "offerId": null,
      "maxQty": 1,
      "minQty": 1,
      "categoryCode": "StandardCheckInBaggage",
      "ancillaryCode": "SCI_BAG_3PC_90KG",
      "auxSeatElement": null
    },
    {
      "segmentIndex": 1,
      "endSegmentIndex": null,
      "productCode": "COL_BAG_1PC_10KG",
      "canPurchaseWithTicket": 0,
      "canPurchasePostTicket": 1,
      "price": 22.71,
      "currency": "USD",
      "vendorPrice": null,
      "vendorCurrency": null,
      "clientTechnicalServiceFee": 0,
      "clientTechnicalServiceFeeMode": "PER_PAX",
      "auxBaggageElement": {
        "piece": 1,
        "weight": 10,
        "isAllWeight": true,
        "size": ""
      },
      "offerId": null,
      "maxQty": 1,
      "minQty": 1,
      "categoryCode": "CabinBaggageOverheadLocker",
      "ancillaryCode": "COL_BAG_1PC_10KG",
      "auxSeatElement": null
    },
    {
      "segmentIndex": 2,
      "endSegmentIndex": null,
      "productCode": "SCI_BAG_1PC_10KG",
      "canPurchaseWithTicket": 0,
      "canPurchasePostTicket": 1,
      "price": 43.48,
      "currency": "USD",
      "vendorPrice": null,
      "vendorCurrency": null,
      "clientTechnicalServiceFee": 0,
      "clientTechnicalServiceFeeMode": "PER_PAX",
      "auxBaggageElement": {
        "piece": 1,
        "weight": 10,
        "isAllWeight": true,
        "size": ""
      },
      "offerId": null,
      "maxQty": 1,
      "minQty": 1,
      "categoryCode": "StandardCheckInBaggage",
      "ancillaryCode": "SCI_BAG_1PC_10KG",
      "auxSeatElement": null
    },
    {
      "segmentIndex": 2,
      "endSegmentIndex": null,
      "productCode": "SCI_BAG_1PC_20KG",
      "canPurchaseWithTicket": 0,
      "canPurchasePostTicket": 1,
      "price": 39.93,
      "currency": "USD",
      "vendorPrice": null,
      "vendorCurrency": null,
      "clientTechnicalServiceFee": 0,
      "clientTechnicalServiceFeeMode": "PER_PAX",
      "auxBaggageElement": {
        "piece": 1,
        "weight": 20,
        "isAllWeight": true,
        "size": ""
      },
      "offerId": null,
      "maxQty": 1,
      "minQty": 1,
      "categoryCode": "StandardCheckInBaggage",
      "ancillaryCode": "SCI_BAG_1PC_20KG",
      "auxSeatElement": null
    },
    {
      "segmentIndex": 2,
      "endSegmentIndex": null,
      "productCode": "SCI_BAG_1PC_30KG",
      "canPurchaseWithTicket": 0,
      "canPurchasePostTicket": 1,
      "price": 44.09,
      "currency": "USD",
      "vendorPrice": null,
      "vendorCurrency": null,
      "clientTechnicalServiceFee": 0,
      "clientTechnicalServiceFeeMode": "PER_PAX",
      "auxBaggageElement": {
        "piece": 1,
        "weight": 30,
        "isAllWeight": true,
        "size": ""
      },
      "offerId": null,
      "maxQty": 1,
      "minQty": 1,
      "categoryCode": "StandardCheckInBaggage",
      "ancillaryCode": "SCI_BAG_1PC_30KG",
      "auxSeatElement": null
    },
    {
      "segmentIndex": 2,
      "endSegmentIndex": null,
      "productCode": "SCI_BAG_2PC_20KG",
      "canPurchaseWithTicket": 0,
      "canPurchasePostTicket": 1,
      "price": 89.28,
      "currency": "USD",
      "vendorPrice": null,
      "vendorCurrency": null,
      "clientTechnicalServiceFee": 0,
      "clientTechnicalServiceFeeMode": "PER_PAX",
      "auxBaggageElement": {
        "piece": 2,
        "weight": 20,
        "isAllWeight": true,
        "size": ""
      },
      "offerId": null,
      "maxQty": 1,
      "minQty": 1,
      "categoryCode": "StandardCheckInBaggage",
      "ancillaryCode": "SCI_BAG_2PC_20KG",
      "auxSeatElement": null
    },
    {
      "segmentIndex": 2,
      "endSegmentIndex": null,
      "productCode": "SCI_BAG_2PC_40KG",
      "canPurchaseWithTicket": 0,
      "canPurchasePostTicket": 1,
      "price": 81.05,
      "currency": "USD",
      "vendorPrice": null,
      "vendorCurrency": null,
      "clientTechnicalServiceFee": 0,
      "clientTechnicalServiceFeeMode": "PER_PAX",
      "auxBaggageElement": {
        "piece": 2,
        "weight": 40,
        "isAllWeight": true,
        "size": ""
      },
      "offerId": null,
      "maxQty": 1,
      "minQty": 1,
      "categoryCode": "StandardCheckInBaggage",
      "ancillaryCode": "SCI_BAG_2PC_40KG",
      "auxSeatElement": null
    },
    {
      "segmentIndex": 2,
      "endSegmentIndex": null,
      "productCode": "SCI_BAG_2PC_60KG",
      "canPurchaseWithTicket": 0,
      "canPurchasePostTicket": 1,
      "price": 141.74,
      "currency": "USD",
      "vendorPrice": null,
      "vendorCurrency": null,
      "clientTechnicalServiceFee": 0,
      "clientTechnicalServiceFeeMode": "PER_PAX",
      "auxBaggageElement": {
        "piece": 2,
        "weight": 60,
        "isAllWeight": true,
        "size": ""
      },
      "offerId": null,
      "maxQty": 1,
      "minQty": 1,
      "categoryCode": "StandardCheckInBaggage",
      "ancillaryCode": "SCI_BAG_2PC_60KG",
      "auxSeatElement": null
    },
    {
      "segmentIndex": 2,
      "endSegmentIndex": null,
      "productCode": "SCI_BAG_3PC_30KG",
      "canPurchaseWithTicket": 0,
      "canPurchasePostTicket": 1,
      "price": 138.97,
      "currency": "USD",
      "vendorPrice": null,
      "vendorCurrency": null,
      "clientTechnicalServiceFee": 0,
      "clientTechnicalServiceFeeMode": "PER_PAX",
      "auxBaggageElement": {
        "piece": 3,
        "weight": 30,
        "isAllWeight": true,
        "size": ""
      },
      "offerId": null,
      "maxQty": 1,
      "minQty": 1,
      "categoryCode": "StandardCheckInBaggage",
      "ancillaryCode": "SCI_BAG_3PC_30KG",
      "auxSeatElement": null
    },
    {
      "segmentIndex": 2,
      "endSegmentIndex": null,
      "productCode": "SCI_BAG_3PC_60KG",
      "canPurchaseWithTicket": 0,
      "canPurchasePostTicket": 1,
      "price": 98.49,
      "currency": "USD",
      "vendorPrice": null,
      "vendorCurrency": null,
      "clientTechnicalServiceFee": 0,
      "clientTechnicalServiceFeeMode": "PER_PAX",
      "auxBaggageElement": {
        "piece": 3,
        "weight": 60,
        "isAllWeight": true,
        "size": ""
      },
      "offerId": null,
      "maxQty": 1,
      "minQty": 1,
      "categoryCode": "StandardCheckInBaggage",
      "ancillaryCode": "SCI_BAG_3PC_60KG",
      "auxSeatElement": null
    },
    {
      "segmentIndex": 2,
      "endSegmentIndex": null,
      "productCode": "SCI_BAG_3PC_90KG",
      "canPurchaseWithTicket": 0,
      "canPurchasePostTicket": 1,
      "price": 272.31,
      "currency": "USD",
      "vendorPrice": null,
      "vendorCurrency": null,
      "clientTechnicalServiceFee": 0,
      "clientTechnicalServiceFeeMode": "PER_PAX",
      "auxBaggageElement": {
        "piece": 3,
        "weight": 90,
        "isAllWeight": true,
        "size": ""
      },
      "offerId": null,
      "maxQty": 1,
      "minQty": 1,
      "categoryCode": "StandardCheckInBaggage",
      "ancillaryCode": "SCI_BAG_3PC_90KG",
      "auxSeatElement": null
    },
    {
      "segmentIndex": 2,
      "endSegmentIndex": null,
      "productCode": "COL_BAG_1PC_10KG",
      "canPurchaseWithTicket": 0,
      "canPurchasePostTicket": 1,
      "price": 22.04,
      "currency": "USD",
      "vendorPrice": null,
      "vendorCurrency": null,
      "clientTechnicalServiceFee": 0,
      "clientTechnicalServiceFeeMode": "PER_PAX",
      "auxBaggageElement": {
        "piece": 1,
        "weight": 10,
        "isAllWeight": true,
        "size": ""
      },
      "offerId": null,
      "maxQty": 1,
      "minQty": 1,
      "categoryCode": "CabinBaggageOverheadLocker",
      "ancillaryCode": "COL_BAG_1PC_10KG",
      "auxSeatElement": null
    }
  ]
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» status|[PostBookingAncillarySearchResponseStatus](#schemapostbookingancillarysearchresponsestatus)|true|none||- 117: Baggage is not allowed for this order as it is not in the ticketed status<br />- 118: Atlas currently does not support seat or baggage for this airline<br />- 119: Baggage or seat selection is not supported for orders with infants<br />- 120: Baggage or seat selection for the flight has been closed<br />- 121: It's not allowed to purchase ancillary in 24 hours before departure<br />- 125: Post booking ancillary search timeout|
|» msg|[ResponseMessage](#schemaresponsemessage)¦null|false|none||It serves as an additional description of the response result. Especially when the interface reports an error (`status` !=`0`), it is usually a human-readable error message. Note: Do not use this field in any programming scenarios. For example, do not judge whether the interface responds successfully based on this field. Instead, you should only determine it by checking whether the status is equal to`0`at any time.|
|» sessionId|string|true|none||The unique identifier for this search. It is required when you call order function to make a reservation to identify which ancillary the client is choosing.|
|» ticketOrderNo|string|true|none||Order number. It is the original order number.|
|» supportCreditTransPayment|string|true|none||This tag is used to identify if the fare needs to be paid using the client's credit card. This field has been deprecated, please use `supportPaymentMethods` instead.|
|» currency|string|true|none||The currency in which Atlas settles transactions with you.|
|» fromSegments|[[RoutingSegment](#schemaroutingsegment)]|true|none||Outbound segments|
|»» aircraftCode|string¦null|false|none||IATA Code of aircraft type|
|»» arrAirport|string|true|none||3-letter iata code for the arrival airport at which the segment is scheduled to arrive.|
|»» arrTerminal|string¦null|false|none||The terminal at the destination airport where the segment is scheduled to arrive.|
|»» arrTime|string|true|none||The datetime at which the segment is scheduled to arrive, in the arrival airport timezone. The format is `YYYYMMDD`.|
|»» cabin|string¦null|false|none||RBD(known as Reservation Booking Designator) displayed by the airline.|
|»» cabinClass|[CabinClass](#schemacabinclass)|true|none||Cabin class of the segment.<br />- 1: economy<br />- 2: business<br />- 3: first<br />- 4: premium economy|
|»» carrier|string|true|none||IATA code of marketing carrier.|
|»» codeShare|boolean|true|none||A flag used to identify whether it is a code share flight.|
|»» depAirport|string|true|none||3-letter iata code for the airport at which the segment is scheduled to depart.|
|»» depTerminal|string¦null|false|none||The terminal at the departure airport from which the segment is scheduled to depart.|
|»» depTime|string|true|none||The datetime at which the segment is scheduled to depart, in the departure airport timezone. The format is`YYYYMMSS`.|
|»» duration|integer|true|none||The duration of the segment in munites.|
|»» fareFamily|string|true|none||Fare Family as per the information received from the airline|
|»» flightNumber|string|true|none||Marketing flight number. The format is: CA123 or TR021 or FR1290, with the first two letters representing the carrier and the following number representing the flight number.|
|»» operatingCarrier|string¦null|false|none||2-letter iata code for the operating carrier. The airline actually operating this segment. This may differ from the marketing carrier in the case of a "codeshare", where one airline sells flights operated by another airline.|
|»» operatingFlightnumber|string¦null|false|none||Operating flight number.|
|»» seatCount|integer|true|none||Max booking seats for the fare.|
|»» segmentIndex|integer|true|none||Segment sequence. Starts from 1. If it is return trip, sequence for outbound trip and inbound trip would be together. The segment index also represents the flight sequence of the segment.|
|»» stopCities|string¦null|false|none||IATA code/Name of cities from where the passengers will take stopover flights. Include IATA code of cities and use a comma in case of multiple cities to separate transfer airports count is higher than 1. For example: `CGK, SUB`. <br />`null` or blank means non-stop flight.|
|» retSegments|[[RoutingSegment](#schemaroutingsegment)]¦null|false|none||Inbound segments|
|»» aircraftCode|string¦null|false|none||IATA Code of aircraft type|
|»» arrAirport|string|true|none||3-letter iata code for the arrival airport at which the segment is scheduled to arrive.|
|»» arrTerminal|string¦null|false|none||The terminal at the destination airport where the segment is scheduled to arrive.|
|»» arrTime|string|true|none||The datetime at which the segment is scheduled to arrive, in the arrival airport timezone. The format is `YYYYMMDD`.|
|»» cabin|string¦null|false|none||RBD(known as Reservation Booking Designator) displayed by the airline.|
|»» cabinClass|[CabinClass](#schemacabinclass)|true|none||Cabin class of the segment.<br />- 1: economy<br />- 2: business<br />- 3: first<br />- 4: premium economy|
|»» carrier|string|true|none||IATA code of marketing carrier.|
|»» codeShare|boolean|true|none||A flag used to identify whether it is a code share flight.|
|»» depAirport|string|true|none||3-letter iata code for the airport at which the segment is scheduled to depart.|
|»» depTerminal|string¦null|false|none||The terminal at the departure airport from which the segment is scheduled to depart.|
|»» depTime|string|true|none||The datetime at which the segment is scheduled to depart, in the departure airport timezone. The format is`YYYYMMSS`.|
|»» duration|integer|true|none||The duration of the segment in munites.|
|»» fareFamily|string|true|none||Fare Family as per the information received from the airline|
|»» flightNumber|string|true|none||Marketing flight number. The format is: CA123 or TR021 or FR1290, with the first two letters representing the carrier and the following number representing the flight number.|
|»» operatingCarrier|string¦null|false|none||2-letter iata code for the operating carrier. The airline actually operating this segment. This may differ from the marketing carrier in the case of a "codeshare", where one airline sells flights operated by another airline.|
|»» operatingFlightnumber|string¦null|false|none||Operating flight number.|
|»» seatCount|integer|true|none||Max booking seats for the fare.|
|»» segmentIndex|integer|true|none||Segment sequence. Starts from 1. If it is return trip, sequence for outbound trip and inbound trip would be together. The segment index also represents the flight sequence of the segment.|
|»» stopCities|string¦null|false|none||IATA code/Name of cities from where the passengers will take stopover flights. Include IATA code of cities and use a comma in case of multiple cities to separate transfer airports count is higher than 1. For example: `CGK, SUB`. <br />`null` or blank means non-stop flight.|
|» ancillaryProductElements|[[AncillaryProduct](#schemaancillaryproduct)]¦null|false|none||Ancillary service quotation. If no available services, it will be`null` or`[]`|
|»» ancillaryCode|string|true|none||A code that is relatively readable by humans and contains information about auxiliary business specifications (such as weight and quantity limitations of luggage). <br />**Note:** <br />This content is only for display purposes and should not be used for programming purposes. That is to say, do not attempt to parse the information about auxiliary business specifications from this code. If you want to access the auxiliary business specifications, please use structured fields. For example, for luggage, please use`auxBaggageElement`.|
|»» auxBaggageElement|object¦null|false|none||Baggage specification limitations. This node is valid only when the ancillary type (`categoryCode`) is baggage.|
|»»» isAllWeight|boolean|true|none||Mark whether the`weight`field restricts the total weight or the weight of a single piece.<br />- `true`: The weight is for all the pieces<br />- `false`: The weight is for each piece|
|»»» piece|integer|true|none||The maximum number of pieces that can be purchased per person.<br />- `0`: No Limitation about piece<br />- `>0`: Maximum pieces|
|»»» size|string¦null|false|none||Maximum size for the baggage|
|»»» weight|integer|true|none||The maximum weight that can be purchased per person.<br />- `0`: No limitation for weight<br />- `>0`: Weight limit (KG)|
|»» canPurchasePostTicket|integer|true|none||A flag used to mark if this ancillary product can be purchased in the post-ticketing flow.<br />- `0`: No<br />- `1`: Yes|
|»» canPurchaseWithTicket|integer|true|none||A flag used to mark if this ancillary product can be purchased during the booking flow.<br />- `0`: No<br />- `1`: Yes|
|»» categoryCode|[AncillaryCategory](#schemaancillarycategory)|true|none||Type of the ancillary.<br /><br />- StandardCheckInBaggage: Standard Check-in Baggage.<br />- CabinBaggage: Usually refers to the Cabin Baggage Overhead Locker. Transition value. It will gradually transition to `CabinBaggageOverheadLocker`.<br />- CabinBaggageOverheadLocker: Cabin Baggage Overhead Locker.<br />- CabinBaggageUnderSeat: Cabin Baggage Under Seat. Usually refers to the personal item.|
|»» clientTechnicalServiceFee|number¦null|false|none||The service fee charged by Atlas for the purchase of the ancillary.|
|»» currency|string|true|none||The currency in which Atlas settles transactions with you|
|»» maxQty|integer|true|none||The maximum number of purchases allowed per person per flight segment|
|»» minQty|integer|true|none||The minimum quantity allowed to be purchased per person per flight segment.|
|»» price|number|true|none||Price for this ancillary.|
|»» productCode|string|true|none||Unique identifier for the ancillary product. It would be used in the order request.|
|»» segmentIndex|integer|true|none||The index of segment the ancillary applies to.|
|»» vendorCurrency|string|true|none||The currency in which the vendor charges for the ancillary. If the fare does not allow for the VCC pass-through or BYOA payment, this information will be`null`.|
|»» vendorPrice|integer|true|none||The price charged by the vendor for the ancillary. If the fare does not allow for the VCC pass-through or BYOA payment, this information will be`null`.|
|» supportPaymentMethods|[[PaymentMethod](#schemapaymentmethod)]¦null|false|none||Support payment methods. If payment is not supported in any way, this will be `null`or`[]`|
|» cardChargeList|[[CardCharge](#schemacardcharge)]¦null|false|none||Payment handling fee of MoR|
|»» cardType|[CardType](#schemacardtype)|true|none||Card types, such as Visa, MasterCard|
|»» percentage|number¦null|false|none||Percentage of payment handling fee|
|»» charge|number¦null|false|none||The amount of payment handling fee|
|»» currency|string¦null|false|none||Currency of `charge`|

#### 枚举值

|属性|值|
|---|---|
|status|117|
|status|118|
|status|119|
|status|120|
|status|121|
|status|125|
|cabinClass|1|
|cabinClass|2|
|cabinClass|3|
|cabinClass|4|
|cabinClass|1|
|cabinClass|2|
|cabinClass|3|
|cabinClass|4|
|categoryCode|StandardCheckInBaggage|
|categoryCode|CabinBaggage|
|categoryCode|CabinBaggageUnderSeat|
|categoryCode|CabinBaggageOverheadLocker|
|cardType|Amex|
|cardType|Visa|
|cardType|MasterCard|
|cardType|JCB|
|cardType|Discover|
|cardType|DinersClub|

## POST Order Ancillary

POST /postBookingAncillaryOrder.do

**Dependency:**
The `postBookingAncillarySearch.do` function should be called prior to this one.

> **Procedure:** 
>   1.  Copy the Session ID into the request body.
>   2.  Type the passenger information and "product code" selected from the response in "postBookingAncillarySearch.do".

**Endpoint:**
https://sandbox.atriptech.com/postBookingAncillaryOrder.do

> Body 请求参数

```json
{
  "sessionId": "2cf48a2a-231e-40f6-aabd-95d4e7c5e68c",
  "ancillaryCategory": "BAGGAGE",
  "ticketOrderNo": "ANGXV20250721232014646",
  "passengers": [
    {
      "name": "************",
      "passengerType": 0,
      "ancillaries": [
        {
          "productCode": "SCI_BAG_1PC_15KG",
          "segmentIndex": 1
        }
      ]
    }
  ],
  "payment": {
    "cardType": "Mastercard"
  }
}
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|Accept|header|string| 是 |none|
|Content-Type|header|string| 是 |none|
|Accept-Encoding|header|string| 是 |none|
|x-atlas-client-id|header|string| 是 |none|
|x-atlas-client-secret|header|string| 是 |none|
|body|body|object| 否 |none|
|» sessionId|body|string| 是 |Identifier of the searched ancillary, received from the ancillary search response.|
|» ancillaryCategory|body|string| 是 |Ancillary Category. Different categories of ancillaries need to be separately requested. Currently we only support`BAGGAGE`.|
|» ticketOrderNo|body|string| 是 |Order number. It is the original order number.|
|» passengers|body|[object]| 是 |Passengers who need to purchase ancillary services and the ancillary services they choose|
|»» name|body|string| 是 |The passenger's name. Please send it in the following format: Family Name/Given Name|
|»» passengerType|body|[PassengerType](#schemapassengertype)| 是 |Type of passenger.|
|»» ancillaries|body|[object]¦null| 否 |Ancillaries selection for the specific passenger|
|»»» productCode|body|string| 是 |Ancillary product code(`productCode`). Got from routing element in the search/revalidation response.|
|»»» segmentIndex|body|integer| 是 |Segment sequence|
|»» residentInfo|body|object¦null| 否 |Resident Info|
|»»» docType|body|string| 是 |Certificate types supported by resident' prices|
|»»» docNum|body|string¦null| 否 |ID number, if the ID type is D, E|
|»»» municipality|body|string¦null| 否 |Municipal district code|
|»»» largeFamilyCert|body|string¦null| 否 |Large Family Cert|
|»»» community|body|string¦null| 否 |Community Region Code|
|» payment|body|object¦null| 否 |none|
|»» cardType|body|[CardType](#schemacardtype)| 是 |The card type you wish to use for payment. Send this information when generating an order can be used to calculate the payment handling fee. This parameter is only effective and required in the MoR payment scenario.|

#### 详细说明

**»» passengerType**: Type of passenger.
- 0: Adult
- 1: Child
- 2: Infant

#### 枚举值

|属性|值|
|---|---|
|»» passengerType|0|
|»» passengerType|1|
|»» passengerType|2|
|»» cardType|Amex|
|»» cardType|Visa|
|»» cardType|MasterCard|
|»» cardType|JCB|
|»» cardType|Discover|
|»» cardType|DinersClub|

> 返回示例

> 200 Response

```json
{
  "status": 0,
  "msg": null,
  "sessionId": "2cf48a2a-231e-40f6-aabd-95d4e7c5e68c",
  "orderNo": "BZYPU20250805170848969",
  "totalPrice": 23.07,
  "totalTransactionFee": 0.75,
  "currency": "USD",
  "vendorTotalPrice": 84.7,
  "vendorCurrency": "AED",
  "tktLimitTime": "2025-08-05 17:24:48",
  "paxTicketInfos": [
    {
      "name": "************",
      "passengerType": 0,
      "birthday": "********",
      "gender": "*",
      "cardNum": "*********",
      "cardType": "**",
      "cardIssuePlace": "**",
      "cardExpired": "********",
      "nationality": "**",
      "ticketNos": null,
      "airlinePNRs": null,
      "contactEmails": null,
      "contactPhones": null,
      "ancillaries": [
        {
          "productCode": "SCI_BAG_1PC_15KG",
          "segmentIndex": 1,
          "ancillaryPrice": 23.07,
          "currency": "USD",
          "auxBaggageElement": {
            "piece": 1,
            "weight": 15,
            "isAllWeight": true,
            "size": null
          }
        }
      ]
    }
  ],
  "paymentOptions": [
    {
      "paymentMethod": 3,
      "serviceFee": {
        "amount": 0.75,
        "currency": "USD",
        "deductFrom": "DEPOSIT"
      },
      "ticketFare": {
        "amount": 84.7,
        "currency": "AED",
        "deductFrom": "CARD"
      },
      "paymentFee": null,
      "cardType": null
    }
  ],
  "ticketOrderNo": "ANGXV20250721232014646"
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» status|[OrderAncillaryResponseStatus](#schemaorderancillaryresponsestatus)|true|none||- 501: Add purchase not allowed. Description: Ancillary addition is not allowed for this order. Check with the airline or open a Service Request with Atlas for the same.<br />- 502: The price has increased, and the order creation has failed. Please perform a new search.. Description: There is a price change from the time the ancillary order search was conducted.<br />- 503: Incorrect baggage selection<br />- 504: Additional baggage not allowed. Ancillary baggage already exists in the original order. Description: Atlas only allows the attachment of ancillary baggage only once<br />- 505: Additional baggage not allowed. Baggage already booked as post-ticket ancillary.. Description: Atlas only allows the attachment of ancillary baggage only once<br />- 506: Ancillary addition is not supported for infants<br />- 507: It's not allowed to purchase ancillary in 24 hours before departure<br />- 508: No payment method is available. Please check whether the quotation currency or account configuration is correct.<br />- 509: Illegal request param|
|» msg|[ResponseMessage](#schemaresponsemessage)|true|none||It serves as an additional description of the response result. Especially when the interface reports an error (`status` !=`0`), it is usually a human-readable error message. Note: Do not use this field in any programming scenarios. For example, do not judge whether the interface responds successfully based on this field. Instead, you should only determine it by checking whether the status is equal to`0`at any time.|
|» sessionId|string|true|none||Echo the`sessionId`in the request parameters.|
|» orderNo|string|true|none||Order number of the created order.|
|» totalPrice|number|true|none||Total price(not including service fee) of this order in the currency TheAtlas settled with you|
|» totalTransactionFee|number|true|none||Total technical fees for this order in the currency TheAtlas settled with you.|
|» currency|string|true|none||The currency TheAtlas settled with you.|
|» vendorTotalPrice|number¦null|false|none||Total price of this order in the vendor's currency, reference for you to generate the specific credit card.|
|» vendorCurrency|string¦null|false|none||Vendor's currency.|
|» tktLimitTime|string|true|none||Payment deadline for this order. This time will be displayed in SGT (GMT +8). The fromat is:`yyyy-MM-dd HH:mm:ss`.|
|» paxTicketInfos|[object]|true|none||Ticket and ancillary information for passengers who purchased ancillary services.|
|»» name|string|true|none||Echo the passenger's name, in the format of last name/first name|
|»» passengerType|[PassengerType](#schemapassengertype)|true|none||Echo the passenger's type.<br />- 0: Adult<br />- 1: Child<br />- 2: Infant|
|»» birthday|string|true|none||Echo the passenger's birthday|
|»» gender|string|true|none||Echo the passenger's gender|
|»» cardNum|string¦null|false|none||Echo the passenger's  identity document number|
|»» cardType|string¦null|false|none||Echo the passenger's  identity document type|
|»» cardIssuePlace|string¦null|false|none||Echo the country where the passenger's identification document was issued.|
|»» cardExpired|string¦null|false|none||Echo the expiration date of the passenger's identification document.|
|»» nationality|string¦null|false|none||Echo the passenger's nationality|
|»» ticketNos|[string]|true|none||Ticket numbers|
|»» airlinePNRs|[string]|true|none||Airline PNRs. The array count would be the same as ticketnos count|
|»» ancillaries|[object]¦null|false|none||Ancillaries selection for the specific passenger|
|»»» productCode|string|true|none||Unique identifier for the ancillary product.|
|»»» segmentIndex|integer|true|none||The index of segment the ancillary applies to.|
|»»» currency|string|true|none||The currency in which Atlas settles transactions with you|
|»»» ancillaryPrice|number|true|none||Price for this ancillary.|
|»»» auxBaggageElement|object¦null|false|none||Baggage specification limitations. This node is valid only when the ancillary type (`categoryCode`) is baggage.|
|»»»» isAllWeight|boolean|true|none||Mark whether the`weight`field restricts the total weight or the weight of a single piece.<br />- `true`: The weight is for all the pieces<br />- `false`: The weight is for each piece|
|»»»» piece|integer|true|none||The maximum number of pieces that can be purchased per person.<br />- `0`: No Limitation about piece<br />- `>0`: Maximum pieces|
|»»»» size|string¦null|false|none||Maximum size for the baggage|
|»»»» weight|integer|true|none||The maximum weight that can be purchased per person.<br />- `0`: No limitation for weight<br />- `>0`: Weight limit (KG)|
|»»» auxSeatElement|object¦null|false|none||Seat selection for the specific passenger|
|»»»» row|string|true|none||Seat row|
|»»»» column|string|true|none||Seat column|
|»»» vendorCurrency|string|false|none||The currency in which the vendor charges for the ancillary. If the fare does not allow for the VCC pass-through or BYOA payment, this information will be`null`.|
|»»» vendorPrice|integer|false|none||The price charged by the vendor for the ancillary. If the fare does not allow for the VCC pass-through or BYOA payment, this information will be`null`.|
|»»» displayCurrency|string¦null|false|none||Display currency|
|»»» displayPrice|number¦null|false|none||Display price|
|»» contactEmails|[string]¦null|false|none||Passenger contact email address.|
|»» contactPhones|[string]¦null|false|none||Passenger contact phone number.|
|» paymentOptions|[object]|true|none||Available paymebt options for this order|
|»» paymentMethod|integer|true|none||none|
|»» serviceFee|[PaymentOption](#schemapaymentoption)|true|none||none|
|»»» paymentMethod|[PaymentMethod](#schemapaymentmethod)|true|none||Payment method.<br />- 1: balance<br />- 3: vcc passthrough<br />- 4: BYOA<br />- 5: MoR|
|»»» ticketFare|[PaymentOptionDetail](#schemapaymentoptiondetail)|true|none||It is used to describe the total ticket price and how the deduction will be made.|
|»»»» amount|number|true|none||Total amount will be deducted.|
|»»»» currency|string|true|none||Currency of the`amount`|
|»»»» deductFrom|string|true|none||Deduction method|
|»»» serviceFee|[PaymentOptionDetail](#schemapaymentoptiondetail)¦null|false|none||It is used to describe the total service and how the deduction will be made.|
|»»»» amount|number|true|none||Total amount will be deducted.|
|»»»» currency|string|true|none||Currency of the`amount`|
|»»»» deductFrom|string|true|none||Deduction method|
|»»» paymentFee|[PaymentOptionDetail](#schemapaymentoptiondetail)¦null|false|none||It is used to describe the payment fee and how the deduction will be made.|
|»»»» amount|number|true|none||Total amount will be deducted.|
|»»»» currency|string|true|none||Currency of the`amount`|
|»»»» deductFrom|string|true|none||Deduction method|
|»»» cardType|string¦null|false|none||Only for MoR. Echo the card type you sent in order request.|
|»» ticketFare|[PaymentOption](#schemapaymentoption)|true|none||none|
|»»» paymentMethod|[PaymentMethod](#schemapaymentmethod)|true|none||Payment method.<br />- 1: balance<br />- 3: vcc passthrough<br />- 4: BYOA<br />- 5: MoR|
|»»» ticketFare|[PaymentOptionDetail](#schemapaymentoptiondetail)|true|none||It is used to describe the total ticket price and how the deduction will be made.|
|»»» serviceFee|[PaymentOptionDetail](#schemapaymentoptiondetail)¦null|false|none||It is used to describe the total service and how the deduction will be made.|
|»»» paymentFee|[PaymentOptionDetail](#schemapaymentoptiondetail)¦null|false|none||It is used to describe the payment fee and how the deduction will be made.|
|»»» cardType|string¦null|false|none||Only for MoR. Echo the card type you sent in order request.|
|»» paymentFee|[PaymentOption](#schemapaymentoption)|true|none||none|
|»»» paymentMethod|[PaymentMethod](#schemapaymentmethod)|true|none||Payment method.<br />- 1: balance<br />- 3: vcc passthrough<br />- 4: BYOA<br />- 5: MoR|
|»»» ticketFare|[PaymentOptionDetail](#schemapaymentoptiondetail)|true|none||It is used to describe the total ticket price and how the deduction will be made.|
|»»» serviceFee|[PaymentOptionDetail](#schemapaymentoptiondetail)¦null|false|none||It is used to describe the total service and how the deduction will be made.|
|»»» paymentFee|[PaymentOptionDetail](#schemapaymentoptiondetail)¦null|false|none||It is used to describe the payment fee and how the deduction will be made.|
|»»» cardType|string¦null|false|none||Only for MoR. Echo the card type you sent in order request.|
|»» cardType|string¦null|true|none||none|
|» ticketOrderNo|string¦null|false|none||Order number. It is the original order number.|

#### 枚举值

|属性|值|
|---|---|
|status|501|
|status|502|
|status|503|
|status|504|
|status|505|
|status|506|
|status|507|
|status|508|
|status|509|
|passengerType|0|
|passengerType|1|
|passengerType|2|
|paymentMethod|1|
|paymentMethod|3|
|paymentMethod|4|
|paymentMethod|5|
|deductFrom|DEPOSIT|
|deductFrom|CARD|
|deductFrom|DEPOSIT|
|deductFrom|CARD|
|deductFrom|DEPOSIT|
|deductFrom|CARD|
|paymentMethod|1|
|paymentMethod|3|
|paymentMethod|4|
|paymentMethod|5|
|paymentMethod|1|
|paymentMethod|3|
|paymentMethod|4|
|paymentMethod|5|

# 数据模型

<h2 id="tocS_PaymentMethod">PaymentMethod</h2>

<a id="schemapaymentmethod"></a>
<a id="schema_PaymentMethod"></a>
<a id="tocSpaymentmethod"></a>
<a id="tocspaymentmethod"></a>

```json
1

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|integer|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|1|
|*anonymous*|3|
|*anonymous*|4|
|*anonymous*|5|

<h2 id="tocS_TransactionFeeMode">TransactionFeeMode</h2>

<a id="schematransactionfeemode"></a>
<a id="schema_TransactionFeeMode"></a>
<a id="tocStransactionfeemode"></a>
<a id="tocstransactionfeemode"></a>

```json
"PER_PAX"

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|string|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|PER_SEGMENT|
|*anonymous*|PER_TICKET|
|*anonymous*|PER_PAX|
|*anonymous*|PER_BOOKING|

<h2 id="tocS_CabinClass">CabinClass</h2>

<a id="schemacabinclass"></a>
<a id="schema_CabinClass"></a>
<a id="tocScabinclass"></a>
<a id="tocscabinclass"></a>

```json
1

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|integer|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|1|
|*anonymous*|2|
|*anonymous*|3|
|*anonymous*|4|

<h2 id="tocS_AncillaryCategory">AncillaryCategory</h2>

<a id="schemaancillarycategory"></a>
<a id="schema_AncillaryCategory"></a>
<a id="tocSancillarycategory"></a>
<a id="tocsancillarycategory"></a>

```json
"StandardCheckInBaggage"

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|string|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|StandardCheckInBaggage|
|*anonymous*|CabinBaggage|
|*anonymous*|CabinBaggageUnderSeat|
|*anonymous*|CabinBaggageOverheadLocker|

<h2 id="tocS_CardType">CardType</h2>

<a id="schemacardtype"></a>
<a id="schema_CardType"></a>
<a id="tocScardtype"></a>
<a id="tocscardtype"></a>

```json
"Amex"

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|string|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|Amex|
|*anonymous*|Visa|
|*anonymous*|MasterCard|
|*anonymous*|JCB|
|*anonymous*|Discover|
|*anonymous*|DinersClub|

<h2 id="tocS_PassengerType">PassengerType</h2>

<a id="schemapassengertype"></a>
<a id="schema_PassengerType"></a>
<a id="tocSpassengertype"></a>
<a id="tocspassengertype"></a>

```json
0

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|integer|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|0|
|*anonymous*|1|
|*anonymous*|2|

<h2 id="tocS_RefundStatus">RefundStatus</h2>

<a id="schemarefundstatus"></a>
<a id="schema_RefundStatus"></a>
<a id="tocSrefundstatus"></a>
<a id="tocsrefundstatus"></a>

```json
"T"

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|string|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|T|
|*anonymous*|H|
|*anonymous*|F|

<h2 id="tocS_ChangeStatus">ChangeStatus</h2>

<a id="schemachangestatus"></a>
<a id="schema_ChangeStatus"></a>
<a id="tocSchangestatus"></a>
<a id="tocschangestatus"></a>

```json
"T"

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|string|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|T|
|*anonymous*|H|
|*anonymous*|F|

<h2 id="tocS_OrderResponseStatus">OrderResponseStatus</h2>

<a id="schemaorderresponsestatus"></a>
<a id="schema_OrderResponseStatus"></a>
<a id="tocSorderresponsestatus"></a>
<a id="tocsorderresponsestatus"></a>

```json
301

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|integer|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|301|
|*anonymous*|302|
|*anonymous*|303|
|*anonymous*|304|
|*anonymous*|305|
|*anonymous*|307|
|*anonymous*|308|
|*anonymous*|309|
|*anonymous*|310|
|*anonymous*|312|
|*anonymous*|313|
|*anonymous*|315|
|*anonymous*|316|
|*anonymous*|317|
|*anonymous*|318|
|*anonymous*|319|
|*anonymous*|320|
|*anonymous*|321|
|*anonymous*|322|
|*anonymous*|323|
|*anonymous*|324|
|*anonymous*|325|
|*anonymous*|326|
|*anonymous*|327|
|*anonymous*|328|
|*anonymous*|329|
|*anonymous*|330|
|*anonymous*|407|
|*anonymous*|408|
|*anonymous*|409|
|*anonymous*|410|

<h2 id="tocS_PostBookingAncillarySearchResponseStatus">PostBookingAncillarySearchResponseStatus</h2>

<a id="schemapostbookingancillarysearchresponsestatus"></a>
<a id="schema_PostBookingAncillarySearchResponseStatus"></a>
<a id="tocSpostbookingancillarysearchresponsestatus"></a>
<a id="tocspostbookingancillarysearchresponsestatus"></a>

```json
117

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|integer|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|117|
|*anonymous*|118|
|*anonymous*|119|
|*anonymous*|120|
|*anonymous*|121|
|*anonymous*|125|

<h2 id="tocS_OrderAncillaryResponseStatus">OrderAncillaryResponseStatus</h2>

<a id="schemaorderancillaryresponsestatus"></a>
<a id="schema_OrderAncillaryResponseStatus"></a>
<a id="tocSorderancillaryresponsestatus"></a>
<a id="tocsorderancillaryresponsestatus"></a>

```json
501

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|integer|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|501|
|*anonymous*|502|
|*anonymous*|503|
|*anonymous*|504|
|*anonymous*|505|
|*anonymous*|506|
|*anonymous*|507|
|*anonymous*|508|
|*anonymous*|509|

<h2 id="tocS_ResidentInfo">ResidentInfo</h2>

<a id="schemaresidentinfo"></a>
<a id="schema_ResidentInfo"></a>
<a id="tocSresidentinfo"></a>
<a id="tocsresidentinfo"></a>

```json
{
  "residentInfo": {
    "docType": "string",
    "docNum": "string",
    "municipality": "string",
    "largeFamilyCert": "string",
    "community": "string"
  }
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|residentInfo|object¦null|false|none||Resident Info|
|» docType|string|true|none||Certificate types supported by resident' prices|
|» docNum|string¦null|false|none||ID number, if the ID type is D, E|
|» municipality|string¦null|false|none||Municipal district code|
|» largeFamilyCert|string¦null|false|none||Large Family Cert|
|» community|string¦null|false|none||Community Region Code|

<h2 id="tocS_Routing">Routing</h2>

<a id="schemarouting"></a>
<a id="schema_Routing"></a>
<a id="tocSrouting"></a>
<a id="tocsrouting"></a>

```json
{
  "routingIdentifier": "string",
  "supportCreditTransPayment": "1",
  "supportPaymentMethods": [
    1
  ],
  "currency": "string",
  "adultPrice": 0,
  "adultTax": 0,
  "adultDetails": [
    {
      "code": "string",
      "type": "base",
      "amount": 0,
      "description": "string"
    }
  ],
  "childPrice": 0,
  "childTax": 0,
  "childDetails": [
    {
      "code": "string",
      "type": "base",
      "amount": 0,
      "description": "string"
    }
  ],
  "infantPrice": 0,
  "infantTax": 0,
  "infantDetails": [
    {
      "code": "string",
      "type": "base",
      "amount": 0,
      "description": "string"
    }
  ],
  "infantAllowed": true,
  "childMandatorySeatingFee": 0,
  "transactionFeePerPax": 0,
  "transactionFee": 0,
  "transactionFeeMode": "PER_PAX",
  "fromSegments": [
    {
      "aircraftCode": "string",
      "arrAirport": "string",
      "arrTerminal": "string",
      "arrTime": "string",
      "cabin": "string",
      "cabinClass": 1,
      "carrier": "string",
      "codeShare": true,
      "depAirport": "string",
      "depTerminal": "string",
      "depTime": "string",
      "duration": 0,
      "fareFamily": "string",
      "flightNumber": "string",
      "operatingCarrier": "string",
      "operatingFlightnumber": "string",
      "seatCount": 0,
      "segmentIndex": 0,
      "stopCities": "string"
    }
  ],
  "retSegments": [
    {
      "aircraftCode": "string",
      "arrAirport": "string",
      "arrTerminal": "string",
      "arrTime": "string",
      "cabin": "string",
      "cabinClass": 1,
      "carrier": "string",
      "codeShare": true,
      "depAirport": "string",
      "depTerminal": "string",
      "depTime": "string",
      "duration": 0,
      "fareFamily": "string",
      "flightNumber": "string",
      "operatingCarrier": "string",
      "operatingFlightnumber": "string",
      "seatCount": 0,
      "segmentIndex": 0,
      "stopCities": "string"
    }
  ],
  "rule": {
    "hasBaggage": 0,
    "baggageElements": [
      {
        "segmentNo": 0,
        "baggageType": "StandardCheckInBaggage",
        "passengerType": 0,
        "baggagePiece": 0,
        "baggageWeight": 0,
        "baggageSize": "string",
        "isAllWeight": true
      }
    ],
    "refundRules": [
      {
        "refundType": 0,
        "refundStatus": "T",
        "refundFee": 0,
        "currency": "string",
        "refNoshow": "T",
        "refNoShowCondition": 0,
        "refNoshowFee": 0,
        "refundMethod": "CashBackToOriginalPayment",
        "ruleDetailList": [
          {
            "status": null,
            "startMinute": null,
            "endMinute": null,
            "amount": null,
            "currency": null,
            "refundMethod": null
          }
        ]
      }
    ],
    "changesRules": [
      {
        "changesType": 0,
        "changesStatus": "T",
        "changesFee": 0,
        "currency": "string",
        "revNoshow": "T",
        "revNoShowCondition": 0,
        "revNoshowFee": 0,
        "ruleDetailList": [
          {
            "status": null,
            "startMinute": null,
            "endMinute": null,
            "amount": null,
            "currency": null
          }
        ]
      }
    ],
    "serviceElements": [
      {
        "hasFreeSeat": 0,
        "hasFreeMeal": 0
      }
    ]
  },
  "ancillaryProductElements": [
    {
      "ancillaryCode": "string",
      "auxBaggageElement": {
        "isAllWeight": true,
        "piece": 0,
        "size": "string",
        "weight": 0
      },
      "canPurchasePostTicket": 0,
      "canPurchaseWithTicket": 0,
      "categoryCode": "StandardCheckInBaggage",
      "clientTechnicalServiceFee": 0,
      "currency": "string",
      "maxQty": 0,
      "minQty": 0,
      "price": 0,
      "productCode": "string",
      "segmentIndex": 0,
      "vendorCurrency": "string",
      "vendorPrice": 0
    }
  ],
  "vendorFare": {
    "vendorAdultPrice": 0,
    "vendorAdultTax": 0,
    "vendorChildPrice": 0,
    "vendorChildTax": 0,
    "vendorInfantPrice": 0,
    "vendorInfantTax": 0,
    "vendorCurrency": "string"
  },
  "links": {
    "carrier": "string",
    "kind": "string",
    "link": "string",
    "description": "string"
  },
  "separateBookings": true,
  "refreshTime": "string",
  "expireTime": "string",
  "ancillarySupported": [
    "string"
  ],
  "cardChargeList": [
    {
      "cardType": "Amex",
      "percentage": 0,
      "charge": 0,
      "currency": "string"
    }
  ]
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|routingIdentifier|string|true|none||This unique string identifier is used to verify requests for a particular route.<br />**Note:**<br />Has a certain validity period (generally not exceeding 6 hours).|
|supportCreditTransPayment|string|true|none||This tag is used to identify if the fare is support to be paid using the client's credit card(known as vcc passthrough). This field has been deprecated, please use `supportPaymentMethods` instead.|
|supportPaymentMethods|[[PaymentMethod](#schemapaymentmethod)]|true|none||Support payment methods for this fare. If payment is not supported in any way, this will be `null`or`[]`. Each item in this array is one of the following:<br />- 1: deposit<br />- 3: vcc passthrough<br />- 4: BYOA(Bring Your Own Account)<br />- 5: MoR|
|currency|string|true|none||The currency in which Atlas settles transactions with you.|
|adultPrice|number|true|none||Adult fare per passenger.|
|adultTax|number|true|none||Adult tax per passenger.|
|adultDetails|[[PriceItem](#schemapriceitem)]¦null|false|none||Details of the adult price composition.|
|childPrice|number|true|none||Child fare per passenger.|
|childTax|number|true|none||Child tax per passenger.|
|childDetails|[[PriceItem](#schemapriceitem)]¦null|false|none||Details of the child price composition.|
|infantPrice|number|true|none||Infant fare per passenger.|
|infantTax|integer|true|none||Infant tax per passenger.|
|infantDetails|[[PriceItem](#schemapriceitem)]¦null|false|none||Details of the child infant composition.|
|infantAllowed|boolean¦null|false|none||Since `infantPrice` and `infantTax` will never be `null`, when the fare does not support infants or is free for infants, both `infantPrice` and `infantTax` display `0`. In this case, you need this field to distinguish which situation it is.<br />**Scenario description:**<br />- `true`: infants is supported by this fare, `infantPrice` and `infantTax` will >= `0`<br />- `false`: infants is not supported by this fare, `infantPrice` and `infantTax`will be displayed as `0`|
|childMandatorySeatingFee|number¦null|false|none||Only valid for FR integration.<br /><br />**FR Seat Selection Rules:**<br />- Children under 12 years old are provided with free seats.<br />- Children must be seated in the same row as an adult.<br />- Each adult may accompany up to 4 children.<br /><br />For fare families that do not include seat selection fees (e.g., Basic or Family Plus), FR offers discounted seat selection fees for adults traveling with children. The`childMandatorySeatingFee`field displays this discounted fee.<br />For fare families that already include seat selection fees, this field will be `null`.<br /><br />**Handling by Atlas for Fare Families Without Seat Selection Fees:**<br />- The number of children cannot exceed 4.<br />- Customers cannot select seats manually.<br />- Atlas will automatically assign seats randomly to one adult and all children according to FR's rules. The adult will be charged the `childMandatorySeatingFee` for their seat.<br /><br />**For Fare Families That Include Seat Selection Fees:**<br />- Seat selection is free.<br />- Users may call the seat map API to select seats; otherwise, Atlas will automatically assign seats.|
|transactionFeePerPax|number|true|none||Technical service fee per passenger. This field has been deprecated and final total transaction fee will calculated based on `transactionFee` and `transactionFeeMode`.|
|transactionFee|number|true|none||Technical service fee as per `transactionFeeMode`. The following lists the calculation methods for the final technical service fee in various situations.<br />- `transactionFeeMode`=`PER_SEGMENT`:`transactionFee` * number of passengers * number of segments.<br />- `transactionFeeMode`=`PER_TICKET`:`transactionFee` * number of passengers * number of orders on airline side.<br />- `transactionFeeMode`=`PER_PAX`:`transactionFee` * number of passengers.<br />- `transactionFeeMode`=`PER_BOOKING`:`transactionFee`.|
|transactionFeeMode|[TransactionFeeMode](#schematransactionfeemode)|true|none||Calculation method for technical service fee.<br />- PER_SEGMENT: Calculate based on the number of segments in the order (number of travel segments * number of passengers)<br />- PER_TICKET: Calculate based on the number of orders on the airline's side<br />- PER_PAX: Calculate based on the number of passengers<br />- PER_BOOKING: Calculate based on each order|
|fromSegments|[[RoutingSegment](#schemaroutingsegment)]|true|none||For outbound segments.|
|retSegments|[[RoutingSegment](#schemaroutingsegment)]¦null|false|none||For inbound segments. For one-way, this field will be `null` or `[]`.|
|rule|object|true|none||none|
|» hasBaggage|integer|true|none||This tag is used to identify if the fare includes free checked-in or cabin baggage.<br />- `0`: Not included<br />- `1`: Included|
|» baggageElements|[object]|true|none||The free baggage allowance|
|»» segmentNo|integer|true|none||The index of segment the baggage allowance applies to.|
|»» baggageType|[AncillaryCategory](#schemaancillarycategory)|true|none||Type of the baggage.|
|»» passengerType|[PassengerType](#schemapassengertype)|true|none||The type of passenger the baggage allowance applies to.<br />- 0: Adult<br />- 1: Child<br />- 2: Infant|
|»» baggagePiece|integer|true|none||Baggage pieces:<br />- `0`: No limitation<br />- `>0`: Maximum pieces|
|»» baggageWeight|integer|true|none||Baggage Weight, with the unit of KG.<br />- `0`: No Free baggage<br />- `-1`: No limitation on weight<br />- `>0`: Maximum weight|
|»» baggageSize|string|true|none||Baggage Size:<br />length＊width＊height and units. eg. `56＊36＊23cm`, `18＊14＊8inch`.<br />Or Total dimensions (length + width + height) of each piece. eg. `L+W+H<=158cm`.<br />Empty means no limitation.|
|»» isAllWeight|boolean¦null|false|none||Baggage is all weight: true or false|
|» refundRules|[object]|true|none||This node is used to fetch the refund rules of the fare. There is only one array element for one way, and two elements for round-trip. The first element is for the outbound, and the second element is for the inbound.|
|»» refundType|integer|true|none||Type of refund allowed.<br />- 0: Wholly unused ticket<br />- 1: Partially used ticket (For example, when the passenger has used an outbound flight and wants to refund an inbound flight.)|
|»» refundStatus|[RefundStatus](#schemarefundstatus)|false|none||Refund rule types (for the most restrictive condition).<br />- T: Non refundable<br />- H: Refundable with restrictions<br />- F: Full refundable|
|»» refundFee|integer¦null|false|none||Refund penalty amount (for the most restrictive condition)|
|»» currency|string¦null|false|none||The currency of refund penalty|
|»» refNoshow|string|true|none||Indicates if a no-show affects refunds (for the most restrictive condition).<br />- T: Non refundable<br />- H: Refundable with restrictions<br />- F: Free for refund|
|»» refNoShowCondition|integer|true|none||Time before scheduled flight departure|
|»» refNoshowFee|number|true|none||Total refund fee (for the most restrictive condition): If refNoshow = H, it should not be "null". This value includes the refund fee and no-show penalty|
|»» refundMethod|string¦null|false|none||Refund method: CashBackToOriginalPayment or Voucher.<br />- CashBackToOriginalPayment: Refund cash back to the original form of payment.<br />- Voucher: Refund in the form of a voucher.|
|»» ruleDetailList|[[AirlineRuleRes](#schemaairlineruleres)]|false|none||none|
|» changesRules|[object]|true|none||This node is used to fetch the change rules of the fare. There is only one array element for one way, and two elements for round-trip. The first element is for the outbound, and the second element is for the inbound.|
|»» changesType|integer|true|none||Change flight type.<br />- `0`: Wholly unused ticket<br />- `1`: Partially used ticket (For example. When the passenger has used an outbound flight and wants to change an inbound flight)|
|»» changesStatus|[ChangeStatus](#schemachangestatus)|false|none||Change flight rule type (for the most restrictive condition):<br />- T: Non changeable<br />- H: Changeable with restrictions<br />- F: Free rescheduling|
|»» changesFee|number¦null|false|none||Change flight fee (for the most restrictive condition):<br />- If`changesStatus`=`H`, it should not be`null`<br />- If`changesStatus`=`T/F`, it can be`null`|
|»» currency|string¦null|false|none||The currency of change flight fee|
|»» revNoshow|string|true|none||Indicates if a no-show affects changes (for the most restrictive condition).<br />Valid values:<br />- T: Non changeable<br />- H: Changeable with restrictions<br />- F: Free flight change|
|»» revNoShowCondition|integer|true|none||Time before scheduled flight departure.|
|»» revNoshowFee|number|true|none||The total fee charged to change flight in case of no show. If revNoshow = H, it should not be "null." This value includes the change flight fee and no-show penalty.|
|»» ruleDetailList|[object]|false|none||Change conditions|
|»»» status|[RefundStatus](#schemarefundstatus)|true|none||Level of refund/change.<br />- T: Non refundable<br />- H: Refundable with restrictions<br />- F: Full refundable|
|»»» startMinute|string|true|none||Starting time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|»»» endMinute|string|true|none||Ending time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|»»» amount|string¦null|false|none||Penalty amount for refund/change. If the`status`indicates free refund/change, then this field will be either`0`or`null`.|
|»»» currency|string¦null|false|none||The currency of penalty|
|» serviceElements|[object]¦null|false|none||This function is used to fetch the other service rules of the fare. There is only one array for one way, and two arrays for round-trip. The first array is for the outbound, and the second array is for the inbound.|
|»» hasFreeSeat|integer|false|none||A marker used to indicate whether free seat selection is included.<br />- `0`: Not included<br />- `1`: Included<br />- `2`: Partially free|
|»» hasFreeMeal|integer|false|none||A marker used to indicate whether free meals are included.<br />- `0`: Not included<br />- `1`: Included|
|ancillaryProductElements|[[AncillaryProduct](#schemaancillaryproduct)]¦null|false|none||none|
|vendorFare|object|true|none||To identify the vendor’s fare with vendor’s currency. It is only available when`supportPaymentMethods`contains`3`or`4`.|
|» vendorAdultPrice|number|true|none||Adult fare per passenger in vendor’s currency|
|» vendorAdultTax|number|true|none||Adult tax per passenger in vendor’s currency|
|» vendorChildPrice|number|true|none||Child fare per passenger in vendor’s currency|
|» vendorChildTax|number|true|none||Child tax per passenger in vendor’s currency|
|» vendorInfantPrice|number|true|none||Infant fare per passenger in vendor’s currency|
|» vendorInfantTax|integer|true|none||Infant tax per passenger in vendor’s currency|
|» vendorCurrency|string|true|none||Vendor’s currency|
|links|[TAndCLink](#schematandclink)|true|none||The terms and conditions links of the airlines. Will only return in verify response.|
|separateBookings|boolean|true|none||When the outbound and inbound of round trip need to be booked separately, it will be true.|
|refreshTime|string|true|none||If the fare is from the cache of Atlas, this field is used to indicate the refresh time of the cache. The time is a certain moment in the past (UTC), and the format is:`yyyy-MM-dd'T'HH:mm:ss'Z'`.|
|expireTime|string|true|none||If the current fare comes from the cache of Atlas, this field is used to indicate the estimated expiration time of the cache. This time is a certain moment in the future (UTC), and the format is:`yyyy-MM-dd'T'HH:mm:ss'Z'`.<br />**Note:** <br />This time is estimated, which means Atlas may refresh the cache before or after that time.|
|ancillarySupported|[string]|true|none||A list of ancillary service types that the fare allows for additional purchase. Possible value contains:<br />- `luggage`<br />- `seat`: You can carry out the subsequent seat selection process through our seat map interface.|
|cardChargeList|[[CardCharge](#schemacardcharge)]¦null|false|none||Payment handling fee for MoR/VCC|

#### 枚举值

|属性|值|
|---|---|
|supportCreditTransPayment|0|
|supportCreditTransPayment|1|
|refundMethod|CashBackToOriginalPayment|
|refundMethod|Voucher|

<h2 id="tocS_PriceItem">PriceItem</h2>

<a id="schemapriceitem"></a>
<a id="schema_PriceItem"></a>
<a id="tocSpriceitem"></a>
<a id="tocspriceitem"></a>

```json
{
  "code": "string",
  "type": "base",
  "amount": 0,
  "description": "string"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|code|string|true|none||Machine readable code used to identify this price item.|
|type|string|true|none||Type of this price item.|
|amount|number|true|none||none|
|description|string¦null|false|none||Human-readable description for this price item.|

#### 枚举值

|属性|值|
|---|---|
|type|base|
|type|tax|
|type|fee|

<h2 id="tocS_TAndCLink">TAndCLink</h2>

<a id="schematandclink"></a>
<a id="schema_TAndCLink"></a>
<a id="tocStandclink"></a>
<a id="tocstandclink"></a>

```json
{
  "carrier": "string",
  "kind": "string",
  "link": "string",
  "description": "string"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|carrier|string|true|none||IATA code for the airline|
|kind|string|true|none||always:`terms`|
|link|string|true|none||URL to the carrier's terms and conditions|
|description|string|true|none||Carrier terms and conditions|

<h2 id="tocS_RoutingSegment">RoutingSegment</h2>

<a id="schemaroutingsegment"></a>
<a id="schema_RoutingSegment"></a>
<a id="tocSroutingsegment"></a>
<a id="tocsroutingsegment"></a>

```json
{
  "aircraftCode": "string",
  "arrAirport": "string",
  "arrTerminal": "string",
  "arrTime": "string",
  "cabin": "string",
  "cabinClass": 1,
  "carrier": "string",
  "codeShare": true,
  "depAirport": "string",
  "depTerminal": "string",
  "depTime": "string",
  "duration": 0,
  "fareFamily": "string",
  "flightNumber": "string",
  "operatingCarrier": "string",
  "operatingFlightnumber": "string",
  "seatCount": 0,
  "segmentIndex": 0,
  "stopCities": "string"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|aircraftCode|string¦null|false|none||IATA Code of aircraft type|
|arrAirport|string|true|none||3-letter iata code for the arrival airport at which the segment is scheduled to arrive.|
|arrTerminal|string¦null|false|none||The terminal at the destination airport where the segment is scheduled to arrive.|
|arrTime|string|true|none||The datetime at which the segment is scheduled to arrive, in the arrival airport timezone. The format is `YYYYMMDD`.|
|cabin|string¦null|false|none||RBD(known as Reservation Booking Designator) displayed by the airline.|
|cabinClass|[CabinClass](#schemacabinclass)|true|none||Cabin class of the segment.<br />- 1: economy<br />- 2: business<br />- 3: first<br />- 4: premium economy|
|carrier|string|true|none||IATA code of marketing carrier.|
|codeShare|boolean|true|none||A flag used to identify whether it is a code share flight.|
|depAirport|string|true|none||3-letter iata code for the airport at which the segment is scheduled to depart.|
|depTerminal|string¦null|false|none||The terminal at the departure airport from which the segment is scheduled to depart.|
|depTime|string|true|none||The datetime at which the segment is scheduled to depart, in the departure airport timezone. The format is`YYYYMMSS`.|
|duration|integer|true|none||The duration of the segment in munites.|
|fareFamily|string|true|none||Fare Family as per the information received from the airline|
|flightNumber|string|true|none||Marketing flight number. The format is: CA123 or TR021 or FR1290, with the first two letters representing the carrier and the following number representing the flight number.|
|operatingCarrier|string¦null|false|none||2-letter iata code for the operating carrier. The airline actually operating this segment. This may differ from the marketing carrier in the case of a "codeshare", where one airline sells flights operated by another airline.|
|operatingFlightnumber|string¦null|false|none||Operating flight number.|
|seatCount|integer|true|none||Max booking seats for the fare.|
|segmentIndex|integer|true|none||Segment sequence. Starts from 1. If it is return trip, sequence for outbound trip and inbound trip would be together. The segment index also represents the flight sequence of the segment.|
|stopCities|string¦null|false|none||IATA code/Name of cities from where the passengers will take stopover flights. Include IATA code of cities and use a comma in case of multiple cities to separate transfer airports count is higher than 1. For example: `CGK, SUB`. <br />`null` or blank means non-stop flight.|

<h2 id="tocS_AncillaryProduct">AncillaryProduct</h2>

<a id="schemaancillaryproduct"></a>
<a id="schema_AncillaryProduct"></a>
<a id="tocSancillaryproduct"></a>
<a id="tocsancillaryproduct"></a>

```json
{
  "ancillaryCode": "string",
  "auxBaggageElement": {
    "isAllWeight": true,
    "piece": 0,
    "size": "string",
    "weight": 0
  },
  "canPurchasePostTicket": 0,
  "canPurchaseWithTicket": 0,
  "categoryCode": "StandardCheckInBaggage",
  "clientTechnicalServiceFee": 0,
  "currency": "string",
  "maxQty": 0,
  "minQty": 0,
  "price": 0,
  "productCode": "string",
  "segmentIndex": 0,
  "vendorCurrency": "string",
  "vendorPrice": 0
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|ancillaryCode|string|true|none||A code that is relatively readable by humans and contains information about auxiliary business specifications (such as weight and quantity limitations of luggage). <br />**Note:** <br />This content is only for display purposes and should not be used for programming purposes. That is to say, do not attempt to parse the information about auxiliary business specifications from this code. If you want to access the auxiliary business specifications, please use structured fields. For example, for luggage, please use`auxBaggageElement`.|
|auxBaggageElement|object¦null|false|none||Baggage specification limitations. This node is valid only when the ancillary type (`categoryCode`) is baggage.|
|» isAllWeight|boolean|true|none||Mark whether the`weight`field restricts the total weight or the weight of a single piece.<br />- `true`: The weight is for all the pieces<br />- `false`: The weight is for each piece|
|» piece|integer|true|none||The maximum number of pieces that can be purchased per person.<br />- `0`: No Limitation about piece<br />- `>0`: Maximum pieces|
|» size|string¦null|false|none||Maximum size for the baggage|
|» weight|integer|true|none||The maximum weight that can be purchased per person.<br />- `0`: No limitation for weight<br />- `>0`: Weight limit (KG)|
|canPurchasePostTicket|integer|true|none||A flag used to mark if this ancillary product can be purchased in the post-ticketing flow.<br />- `0`: No<br />- `1`: Yes|
|canPurchaseWithTicket|integer|true|none||A flag used to mark if this ancillary product can be purchased during the booking flow.<br />- `0`: No<br />- `1`: Yes|
|categoryCode|[AncillaryCategory](#schemaancillarycategory)|true|none||Type of the ancillary.<br /><br />- StandardCheckInBaggage: Standard Check-in Baggage.<br />- CabinBaggage: Usually refers to the Cabin Baggage Overhead Locker. Transition value. It will gradually transition to `CabinBaggageOverheadLocker`.<br />- CabinBaggageOverheadLocker: Cabin Baggage Overhead Locker.<br />- CabinBaggageUnderSeat: Cabin Baggage Under Seat. Usually refers to the personal item.|
|clientTechnicalServiceFee|number¦null|false|none||The service fee charged by Atlas for the purchase of the ancillary.|
|currency|string|true|none||The currency in which Atlas settles transactions with you|
|maxQty|integer|true|none||The maximum number of purchases allowed per person per flight segment|
|minQty|integer|true|none||The minimum quantity allowed to be purchased per person per flight segment.|
|price|number|true|none||Price for this ancillary.|
|productCode|string|true|none||Unique identifier for the ancillary product. It would be used in the order request.|
|segmentIndex|integer|true|none||The index of segment the ancillary applies to.|
|vendorCurrency|string|true|none||The currency in which the vendor charges for the ancillary. If the fare does not allow for the VCC pass-through or BYOA payment, this information will be`null`.|
|vendorPrice|integer|true|none||The price charged by the vendor for the ancillary. If the fare does not allow for the VCC pass-through or BYOA payment, this information will be`null`.|

<h2 id="tocS_CardCharge">CardCharge</h2>

<a id="schemacardcharge"></a>
<a id="schema_CardCharge"></a>
<a id="tocScardcharge"></a>
<a id="tocscardcharge"></a>

```json
{
  "cardType": "Amex",
  "percentage": 0,
  "charge": 0,
  "currency": "string"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|cardType|[CardType](#schemacardtype)|true|none||Card types, such as Visa, MasterCard|
|percentage|number¦null|false|none||Percentage of payment handling fee|
|charge|number¦null|false|none||The amount of payment handling fee|
|currency|string¦null|false|none||Currency of `charge`|

<h2 id="tocS_AirlineRuleRes">AirlineRuleRes</h2>

<a id="schemaairlineruleres"></a>
<a id="schema_AirlineRuleRes"></a>
<a id="tocSairlineruleres"></a>
<a id="tocsairlineruleres"></a>

```json
{
  "status": "T",
  "startMinute": "string",
  "endMinute": "string",
  "amount": "string",
  "currency": "string",
  "refundMethod": "CashBackToOriginalPayment"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|status|[RefundStatus](#schemarefundstatus)|true|none||Level of refund/change.<br />- T: Non refundable<br />- H: Refundable with restrictions<br />- F: Full refundable|
|startMinute|string|true|none||Starting time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|endMinute|string|true|none||Ending time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|amount|string¦null|false|none||Penalty amount for refund/change. If the`status`indicates free refund/change, then this field will be either`0`or`null`.|
|currency|string¦null|false|none||The currency of penalty|
|refundMethod|string¦null|false|none||Refund method: CashBackToOriginalPayment or Voucher.<br />- CashBackToOriginalPayment: Refund cash back to the original form of payment.<br />- Voucher: Refund in the form of a voucher.|

#### 枚举值

|属性|值|
|---|---|
|refundMethod|CashBackToOriginalPayment|
|refundMethod|Voucher|

<h2 id="tocS_ResponseMessage">ResponseMessage</h2>

<a id="schemaresponsemessage"></a>
<a id="schema_ResponseMessage"></a>
<a id="tocSresponsemessage"></a>
<a id="tocsresponsemessage"></a>

```json
"string"

```

It serves as an additional description of the response result. Especially when the interface reports an error (`status` !=`0`), it is usually a human-readable error message. Note: Do not use this field in any programming scenarios. For example, do not judge whether the interface responds successfully based on this field. Instead, you should only determine it by checking whether the status is equal to`0`at any time.

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|string|false|none||It serves as an additional description of the response result. Especially when the interface reports an error (`status` !=`0`), it is usually a human-readable error message. Note: Do not use this field in any programming scenarios. For example, do not judge whether the interface responds successfully based on this field. Instead, you should only determine it by checking whether the status is equal to`0`at any time.|

<h2 id="tocS_PaymentOption">PaymentOption</h2>

<a id="schemapaymentoption"></a>
<a id="schema_PaymentOption"></a>
<a id="tocSpaymentoption"></a>
<a id="tocspaymentoption"></a>

```json
{
  "paymentMethod": 1,
  "ticketFare": {
    "amount": 0,
    "currency": "string",
    "deductFrom": "DEPOSIT"
  },
  "serviceFee": {
    "amount": 0,
    "currency": "string",
    "deductFrom": "DEPOSIT"
  },
  "paymentFee": {
    "amount": 0,
    "currency": "string",
    "deductFrom": "DEPOSIT"
  },
  "cardType": "string"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|paymentMethod|[PaymentMethod](#schemapaymentmethod)|true|none||Payment method.<br />- 1: balance<br />- 3: vcc passthrough<br />- 4: BYOA<br />- 5: MoR|
|ticketFare|[PaymentOptionDetail](#schemapaymentoptiondetail)|true|none||It is used to describe the total ticket price and how the deduction will be made.|
|serviceFee|[PaymentOptionDetail](#schemapaymentoptiondetail)|false|none||It is used to describe the total service and how the deduction will be made.|
|paymentFee|[PaymentOptionDetail](#schemapaymentoptiondetail)|false|none||It is used to describe the payment fee and how the deduction will be made.|
|cardType|string¦null|false|none||Only for MoR. Echo the card type you sent in order request.|

<h2 id="tocS_PaymentOptionDetail">PaymentOptionDetail</h2>

<a id="schemapaymentoptiondetail"></a>
<a id="schema_PaymentOptionDetail"></a>
<a id="tocSpaymentoptiondetail"></a>
<a id="tocspaymentoptiondetail"></a>

```json
{
  "amount": 0,
  "currency": "string",
  "deductFrom": "DEPOSIT"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|amount|number|true|none||Total amount will be deducted.|
|currency|string|true|none||Currency of the`amount`|
|deductFrom|string|true|none||Deduction method|

#### 枚举值

|属性|值|
|---|---|
|deductFrom|DEPOSIT|
|deductFrom|CARD|

<h2 id="tocS_OrderPax">OrderPax</h2>

<a id="schemaorderpax"></a>
<a id="schema_OrderPax"></a>
<a id="tocSorderpax"></a>
<a id="tocsorderpax"></a>

```json
{
  "name": "string",
  "passengerType": 0,
  "gender": "string",
  "birthday": "string",
  "cardType": "PP",
  "cardNum": "string",
  "cardIssuePlace": "string",
  "cardExpired": "string",
  "nationality": "string",
  "ffpCardNo": "string",
  "ffpCarrier": "string",
  "ancillaries": [
    {
      "productCode": "string",
      "segmentIndex": 0
    }
  ],
  "residentInfo": {
    "docType": "string",
    "docNum": "string",
    "municipality": "string",
    "largeFamilyCert": "string",
    "community": "string"
  }
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|name|string|true|none||The passenger's name. Please send it in the following format: Family Name/Given Name|
|passengerType|[PassengerType](#schemapassengertype)|true|none||Type of passenger.<br />- 0: Adult<br />- 1: Child<br />- 2: Infant|
|gender|string|true|none||The passenger's gender.<br />- `M`: Male<br />- `F`: Female|
|birthday|string¦null|false|none||The passenger's date of birth. Format:`YYYYMMDD`. Please fill in according to the passenger information requirements(`bookingRequirement`) returned by the Verification / Get Offer API.|
|cardType|string¦null|false|none||The type of the identity document.<br />- PP: Passport<br />- GA: Hong Kong Macau Pass for China mainland citizens<br />- TW: Taiwan Pass for China mainland citizens<br />- TB: China mainland pass for Taiwanese<br />- HY: International Seaman's Certificate|
|cardNum|string¦null|false|none||The unique identifier of the identity document. e.g. the passport number. Please fill in according to the passenger information requirements(`bookingRequirement`) returned by the Verification / Get Offer API.|
|cardIssuePlace|string¦null|false|none||The ISO 3166-1 alpha-2 code for the country where the identity document is issued. Please fill in according to the passenger information requirements(`bookingRequirement`) returned by the Verification / Get Offer API.|
|cardExpired|string¦null|false|none||The date on which the identity document expires. Format:`YYYYMMDD`.Please fill in according to the passenger information requirements(`bookingRequirement`) returned by the Verification / Get Offer API.|
|nationality|string¦null|false|none||The ISO 3166-1 alpha-2 code for the nationality of passenger. Please fill in according to the passenger information requirements(`bookingRequirement`) returned by the Verification / Get Offer API.|
|ffpCardNo|string¦null|false|none||The passenger's account number for this frequent flyer account|
|ffpCarrier|string¦null|false|none||The IATA code for the airline that this frequent flyer account belongs to|
|ancillaries|[object]¦null|false|none||Ancillaries selection for the specific passenger|
|» productCode|string|true|none||Ancillary product code(`productCode`). Got from routing element in the search/revalidation response.|
|» segmentIndex|integer|true|none||Segment sequence|
|residentInfo|object¦null|false|none||Resident Info|
|» docType|string|true|none||Certificate types supported by resident' prices|
|» docNum|string¦null|false|none||ID number, if the ID type is D, E|
|» municipality|string¦null|false|none||Municipal district code|
|» largeFamilyCert|string¦null|false|none||Large Family Cert|
|» community|string¦null|false|none||Community Region Code|

#### 枚举值

|属性|值|
|---|---|
|cardType|PP|
|cardType|GA|
|cardType|TW|
|cardType|TB|
|cardType|HY|

<h2 id="tocS_OrderPaxTicket">OrderPaxTicket</h2>

<a id="schemaorderpaxticket"></a>
<a id="schema_OrderPaxTicket"></a>
<a id="tocSorderpaxticket"></a>
<a id="tocsorderpaxticket"></a>

```json
{
  "name": "string",
  "passengerType": 0,
  "birthday": "string",
  "gender": "string",
  "cardNum": "string",
  "cardType": "string",
  "cardIssuePlace": "string",
  "cardExpired": "string",
  "nationality": "string",
  "ticketNos": [
    "string"
  ],
  "airlinePNRs": [
    "string"
  ],
  "ancillaries": [
    {
      "productCode": "string",
      "segmentIndex": 0,
      "currency": "string",
      "ancillaryPrice": 0,
      "auxBaggageElement": {
        "isAllWeight": true,
        "piece": 0,
        "size": "string",
        "weight": 0
      },
      "auxSeatElement": {
        "row": "27",
        "column": "A"
      },
      "vendorCurrency": "string",
      "vendorPrice": 0,
      "displayCurrency": "string",
      "displayPrice": 0
    }
  ],
  "contactEmails": [
    "test@test.com"
  ],
  "contactPhones": [
    "0001-87291810"
  ]
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|name|string|true|none||Echo the passenger's name, in the format of last name/first name|
|passengerType|[PassengerType](#schemapassengertype)|true|none||Echo the passenger's type.<br />- 0: Adult<br />- 1: Child<br />- 2: Infant|
|birthday|string|true|none||Echo the passenger's birthday|
|gender|string|true|none||Echo the passenger's gender|
|cardNum|string¦null|false|none||Echo the passenger's  identity document number|
|cardType|string¦null|false|none||Echo the passenger's  identity document type|
|cardIssuePlace|string¦null|false|none||Echo the country where the passenger's identification document was issued.|
|cardExpired|string¦null|false|none||Echo the expiration date of the passenger's identification document.|
|nationality|string¦null|false|none||Echo the passenger's nationality|
|ticketNos|[string]|true|none||Ticket numbers. There may be two tickets for the round trip, in which case the number of arrays is two.|
|airlinePNRs|[string]|true|none||A list containing airline PNR. There may be two PNRs for the round trip, in which case the number of arrays is two.|
|ancillaries|[object]¦null|false|none||Ancillaries selection for the specific passenger|
|» productCode|string|true|none||Unique identifier for the ancillary product.|
|» segmentIndex|integer|true|none||The index of segment the ancillary applies to.|
|» currency|string|true|none||The currency in which Atlas settles transactions with you|
|» ancillaryPrice|number|true|none||Price for this ancillary.|
|» auxBaggageElement|object¦null|false|none||Baggage specification limitations. This node is valid only when the ancillary type (`categoryCode`) is baggage.|
|»» isAllWeight|boolean|true|none||Mark whether the`weight`field restricts the total weight or the weight of a single piece.<br />- `true`: The weight is for all the pieces<br />- `false`: The weight is for each piece|
|»» piece|integer|true|none||The maximum number of pieces that can be purchased per person.<br />- `0`: No Limitation about piece<br />- `>0`: Maximum pieces|
|»» size|string¦null|false|none||Maximum size for the baggage|
|»» weight|integer|true|none||The maximum weight that can be purchased per person.<br />- `0`: No limitation for weight<br />- `>0`: Weight limit (KG)|
|» auxSeatElement|object¦null|false|none||Seat selection for the specific passenger|
|»» row|string|true|none||Seat row|
|»» column|string|true|none||Seat column|
|» vendorCurrency|string|false|none||The currency in which the vendor charges for the ancillary. If the fare does not allow for the VCC pass-through or BYOA payment, this information will be`null`.|
|» vendorPrice|integer|false|none||The price charged by the vendor for the ancillary. If the fare does not allow for the VCC pass-through or BYOA payment, this information will be`null`.|
|» displayCurrency|string¦null|false|none||Display currency|
|» displayPrice|number¦null|false|none||Display price|
|contactEmails|[string]¦null|false|none||Passenger contact email address.|
|contactPhones|[string]¦null|false|none||Passenger contact phone number.|

<h2 id="tocS_OrderResponsePostbooking">OrderResponsePostbooking</h2>

<a id="schemaorderresponsepostbooking"></a>
<a id="schema_OrderResponsePostbooking"></a>
<a id="tocSorderresponsepostbooking"></a>
<a id="tocsorderresponsepostbooking"></a>

```json
{
  "status": 301,
  "msg": "string",
  "sessionId": "string",
  "offerId": "string",
  "orderNo": "string",
  "pnrCode": "string",
  "totalPrice": 0,
  "totalTransactionFee": 0,
  "currency": "string",
  "vendorTotalPrice": 0,
  "vendorCurrency": "string",
  "tktLimitTime": "string",
  "paxTicketInfos": [
    {
      "name": "string",
      "passengerType": 0,
      "birthday": "string",
      "gender": "string",
      "cardNum": "string",
      "cardType": "string",
      "cardIssuePlace": "string",
      "cardExpired": "string",
      "nationality": "string",
      "ticketNos": [
        "string"
      ],
      "airlinePNRs": [
        "string"
      ],
      "ancillaries": [
        {
          "productCode": "string",
          "segmentIndex": 0,
          "currency": "string",
          "ancillaryPrice": 0,
          "auxBaggageElement": {
            "isAllWeight": null,
            "piece": null,
            "size": null,
            "weight": null
          },
          "auxSeatElement": {
            "row": null,
            "column": null
          },
          "vendorCurrency": "string",
          "vendorPrice": 0,
          "displayCurrency": "string",
          "displayPrice": 0
        }
      ],
      "contactEmails": [
        "test@test.com"
      ],
      "contactPhones": [
        "0001-87291810"
      ]
    }
  ],
  "routing": {
    "routingIdentifier": "string",
    "supportCreditTransPayment": "1",
    "supportPaymentMethods": [
      1
    ],
    "currency": "string",
    "adultPrice": 0,
    "adultTax": 0,
    "adultDetails": [
      {
        "code": "string",
        "type": "base",
        "amount": 0,
        "description": "string"
      }
    ],
    "childPrice": 0,
    "childTax": 0,
    "childDetails": [
      {
        "code": "string",
        "type": "base",
        "amount": 0,
        "description": "string"
      }
    ],
    "infantPrice": 0,
    "infantTax": 0,
    "infantDetails": [
      {
        "code": "string",
        "type": "base",
        "amount": 0,
        "description": "string"
      }
    ],
    "infantAllowed": true,
    "childMandatorySeatingFee": 0,
    "transactionFeePerPax": 0,
    "transactionFee": 0,
    "transactionFeeMode": "PER_PAX",
    "fromSegments": [
      {
        "aircraftCode": "string",
        "arrAirport": "string",
        "arrTerminal": "string",
        "arrTime": "string",
        "cabin": "string",
        "cabinClass": 1,
        "carrier": "string",
        "codeShare": true,
        "depAirport": "string",
        "depTerminal": "string",
        "depTime": "string",
        "duration": 0,
        "fareFamily": "string",
        "flightNumber": "string",
        "operatingCarrier": "string",
        "operatingFlightnumber": "string",
        "seatCount": 0,
        "segmentIndex": 0,
        "stopCities": "string"
      }
    ],
    "retSegments": [
      {
        "aircraftCode": "string",
        "arrAirport": "string",
        "arrTerminal": "string",
        "arrTime": "string",
        "cabin": "string",
        "cabinClass": 1,
        "carrier": "string",
        "codeShare": true,
        "depAirport": "string",
        "depTerminal": "string",
        "depTime": "string",
        "duration": 0,
        "fareFamily": "string",
        "flightNumber": "string",
        "operatingCarrier": "string",
        "operatingFlightnumber": "string",
        "seatCount": 0,
        "segmentIndex": 0,
        "stopCities": "string"
      }
    ],
    "rule": {
      "hasBaggage": 0,
      "baggageElements": [
        {
          "segmentNo": 0,
          "baggageType": "[",
          "passengerType": "[",
          "baggagePiece": 0,
          "baggageWeight": 0,
          "baggageSize": "string",
          "isAllWeight": true
        }
      ],
      "refundRules": [
        {
          "refundType": 0,
          "refundStatus": "[",
          "refundFee": 0,
          "currency": "string",
          "refNoshow": "T",
          "refNoShowCondition": 0,
          "refNoshowFee": 0,
          "refundMethod": "[",
          "ruleDetailList": [
            null
          ]
        }
      ],
      "changesRules": [
        {
          "changesType": 0,
          "changesStatus": "[",
          "changesFee": 0,
          "currency": "string",
          "revNoshow": "T",
          "revNoShowCondition": 0,
          "revNoshowFee": 0,
          "ruleDetailList": [
            null
          ]
        }
      ],
      "serviceElements": [
        {
          "hasFreeSeat": 0,
          "hasFreeMeal": 0
        }
      ]
    },
    "ancillaryProductElements": [
      {
        "ancillaryCode": "string",
        "auxBaggageElement": {
          "isAllWeight": true,
          "piece": 0,
          "size": "string",
          "weight": 0
        },
        "canPurchasePostTicket": 0,
        "canPurchaseWithTicket": 0,
        "categoryCode": "StandardCheckInBaggage",
        "clientTechnicalServiceFee": 0,
        "currency": "string",
        "maxQty": 0,
        "minQty": 0,
        "price": 0,
        "productCode": "string",
        "segmentIndex": 0,
        "vendorCurrency": "string",
        "vendorPrice": 0
      }
    ],
    "vendorFare": {
      "vendorAdultPrice": 0,
      "vendorAdultTax": 0,
      "vendorChildPrice": 0,
      "vendorChildTax": 0,
      "vendorInfantPrice": 0,
      "vendorInfantTax": 0,
      "vendorCurrency": "string"
    },
    "links": {
      "carrier": "string",
      "kind": "string",
      "link": "string",
      "description": "string"
    },
    "separateBookings": true,
    "refreshTime": "string",
    "expireTime": "string",
    "ancillarySupported": [
      "string"
    ],
    "cardChargeList": [
      {
        "cardType": "Amex",
        "percentage": 0,
        "charge": 0,
        "currency": "string"
      }
    ]
  },
  "paymentOptions": [
    {
      "paymentMethod": 0,
      "serviceFee": {
        "paymentMethod": 1,
        "ticketFare": {
          "amount": 0,
          "currency": "string",
          "deductFrom": "["
        },
        "serviceFee": {
          "amount": 0,
          "currency": "string",
          "deductFrom": "["
        },
        "paymentFee": {
          "amount": 0,
          "currency": "string",
          "deductFrom": "["
        },
        "cardType": "string"
      },
      "ticketFare": {
        "paymentMethod": 1,
        "ticketFare": {
          "amount": 0,
          "currency": "string",
          "deductFrom": "["
        },
        "serviceFee": {
          "amount": 0,
          "currency": "string",
          "deductFrom": "["
        },
        "paymentFee": {
          "amount": 0,
          "currency": "string",
          "deductFrom": "["
        },
        "cardType": "string"
      },
      "paymentFee": {
        "paymentMethod": 1,
        "ticketFare": {
          "amount": 0,
          "currency": "string",
          "deductFrom": "["
        },
        "serviceFee": {
          "amount": 0,
          "currency": "string",
          "deductFrom": "["
        },
        "paymentFee": {
          "amount": 0,
          "currency": "string",
          "deductFrom": "["
        },
        "cardType": "string"
      },
      "cardType": "string"
    }
  ],
  "ticketOrderNo": "string"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|status|[OrderResponseStatus](#schemaorderresponsestatus)|true|none||- 301: Session does not exist or timed out. Description: The "sessionID" has a validity of 2 hrs. If the “sessionID” is used after this time period, then this error is displayed<br />- 302: The target flight is no longer available. Description: In the period between verify and book, the flight has been sold out. This can also be due to the number of passengers booked. The number of pax when booking and the number of pax when verifying may be different. When create a booking, the price is verified based on the actual number of pax booked<br />- 303: Airline closed. Description: Airline has either ceased to exist or not operational.<br />- 304: Verify failed. Description: In some uncontrollable situations, such as network issues, upgrades, and restarts, 304 error may occur, but not many. If there are many 304 errors, it is possible that the airline is not available or some technical issue at Atlas' end. Contact your account manager if this error keeps on repeating.<br />- 305: Invalid routing. Description: When generating an order, the system found that the flight was no longer sold for various reasons, such as 1) L2B 2) The system has identified that there may be a risk of the flight being sold out 3) The airline's sales have been closed<br />- 307: Illegal booking request parameters. Description: Some request parameters have problem. Please check the message.<br />- 308: Price changed. Description: The price has changed between the price verification and order. Please verify the price again and generate the order.<br />- 309: Ancillary not found. Description: Incorrect ancillary product code has been entered. Check and enter the correct ancillary product code.<br />- 310: Infant not allowed. Description: The offer does not support infant. Create a new booking without infant passenger type.<br />- 312: Too many seats booked. Description: The number of pax booked exceeds the remaining (or allowed) seats on the current flight.<br />- 313: Fare family sold out. Description: Selected offer is no longer available. Conduct the search again and rebook.<br />- 315: Not enough seats. Description: Seats have been sold out<br />- 316: Timed out. Description: There is a time-out error at the airline’s end<br />- 317: Booking unsuccessful with Airline. Description: An error has happened at the airline’s end.<br />- 318: Check if a booking with the same passenger details and flight numbers exists. After confirming, ignore this booking.<br />- 319: Flight information has changed. Description: Re-verify the price (query the latest flight information) and generate the order.<br />- 320: The requested seats were not found or they are already occupied. Description: Rebook seats and submit a new order.<br />- 321: <br />- 322: Seat price changed. Description: Seat price changed. Re-query the seat map and select seats<br />- 323: The format of the e-mail in the contact information is incorrect<br />- 324: Airline system issues. Description: Retry after some time. If the issue persists, please contact our operations team.<br />- 325: The airline has deemed the passenger unserviceable<br />- 326: Your account balance on the airline side is insufficient(BYOA scenario)<br />- 327: Passenger information does not meet the requirements. Description: Check and correct the passenger information according to the error message<br />- 328: Selected seat is no longer available. Description: The selected seat has been occupied.<br />- 329: No payment method is available. Description: No payment method is available. Please check whether the quotation currency or account configuration is correct.<br />- 330: operation is in progress. Description: operation is in progress|
|msg|[ResponseMessage](#schemaresponsemessage)|true|none||It serves as an additional description of the response result. Especially when the interface reports an error (`status` !=`0`), it is usually a human-readable error message. Note: Do not use this field in any programming scenarios. For example, do not judge whether the interface responds successfully based on this field. Instead, you should only determine it by checking whether the status is equal to`0`at any time.|
|sessionId|string|true|none||Echo the`sessionId`in the request parameters.|
|offerId|string¦null|false|none||Echo the`offerId`in the request parameters.|
|orderNo|string|true|none||Order number of the created order.|
|pnrCode|string|true|none||The pnrCode is the single reference for the booking. This is the Atlas PNR, not airline's.|
|totalPrice|number|true|none||Total price(not including service fee) of this order in the currency TheAtlas settled with you|
|totalTransactionFee|number|true|none||Total technical fees for this order in the currency TheAtlas settled with you.|
|currency|string|true|none||The currency TheAtlas settled with you.|
|vendorTotalPrice|number¦null|false|none||Total price of this order in the vendor's currency, reference for you to generate the specific credit card.|
|vendorCurrency|string¦null|false|none||Vendor's currency.|
|tktLimitTime|string|true|none||Payment deadline for this order. This time will be displayed in SGT (GMT +8). The fromat is:`yyyy-MM-dd HH:mm:ss`.|
|paxTicketInfos|[object]|true|none||Ticket information for passengers. The number of elements is the same as the number of passengers, with each passenger corresponding to one element.|
|» name|string|true|none||Echo the passenger's name, in the format of last name/first name|
|» passengerType|[PassengerType](#schemapassengertype)|true|none||Echo the passenger's type.<br />- 0: Adult<br />- 1: Child<br />- 2: Infant|
|» birthday|string|true|none||Echo the passenger's birthday|
|» gender|string|true|none||Echo the passenger's gender|
|» cardNum|string¦null|false|none||Echo the passenger's  identity document number|
|» cardType|string¦null|false|none||Echo the passenger's  identity document type|
|» cardIssuePlace|string¦null|false|none||Echo the country where the passenger's identification document was issued.|
|» cardExpired|string¦null|false|none||Echo the expiration date of the passenger's identification document.|
|» nationality|string¦null|false|none||Echo the passenger's nationality|
|» ticketNos|[string]|true|none||Ticket numbers. Since the ticket hasn't been issued at this moment, the array will be empty(`[]`).|
|» airlinePNRs|[string]|true|none||Since the airline side hasn't generated the order yet, the array is empty(`[]`).|
|» ancillaries|[object]¦null|false|none||Ancillaries selection for the specific passenger|
|»» productCode|string|true|none||Unique identifier for the ancillary product.|
|»» segmentIndex|integer|true|none||The index of segment the ancillary applies to.|
|»» currency|string|true|none||The currency in which Atlas settles transactions with you|
|»» ancillaryPrice|number|true|none||Price for this ancillary.|
|»» auxBaggageElement|object¦null|false|none||Baggage specification limitations. This node is valid only when the ancillary type (`categoryCode`) is baggage.|
|»»» isAllWeight|boolean|true|none||Mark whether the`weight`field restricts the total weight or the weight of a single piece.<br />- `true`: The weight is for all the pieces<br />- `false`: The weight is for each piece|
|»»» piece|integer|true|none||The maximum number of pieces that can be purchased per person.<br />- `0`: No Limitation about piece<br />- `>0`: Maximum pieces|
|»»» size|string¦null|false|none||Maximum size for the baggage|
|»»» weight|integer|true|none||The maximum weight that can be purchased per person.<br />- `0`: No limitation for weight<br />- `>0`: Weight limit (KG)|
|»» auxSeatElement|object¦null|false|none||Seat selection for the specific passenger|
|»»» row|string|true|none||Seat row|
|»»» column|string|true|none||Seat column|
|»» vendorCurrency|string|false|none||The currency in which the vendor charges for the ancillary. If the fare does not allow for the VCC pass-through or BYOA payment, this information will be`null`.|
|»» vendorPrice|integer|false|none||The price charged by the vendor for the ancillary. If the fare does not allow for the VCC pass-through or BYOA payment, this information will be`null`.|
|»» displayCurrency|string¦null|false|none||Display currency|
|»» displayPrice|number¦null|false|none||Display price|
|» contactEmails|[string]¦null|false|none||Passenger contact email address.|
|» contactPhones|[string]¦null|false|none||Passenger contact phone number.|
|routing|[Routing](#schemarouting)|true|none||none|
|paymentOptions|[object]|true|none||Available paymebt options for this order|
|» paymentMethod|integer|true|none||none|
|» serviceFee|[PaymentOption](#schemapaymentoption)|true|none||none|
|» ticketFare|[PaymentOption](#schemapaymentoption)|true|none||none|
|» paymentFee|[PaymentOption](#schemapaymentoption)|true|none||none|
|» cardType|string¦null|true|none||none|
|ticketOrderNo|string¦null|false|none||Order number. It is the original order number.|

<h2 id="tocS_PNRClaimFlight">PNRClaimFlight</h2>

<a id="schemapnrclaimflight"></a>
<a id="schema_PNRClaimFlight"></a>
<a id="tocSpnrclaimflight"></a>
<a id="tocspnrclaimflight"></a>

```json
{
  "carrier": "string",
  "flightNumber": "string",
  "depAirport": "string",
  "arrAirport": "string",
  "depTime": "string",
  "arrTime": "string",
  "stopCities": "string",
  "codeShare": 0,
  "operatingCarrier": "string",
  "operatingFlightNumber": "string",
  "depTerminal": "string",
  "arrTerminal": "string",
  "cabinClass": 1,
  "fareFamily": "string",
  "duration": 0
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|carrier|string|true|none||IATA code of the marketing airline|
|flightNumber|string|true|none||The value denotes the marketing flight number.<br />Format: CA123 or TR021 or FR1290. The letters denote the carrier and the three/four-digit number that follows is the flight number.|
|depAirport|string|true|none||IATA code of the departure airport.|
|arrAirport|string|true|none||IATA code of the arrival airport.|
|depTime|string|true|none||Departure time of the flight. Format:`yyyyMMddHHmm`|
|arrTime|string¦null|false|none||Arrival time of the flight. Format:`yyyyMMddHHmm`|
|stopCities|string¦null|false|none||Name of cities from where the passengers will take connecting flights. Include IATA code of cities and use a comma in case of multiple cities to separate if transfer airports count is higher than 1. For example: CGK, SUB. Blank means non-stop flight.|
|codeShare|integer¦null|false|none||- 1: code share<br />- 0: Not code share|
|operatingCarrier|string¦null|false|none||Operating carrier. It is blank when codeshare=false|
|operatingFlightNumber|string¦null|false|none||Operating flight number. It is blank when codeshare=false|
|depTerminal|string¦null|false|none||Departure Terminal|
|arrTerminal|string¦null|false|none||Arrival Terminal|
|cabinClass|[CabinClass](#schemacabinclass)|false|none||Service grade of the fare|
|fareFamily|string¦null|false|none||Fare Family as per the information received from the airline.|
|duration|integer¦null|false|none||The flying duration in minutes.|

<h2 id="tocS_OrderPayment">OrderPayment</h2>

<a id="schemaorderpayment"></a>
<a id="schema_OrderPayment"></a>
<a id="tocSorderpayment"></a>
<a id="tocsorderpayment"></a>

```json
{
  "cardType": "Amex"
}

```

Payment information

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|cardType|[CardType](#schemacardtype)|true|none||The card type you wish to use for payment. Send this information when generating an order can be used to calculate the payment handling fee. This parameter is only effective and required in the MoR payment scenario.|

