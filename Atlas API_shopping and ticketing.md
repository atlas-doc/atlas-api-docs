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

# Shopping and Ticketing

## POST Search

POST /search.do

**Dependency:**
No preceding function needs to be called before Search.

> **The search results will include a lot of items. Some highlights are:** 
> - The returned currency is by configuration according to the business agreement between you and Atlas
> - The total cost to purchase for a single adult passenger is: `adultPrice`+`adultTax`+`transactionFeePerPax`
> - For the airlines which support pass through payment method, we would set `supportCreditTransPayment` to `1` and present the vendor's fare in the `vendorFare` element. Alternatively, if the airline doesn't support pass through payment method, we would set `supportCreditTransPayment` to `0` and the `vendorFare` element will be `null`.
> - You can choose to show or hide `ancillaryProductElements` in search response, according to the configuration of each client in the backend system.
> - The `links` element will have the link to the terms and conditions of the airlines.
> - Display Currency is only to be used for display purposes. The amount in the response is not to be used for fare comparison or accounting purposes. The display currency conversion will be available in fares, taxes and ancillary baggage sections of the search and verify response. When the "vendorFare" element is available, the conversion will be from the vendor fare. In the absence of the "vendorFare" element, the conversion would be from the transacted fare.

**Endpoint:**
https://sandbox.atriptech.com/search.do

> Body 请求参数

```json
{
  "tripType": "2",
  "adultNum": 1,
  "childNum": 0,
  "infantNum": 0,
  "fromCity": "KUL",
  "fromAirport": "",
  "toCity": "BKI",
  "toAirport": "",
  "fromDate": "20260222",
  "retDate": "20260222",
  "airlines": [
    "OD"
  ],
  "includeMultipleFareFamily": false,
  "currency": null,
  "requestSource": null
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
|» tripType|body|string| 是 |The trip type(one way or round trip) you want to search.|
|» adultNum|body|integer| 是 |Adult passenger count. Please note that the total number of adults(`adultNum`) and children(`childNum`) cannot exceed 9.|
|» childNum|body|integer| 是 |Child passenger count. Please note that the total number of adults(`adultNum`) and children(`childNum`) cannot exceed 9|
|» infantNum|body|integer| 是 |Infant passenger count, no more than the number of adult|
|» fromCity|body|string| 是 |IATA code of the departure city or airport (in capital letters).When the airport code you sent is different from the code of the city where the airport is located, we can recognize that it is an airport, otherwise we will treat it as a city code. We will filter flights based on your departure location type.|
|» toCity|body|string| 是 |IATA code of the arrival city or airport (in capital letters).When the airport code you sent is different from the code of the city where the airport is located, we can recognize that it is an airport, otherwise we will treat it as a city code. We will filter flights based on your departure location type.|
|» fromDate|body|string(date)| 是 |Departure date, the format is `YYYYMMDD`|
|» retDate|body|string(date)¦null| 否 |Return date, the format is `YYYYMMDD`. If you are searching for round-trip, the return date is mandatory.|
|» airlines|body|[string]¦null| 否 |An array of IATA Codes(in capital letters) of airlines. The result will only contain the airlines specified in the search request.|
|» fromFlightNumbers|body|[string]¦null| 否 |Search for specified departure flights. Each element represents one flight. Connecting flight numbers are separated by "`,`" (comma). |
|» retFlightNumbers|body|[string]¦null| 否 |Search for specified return flights. Each element represents one flight. Connecting flight numbers are separated by "`,`" (comma).|
|» includeMultipleFareFamily|body|boolean¦null| 否 |Search only for the lowest fare or for the Fare Families. By default, each flight only returns the lowest fare, and each array element in the response represents: flight - lowest fare. If this parameter is turned on, each element of the search results will be a combination of flight and one of the fares, that is, different elements will have the same flight but different ticket fare.|
|» currency|body|string¦null| 否 |This is the settlement currency. The 3-letter currency code should be entered. This field is optional, and when you want to settle with Atlas in different currencies (especially when you have opened multiple deposit accounts in different currencies in Atlas), you need to use this parameter.|
|» requestSource|body|string¦null| 否 |Identify the source of the search traffic, E.g. Google Flights, Oganic Search, SkyScanner.|
|» residentCode|body|string¦null| 否 |Resident discount code|

#### 详细说明

**» tripType**: The trip type(one way or round trip) you want to search.
- 1: Oneway
- 2: Return Trip

**» fromFlightNumbers**: Search for specified departure flights. Each element represents one flight. Connecting flight numbers are separated by "`,`" (comma). 
**Example**:
- ["FR123"]: A direct flight
- ["FR456,FR789"]: A connecting flight
- ["FR123", "FR456,FR789"]: 2 flights, a direct flight and a connecting flight

#### 枚举值

|属性|值|
|---|---|
|» tripType|1|
|» tripType|2|

> 返回示例

> 200 Response

```json
{
  "status": 0,
  "msg": null,
  "routings": [
    {
      "routingIdentifier": "TE9OX1BBUl8yXzIwMjUwODE4XzIwMjUwODIwXzFfMF8wfHR2aWluNjU0Mjh8MnwyMzIuMzhfMjMyLjM4XzYwLjE5XzQuMDBfNTI4Ljk1X1VTRHxMT05fUEFSXzFfMjAyNTA4MThfXzFfMF8wXkxHVy1VMjg0MDUtLUNERy0yMDI1MDgxODE2NDAtMjAyNTA4MTgxODU1LVN0YW5kYXJkLTEtXjE3MC4xNV8xNzAuMTVfMzUuMTZfMi4wMF8zNzcuNDZeQUVDQUVVUl9BRUNeXkFFQzFMT05QQVIyMDAyMDI1MDgxOF5HQlBeMTI1LjMwXjEyNS4zMF4yNS44OV4xJFBBUl9MT05fMl8yMDI1MDgyMF9fMV8wXzBeQ0RHLVUyODQxMC0tTEdXLTIwMjUwODIwMTkxMC0yMDI1MDgyMDE5MjAtU3RhbmRhcmQtMS1eNjIuMjNfNjIuMjNfMjUuMDNfMi4wMF8xNTEuNDleQUVDQUVVUl9BRUNeXkFFQzFQQVJMT04yMDAyMDI1MDgyMF5FVVJeNTMuMTJeNTMuMTJeMjEuMzZeMXwwfDIwMjUwODE2MTUyNzU2fDB8MTc1NTMyOTI3MTAyNFJ2VzdJfHx8fDF8Mi4wMHwzfDB8fG5vcm1hbHxmYWxzZQ==.zkLMRkU3ohHS9/5p28KK1Jw4PTWTsICx24yIQoygMMw=",
      "supportCreditTransPayment": "0",
      "supportPaymentMethods": [
        1,
        5
      ],
      "currency": "USD",
      "adultPrice": 232.38,
      "adultTax": 0,
      "adultDetails": [
        {
          "code": "tax",
          "type": "tax",
          "amount": 0,
          "description": ""
        },
        {
          "code": "farePrice",
          "type": "base",
          "amount": 232.38,
          "description": ""
        }
      ],
      "childPrice": 232.38,
      "childTax": 0,
      "childDetails": [
        {
          "code": "tax",
          "type": "tax",
          "amount": 0,
          "description": ""
        },
        {
          "code": "farePrice",
          "type": "base",
          "amount": 232.38,
          "description": ""
        }
      ],
      "infantPrice": 60.19,
      "infantTax": 0,
      "infantDetails": [
        {
          "code": "tax",
          "type": "tax",
          "amount": 0,
          "description": ""
        },
        {
          "code": "farePrice",
          "type": "base",
          "amount": 60.19,
          "description": ""
        }
      ],
      "infantAllowed": true,
      "childMandatorySeatingFee": null,
      "transactionFeePerPax": 2,
      "transactionFee": 2,
      "transactionFeeMode": "PER_PAX",
      "fromSegments": [
        {
          "aircraftCode": "",
          "arrAirport": "CDG",
          "arrTerminal": "",
          "arrTime": "202508181855",
          "cabin": "",
          "cabinClass": 1,
          "carrier": "U2",
          "codeShare": false,
          "depAirport": "LGW",
          "depTerminal": "",
          "depTime": "202508181640",
          "duration": 75,
          "fareFamily": "Standard",
          "flightNumber": "U28405",
          "operatingCarrier": "",
          "operatingFlightnumber": "",
          "seatCount": 3,
          "segmentIndex": 1,
          "stopCities": ""
        }
      ],
      "retSegments": [
        {
          "aircraftCode": "",
          "arrAirport": "LGW",
          "arrTerminal": "",
          "arrTime": "202508201920",
          "cabin": "",
          "cabinClass": 1,
          "carrier": "U2",
          "codeShare": false,
          "depAirport": "CDG",
          "depTerminal": "",
          "depTime": "202508201910",
          "duration": 70,
          "fareFamily": "Standard",
          "flightNumber": "U28410",
          "operatingCarrier": "",
          "operatingFlightnumber": "",
          "seatCount": 6,
          "segmentIndex": 2,
          "stopCities": ""
        }
      ],
      "rule": {
        "hasBaggage": 1,
        "baggageElements": [
          {
            "segmentNo": 1,
            "baggageType": "CabinBaggageUnderSeat",
            "passengerType": 0,
            "baggagePiece": 1,
            "baggageWeight": 15,
            "baggageSize": "45*36*20cm"
          },
          {
            "segmentNo": 1,
            "baggageType": "StandardCheckInBaggage",
            "passengerType": 0,
            "baggagePiece": 0,
            "baggageWeight": 0,
            "baggageSize": ""
          },
          {
            "segmentNo": 2,
            "baggageType": "CabinBaggageUnderSeat",
            "passengerType": 0,
            "baggagePiece": 1,
            "baggageWeight": 15,
            "baggageSize": "45*36*20cm"
          },
          {
            "segmentNo": 2,
            "baggageType": "StandardCheckInBaggage",
            "passengerType": 0,
            "baggagePiece": 0,
            "baggageWeight": 0,
            "baggageSize": ""
          }
        ],
        "refundRules": [
          {
            "refundType": 0,
            "refundStatus": "T",
            "refundMethod": "CashBackToOriginalPayment",
            "refundFee": 0,
            "currency": "GBP",
            "refNoshow": "T",
            "refNoShowCondition": 0,
            "refNoshowFee": 0,
            "ruleDetailList": [
              {
                "status": "T",
                "refundMethod": "CashBackToOriginalPayment",
                "startMinute": 525600,
                "endMinute": 0,
                "amount": 0,
                "currency": "GBP"
              },
              {
                "status": "T",
                "refundMethod": "CashBackToOriginalPayment",
                "startMinute": 0,
                "endMinute": -525600,
                "amount": 0,
                "currency": "GBP"
              }
            ]
          },
          {
            "refundType": 0,
            "refundStatus": "T",
            "refundMethod": "CashBackToOriginalPayment",
            "refundFee": 0,
            "currency": "GBP",
            "refNoshow": "T",
            "refNoShowCondition": 0,
            "refNoshowFee": 0,
            "ruleDetailList": [
              {
                "ruleId": 47379,
                "status": "T",
                "refundMethod": "CashBackToOriginalPayment",
                "startMinute": 525600,
                "endMinute": 0,
                "amount": 0,
                "currency": "GBP"
              },
              {
                "ruleId": 47381,
                "status": "T",
                "refundMethod": "CashBackToOriginalPayment",
                "startMinute": 0,
                "endMinute": -525600,
                "amount": 0,
                "currency": "GBP"
              }
            ]
          }
        ],
        "changesRules": [
          {
            "changesType": 0,
            "changesStatus": "T",
            "changesFee": 0,
            "currency": "GBP",
            "revNoshow": "T",
            "revNoShowCondition": 0,
            "revNoshowFee": 0,
            "ruleDetailList": [
              {
                "status": "H",
                "refundMethod": null,
                "startMinute": 525600,
                "endMinute": 86400,
                "amount": 30,
                "currency": "GBP"
              },
              {
                "ruleId": 47387,
                "status": "H",
                "refundMethod": null,
                "startMinute": 86400,
                "endMinute": 120,
                "amount": 49,
                "currency": "GBP"
              },
              {
                "ruleId": 47389,
                "status": "T",
                "refundMethod": null,
                "startMinute": 120,
                "endMinute": 0,
                "amount": 0,
                "currency": "GBP"
              },
              {
                "ruleId": 47391,
                "status": "T",
                "refundMethod": null,
                "startMinute": 0,
                "endMinute": -525600,
                "amount": 0,
                "currency": "GBP"
              }
            ]
          },
          {
            "changesType": 0,
            "changesStatus": "T",
            "changesFee": 0,
            "currency": "GBP",
            "revNoshow": "T",
            "revNoShowCondition": 0,
            "revNoshowFee": 0,
            "ruleDetailList": [
              {
                "ruleId": 47385,
                "status": "H",
                "refundMethod": null,
                "startMinute": 525600,
                "endMinute": 86400,
                "amount": 30,
                "currency": "GBP"
              },
              {
                "ruleId": 47387,
                "status": "H",
                "refundMethod": null,
                "startMinute": 86400,
                "endMinute": 120,
                "amount": 45.91,
                "currency": "GBP"
              },
              {
                "ruleId": 47389,
                "status": "T",
                "refundMethod": null,
                "startMinute": 120,
                "endMinute": 0,
                "amount": 0,
                "currency": "GBP"
              },
              {
                "ruleId": 47391,
                "status": "T",
                "refundMethod": null,
                "startMinute": 0,
                "endMinute": -525600,
                "amount": 0,
                "currency": "GBP"
              }
            ]
          }
        ],
        "serviceElements": [
          {
            "hasFreeSeat": 0,
            "hasFreeMeal": 0
          },
          {
            "hasFreeSeat": 0,
            "hasFreeMeal": 0
          }
        ]
      },
      "ancillaryProductElements": [
        {
          "ancillaryCode": "CBOL_1PC_15KG_MAXIMUM SIZE 56 X 45 X 25 CM",
          "auxBaggageElement": {
            "piece": 1,
            "weight": 15,
            "isAllWeight": true,
            "size": "Maximum Size 56 x 45 x 25 cm"
          },
          "canPurchaseWithTicket": 1,
          "canPurchasePostTicket": 0,
          "categoryCode": "CabinBaggageOverheadLocker",
          "clientTechnicalServiceFee": 0,
          "currency": "USD",
          "maxQty": 1,
          "minQty": 1,
          "price": 26.57,
          "productCode": "CBOL_1PC_15KG_MAXIMUM SIZE 56 X 45 X 25 CM",
          "segmentIndex": 1,
          "vendorPrice": 19.56,
          "vendorCurrency": "GBP"
        },
        {
          "segmentIndex": 1,
          "productCode": "SCI_BAG_1PC_15KG",
          "canPurchaseWithTicket": 1,
          "canPurchasePostTicket": 0,
          "price": 27.12,
          "currency": "USD",
          "vendorPrice": 19.97,
          "vendorCurrency": "GBP",
          "clientTechnicalServiceFee": 0,
          "clientTechnicalServiceFeeMode": null,
          "auxBaggageElement": {
            "piece": 1,
            "weight": 15,
            "isAllWeight": true,
            "size": ""
          },
          "maxQty": 1,
          "minQty": 1,
          "categoryCode": "StandardCheckInBaggage",
          "ancillaryCode": "SCI_BAG_1PC_15KG"
        },
        {
          "segmentIndex": 1,
          "productCode": "SCI_BAG_2PC_30KG",
          "canPurchaseWithTicket": 1,
          "canPurchasePostTicket": 0,
          "price": 39.95,
          "currency": "USD",
          "vendorPrice": 29.42,
          "vendorCurrency": "GBP",
          "clientTechnicalServiceFee": 0,
          "clientTechnicalServiceFeeMode": null,
          "auxBaggageElement": {
            "piece": 2,
            "weight": 30,
            "isAllWeight": true,
            "size": ""
          },
          "maxQty": 1,
          "minQty": 1,
          "categoryCode": "StandardCheckInBaggage",
          "ancillaryCode": "SCI_BAG_2PC_30KG"
        },
        {
          "segmentIndex": 2,
          "productCode": "CBOL_1PC_15KG_MAXIMUM SIZE 56 X 45 X 25 CM",
          "canPurchaseWithTicket": 1,
          "canPurchasePostTicket": 0,
          "price": 41.67,
          "currency": "USD",
          "vendorPrice": 35.56,
          "vendorCurrency": "EUR",
          "clientTechnicalServiceFee": 0,
          "clientTechnicalServiceFeeMode": null,
          "auxBaggageElement": {
            "piece": 1,
            "weight": 15,
            "isAllWeight": true,
            "size": "Maximum Size 56 x 45 x 25 cm"
          },
          "maxQty": 1,
          "minQty": 1,
          "categoryCode": "CabinBaggageOverheadLocker",
          "ancillaryCode": "CBOL_1PC_15KG_MAXIMUM SIZE 56 X 45 X 25 CM"
        },
        {
          "segmentIndex": 2,
          "productCode": "SCI_BAG_1PC_15KG",
          "canPurchaseWithTicket": 1,
          "canPurchasePostTicket": 0,
          "price": 31.09,
          "currency": "USD",
          "vendorPrice": 26.53,
          "vendorCurrency": "EUR",
          "clientTechnicalServiceFee": 0,
          "clientTechnicalServiceFeeMode": null,
          "auxBaggageElement": {
            "piece": 1,
            "weight": 15,
            "isAllWeight": true,
            "size": ""
          },
          "maxQty": 1,
          "minQty": 1,
          "categoryCode": "StandardCheckInBaggage",
          "ancillaryCode": "SCI_BAG_1PC_15KG"
        },
        {
          "segmentIndex": 2,
          "productCode": "SCI_BAG_2PC_30KG",
          "canPurchaseWithTicket": 1,
          "canPurchasePostTicket": 0,
          "price": 74.57,
          "currency": "USD",
          "vendorPrice": 63.64,
          "vendorCurrency": "EUR",
          "clientTechnicalServiceFee": 0,
          "clientTechnicalServiceFeeMode": null,
          "auxBaggageElement": {
            "piece": 2,
            "weight": 30,
            "isAllWeight": true,
            "size": ""
          },
          "maxQty": 1,
          "minQty": 1,
          "categoryCode": "StandardCheckInBaggage",
          "ancillaryCode": "SCI_BAG_2PC_30KG"
        }
      ],
      "links": [
        {
          "carrier": "U2",
          "kind": "terms",
          "link": "https://www.easyjet.com",
          "description": null
        }
      ],
      "separateBookings": true,
      "refreshTime": "2025-08-15T22:48:58Z",
      "expireTime": "2025-08-16T07:27:56Z",
      "ancillarySupported": null,
      "cardChargeList": [
        {
          "cardType": "Visa",
          "percentage": 0.03,
          "charge": null,
          "currency": ""
        },
        {
          "cardType": "MasterCard",
          "percentage": 0.03,
          "charge": null,
          "currency": ""
        }
      ],
      "vendorFare": {
        "vendorAdultPrice": 232.38,
        "vendorAdultTax": 0,
        "vendorChildPrice": 232.38,
        "vendorChildTax": 0,
        "vendorInfantPrice": 60.19,
        "vendorInfantTax": 0,
        "vendorCurrency": "USD"
      }
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
|» status|[SearchResponseStatus](#schemasearchresponsestatus)|true|none||- 100: Missing required request data. Description: You should pass the necessary parameters in the HTTP request body.<br />- 101: Illegal request data. Description: Check the format of request<br />- 102: Illegal request param. Description: Some parameters do not meet the requirements. Please adjust them according to the error message.<br />- 105: OD is not in client's round-trip white list. Description: This city pair has not been whitelisted. Check with your account manager if there is a restriction to your account.<br />- 106: You are not allowed to search. Description: Check with your account manager if there is a restriction to your account.<br />- 107: Insufficient balance. Description: The account balance is below the agreed threshold. Top-up your account on a priority.<br />- 108: Route is restricted / System limitations. Description: The airline has flights and quotations, but Atlas has closed sales for some reasons. The reasons can be 1) The sales were manually closed 2) The system has detected a risk of sold out 3) Prohibitions on nearby flights.<br />- 109: The number of searches exceeded the limit. Description: The searches per day have exceeded the allowed limit. Check with your account manager if there is a restriction to your account.<br />- 110: Too many concurrent requests.. Description: The QPS (Queries Per Second) is higher than the allowed limit. If your business requires more resources, please contact your account manager.<br />- 111: Real time search is not allowed. Description: This feature is not activated for your account. Connect with your account manager if you require this service.<br />- 112: Timed out. Description: The search request has timed-out. For further details please refer to FAQs --> Atlas API General Information.<br />- 113: Airline is under maintenance. Description: Airline is in "Inactive" or "Maintenance" status with Atlas. This does not necessarily mean that there is an issue with the Airline website itself. Wait for the status to change to “active”.<br />- 114: No flights present. Description: This may happen when: - The airline does not fly on that date for the searched city pair. Check the airline website to see if the flight is operational for that date.<br />- 116: Search data not captured. Description: An error was reported during the search data stoprage at Atlas' end. If this error is not constantly reported, you can try trying again. If the error persists, then it is necessary to contact the account manager.<br />- 123: Too many requests but too few paid orders. Description: The service has been blocked as the search requests are too many and the paid orders are very less.<br />- 124: Unsupported settlement currency. Description: The settlement currency is different than what is accepted by Atlas. Change the currency to the currency accepted by Atlas for settlement.<br />- 126: `requestId` does not exist or request is already ended. Description: <br />- 900: Unauthorized access. Description: Incorrect credentials Or the account status is incorrect Or try to access other customer's data. Check credentials. If the error still persists, contact your account manager.<br />- 9999: Inner error. Description: There is a problem or a bug in the system. Contact your account manager.|
|» msg|[ResponseMessage](#schemaresponsemessage)|false|none||It serves as an additional description of the response result. Especially when the interface reports an error (`status` !=`0`), it is usually a human-readable error message. Note: Do not use this field in any programming scenarios. For example, do not judge whether the interface responds successfully based on this field. Instead, you should only determine it by checking whether the status is equal to`0`at any time.|
|» routings|[[Routing](#schemarouting)]¦null|false|none||none|
|»» routingIdentifier|string|true|none||This unique string identifier is used to verify requests for a particular route.<br />**Note:**<br />Has a certain validity period (generally not exceeding 6 hours).|
|»» supportCreditTransPayment|string|true|none||This tag is used to identify if the fare is support to be paid using the client's credit card(known as vcc passthrough). This field has been deprecated, please use `supportPaymentMethods` instead.|
|»» supportPaymentMethods|[[PaymentMethod](#schemapaymentmethod)]|true|none||Support payment methods for this fare. If payment is not supported in any way, this will be `null`or`[]`. Each item in this array is one of the following:<br />- 1: deposit<br />- 3: vcc passthrough<br />- 4: BYOA(Bring Your Own Account)<br />- 5: MoR|
|»» currency|string|true|none||The currency in which Atlas settles transactions with you.|
|»» adultPrice|number|true|none||Adult fare per passenger.|
|»» adultTax|number|true|none||Adult tax per passenger.|
|»» adultDetails|[[PriceItem](#schemapriceitem)]¦null|false|none||Details of the adult price composition.|
|»»» code|string|true|none||Machine readable code used to identify this price item.|
|»»» type|string|true|none||Type of this price item.|
|»»» amount|number|true|none||none|
|»»» description|string¦null|false|none||Human-readable description for this price item.|
|»» childPrice|number|true|none||Child fare per passenger.|
|»» childTax|number|true|none||Child tax per passenger.|
|»» childDetails|[[PriceItem](#schemapriceitem)]¦null|false|none||Details of the child price composition.|
|»»» code|string|true|none||Machine readable code used to identify this price item.|
|»»» type|string|true|none||Type of this price item.|
|»»» amount|number|true|none||none|
|»»» description|string¦null|false|none||Human-readable description for this price item.|
|»» infantPrice|number|true|none||Infant fare per passenger.|
|»» infantTax|integer|true|none||Infant tax per passenger.|
|»» infantDetails|[[PriceItem](#schemapriceitem)]¦null|false|none||Details of the child infant composition.|
|»»» code|string|true|none||Machine readable code used to identify this price item.|
|»»» type|string|true|none||Type of this price item.|
|»»» amount|number|true|none||none|
|»»» description|string¦null|false|none||Human-readable description for this price item.|
|»» infantAllowed|boolean¦null|false|none||Since `infantPrice` and `infantTax` will never be `null`, when the fare does not support infants or is free for infants, both `infantPrice` and `infantTax` display `0`. In this case, you need this field to distinguish which situation it is.<br />**Scenario description:**<br />- `true`: infants is supported by this fare, `infantPrice` and `infantTax` will >= `0`<br />- `false`: infants is not supported by this fare, `infantPrice` and `infantTax`will be displayed as `0`|
|»» childMandatorySeatingFee|number¦null|false|none||Only valid for FR integration.<br /><br />**FR Seat Selection Rules:**<br />- Children under 12 years old are provided with free seats.<br />- Children must be seated in the same row as an adult.<br />- Each adult may accompany up to 4 children.<br /><br />For fare families that do not include seat selection fees (e.g., Basic or Family Plus), FR offers discounted seat selection fees for adults traveling with children. The`childMandatorySeatingFee`field displays this discounted fee.<br />For fare families that already include seat selection fees, this field will be `null`.<br /><br />**Handling by Atlas for Fare Families Without Seat Selection Fees:**<br />- The number of children cannot exceed 4.<br />- Customers cannot select seats manually.<br />- Atlas will automatically assign seats randomly to one adult and all children according to FR's rules. The adult will be charged the `childMandatorySeatingFee` for their seat.<br /><br />**For Fare Families That Include Seat Selection Fees:**<br />- Seat selection is free.<br />- Users may call the seat map API to select seats; otherwise, Atlas will automatically assign seats.|
|»» transactionFeePerPax|number|true|none||Technical service fee per passenger. This field has been deprecated and final total transaction fee will calculated based on `transactionFee` and `transactionFeeMode`.|
|»» transactionFee|number|true|none||Technical service fee as per `transactionFeeMode`. The following lists the calculation methods for the final technical service fee in various situations.<br />- `transactionFeeMode`=`PER_SEGMENT`:`transactionFee` * number of passengers * number of segments.<br />- `transactionFeeMode`=`PER_TICKET`:`transactionFee` * number of passengers * number of orders on airline side.<br />- `transactionFeeMode`=`PER_PAX`:`transactionFee` * number of passengers.<br />- `transactionFeeMode`=`PER_BOOKING`:`transactionFee`.|
|»» transactionFeeMode|[TransactionFeeMode](#schematransactionfeemode)|true|none||Calculation method for technical service fee.<br />- PER_SEGMENT: Calculate based on the number of segments in the order (number of travel segments * number of passengers)<br />- PER_TICKET: Calculate based on the number of orders on the airline's side<br />- PER_PAX: Calculate based on the number of passengers<br />- PER_BOOKING: Calculate based on each order|
|»» fromSegments|[[RoutingSegment](#schemaroutingsegment)]|true|none||For outbound segments.|
|»»» aircraftCode|string¦null|false|none||IATA Code of aircraft type|
|»»» arrAirport|string|true|none||3-letter iata code for the arrival airport at which the segment is scheduled to arrive.|
|»»» arrTerminal|string¦null|false|none||The terminal at the destination airport where the segment is scheduled to arrive.|
|»»» arrTime|string|true|none||The datetime at which the segment is scheduled to arrive, in the arrival airport timezone. The format is `YYYYMMDD`.|
|»»» cabin|string¦null|false|none||RBD(known as Reservation Booking Designator) displayed by the airline.|
|»»» cabinClass|[CabinClass](#schemacabinclass)|true|none||Cabin class of the segment.<br />- 1: economy<br />- 2: business<br />- 3: first<br />- 4: premium economy|
|»»» carrier|string|true|none||IATA code of marketing carrier.|
|»»» codeShare|boolean|true|none||A flag used to identify whether it is a code share flight.|
|»»» depAirport|string|true|none||3-letter iata code for the airport at which the segment is scheduled to depart.|
|»»» depTerminal|string¦null|false|none||The terminal at the departure airport from which the segment is scheduled to depart.|
|»»» depTime|string|true|none||The datetime at which the segment is scheduled to depart, in the departure airport timezone. The format is`YYYYMMSS`.|
|»»» duration|integer|true|none||The duration of the segment in munites.|
|»»» fareFamily|string|true|none||Fare Family as per the information received from the airline|
|»»» flightNumber|string|true|none||Marketing flight number. The format is: CA123 or TR021 or FR1290, with the first two letters representing the carrier and the following number representing the flight number.|
|»»» operatingCarrier|string¦null|false|none||2-letter iata code for the operating carrier. The airline actually operating this segment. This may differ from the marketing carrier in the case of a "codeshare", where one airline sells flights operated by another airline.|
|»»» operatingFlightnumber|string¦null|false|none||Operating flight number.|
|»»» seatCount|integer|true|none||Max booking seats for the fare.|
|»»» segmentIndex|integer|true|none||Segment sequence. Starts from 1. If it is return trip, sequence for outbound trip and inbound trip would be together. The segment index also represents the flight sequence of the segment.|
|»»» stopCities|string¦null|false|none||IATA code/Name of cities from where the passengers will take stopover flights. Include IATA code of cities and use a comma in case of multiple cities to separate transfer airports count is higher than 1. For example: `CGK, SUB`. <br />`null` or blank means non-stop flight.|
|»» retSegments|[[RoutingSegment](#schemaroutingsegment)]¦null|false|none||For inbound segments. For one-way, this field will be `null` or `[]`.|
|»»» aircraftCode|string¦null|false|none||IATA Code of aircraft type|
|»»» arrAirport|string|true|none||3-letter iata code for the arrival airport at which the segment is scheduled to arrive.|
|»»» arrTerminal|string¦null|false|none||The terminal at the destination airport where the segment is scheduled to arrive.|
|»»» arrTime|string|true|none||The datetime at which the segment is scheduled to arrive, in the arrival airport timezone. The format is `YYYYMMDD`.|
|»»» cabin|string¦null|false|none||RBD(known as Reservation Booking Designator) displayed by the airline.|
|»»» cabinClass|[CabinClass](#schemacabinclass)|true|none||Cabin class of the segment.<br />- 1: economy<br />- 2: business<br />- 3: first<br />- 4: premium economy|
|»»» carrier|string|true|none||IATA code of marketing carrier.|
|»»» codeShare|boolean|true|none||A flag used to identify whether it is a code share flight.|
|»»» depAirport|string|true|none||3-letter iata code for the airport at which the segment is scheduled to depart.|
|»»» depTerminal|string¦null|false|none||The terminal at the departure airport from which the segment is scheduled to depart.|
|»»» depTime|string|true|none||The datetime at which the segment is scheduled to depart, in the departure airport timezone. The format is`YYYYMMSS`.|
|»»» duration|integer|true|none||The duration of the segment in munites.|
|»»» fareFamily|string|true|none||Fare Family as per the information received from the airline|
|»»» flightNumber|string|true|none||Marketing flight number. The format is: CA123 or TR021 or FR1290, with the first two letters representing the carrier and the following number representing the flight number.|
|»»» operatingCarrier|string¦null|false|none||2-letter iata code for the operating carrier. The airline actually operating this segment. This may differ from the marketing carrier in the case of a "codeshare", where one airline sells flights operated by another airline.|
|»»» operatingFlightnumber|string¦null|false|none||Operating flight number.|
|»»» seatCount|integer|true|none||Max booking seats for the fare.|
|»»» segmentIndex|integer|true|none||Segment sequence. Starts from 1. If it is return trip, sequence for outbound trip and inbound trip would be together. The segment index also represents the flight sequence of the segment.|
|»»» stopCities|string¦null|false|none||IATA code/Name of cities from where the passengers will take stopover flights. Include IATA code of cities and use a comma in case of multiple cities to separate transfer airports count is higher than 1. For example: `CGK, SUB`. <br />`null` or blank means non-stop flight.|
|»» rule|object|true|none||none|
|»»» hasBaggage|integer|true|none||This tag is used to identify if the fare includes free checked-in or cabin baggage.<br />- `0`: Not included<br />- `1`: Included|
|»»» baggageElements|[object]|true|none||The free baggage allowance|
|»»»» segmentNo|integer|true|none||The index of segment the baggage allowance applies to.|
|»»»» baggageType|[AncillaryCategory](#schemaancillarycategory)|true|none||Type of the baggage.|
|»»»» passengerType|[PassengerType](#schemapassengertype)|true|none||The type of passenger the baggage allowance applies to.<br />- 0: Adult<br />- 1: Child<br />- 2: Infant|
|»»»» baggagePiece|integer|true|none||Baggage pieces:<br />- `0`: No limitation<br />- `>0`: Maximum pieces|
|»»»» baggageWeight|integer|true|none||Baggage Weight, with the unit of KG.<br />- `0`: No Free baggage<br />- `-1`: No limitation on weight<br />- `>0`: Maximum weight|
|»»»» baggageSize|string|true|none||Baggage Size:<br />length＊width＊height and units. eg. `56＊36＊23cm`, `18＊14＊8inch`.<br />Or Total dimensions (length + width + height) of each piece. eg. `L+W+H<=158cm`.<br />Empty means no limitation.|
|»»»» isAllWeight|boolean¦null|false|none||Baggage is all weight: true or false|
|»»» refundRules|[object]|true|none||This node is used to fetch the refund rules of the fare. There is only one array element for one way, and two elements for round-trip. The first element is for the outbound, and the second element is for the inbound.|
|»»»» refundType|integer|true|none||Type of refund allowed.<br />- 0: Wholly unused ticket<br />- 1: Partially used ticket (For example, when the passenger has used an outbound flight and wants to refund an inbound flight.)|
|»»»» refundStatus|[RefundStatus](#schemarefundstatus)|false|none||Refund rule types (for the most restrictive condition).<br />- T: Non refundable<br />- H: Refundable with restrictions<br />- F: Full refundable|
|»»»» refundFee|integer¦null|false|none||Refund penalty amount (for the most restrictive condition)|
|»»»» currency|string¦null|false|none||The currency of refund penalty|
|»»»» refNoshow|string|true|none||Indicates if a no-show affects refunds (for the most restrictive condition).<br />- T: Non refundable<br />- H: Refundable with restrictions<br />- F: Free for refund|
|»»»» refNoShowCondition|integer|true|none||Time before scheduled flight departure|
|»»»» refNoshowFee|number|true|none||Total refund fee (for the most restrictive condition): If refNoshow = H, it should not be "null". This value includes the refund fee and no-show penalty|
|»»»» refundMethod|string¦null|false|none||Refund method: CashBackToOriginalPayment or Voucher.<br />- CashBackToOriginalPayment: Refund cash back to the original form of payment.<br />- Voucher: Refund in the form of a voucher.|
|»»»» ruleDetailList|[[AirlineRuleRes](#schemaairlineruleres)]|false|none||none|
|»»»»» status|[RefundStatus](#schemarefundstatus)|true|none||Level of refund/change.<br />- T: Non refundable<br />- H: Refundable with restrictions<br />- F: Full refundable|
|»»»»» startMinute|string|true|none||Starting time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|»»»»» endMinute|string|true|none||Ending time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|»»»»» amount|string¦null|false|none||Penalty amount for refund/change. If the`status`indicates free refund/change, then this field will be either`0`or`null`.|
|»»»»» currency|string¦null|false|none||The currency of penalty|
|»»»»» refundMethod|string¦null|false|none||Refund method: CashBackToOriginalPayment or Voucher.<br />- CashBackToOriginalPayment: Refund cash back to the original form of payment.<br />- Voucher: Refund in the form of a voucher.|
|»»» changesRules|[object]|true|none||This node is used to fetch the change rules of the fare. There is only one array element for one way, and two elements for round-trip. The first element is for the outbound, and the second element is for the inbound.|
|»»»» changesType|integer|true|none||Change flight type.<br />- `0`: Wholly unused ticket<br />- `1`: Partially used ticket (For example. When the passenger has used an outbound flight and wants to change an inbound flight)|
|»»»» changesStatus|[ChangeStatus](#schemachangestatus)|false|none||Change flight rule type (for the most restrictive condition):<br />- T: Non changeable<br />- H: Changeable with restrictions<br />- F: Free rescheduling|
|»»»» changesFee|number¦null|false|none||Change flight fee (for the most restrictive condition):<br />- If`changesStatus`=`H`, it should not be`null`<br />- If`changesStatus`=`T/F`, it can be`null`|
|»»»» currency|string¦null|false|none||The currency of change flight fee|
|»»»» revNoshow|string|true|none||Indicates if a no-show affects changes (for the most restrictive condition).<br />Valid values:<br />- T: Non changeable<br />- H: Changeable with restrictions<br />- F: Free flight change|
|»»»» revNoShowCondition|integer|true|none||Time before scheduled flight departure.|
|»»»» revNoshowFee|number|true|none||The total fee charged to change flight in case of no show. If revNoshow = H, it should not be "null." This value includes the change flight fee and no-show penalty.|
|»»»» ruleDetailList|[object]|false|none||Change conditions|
|»»»»» status|[RefundStatus](#schemarefundstatus)|true|none||Level of refund/change.<br />- T: Non refundable<br />- H: Refundable with restrictions<br />- F: Full refundable|
|»»»»» startMinute|string|true|none||Starting time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|»»»»» endMinute|string|true|none||Ending time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|»»»»» amount|string¦null|false|none||Penalty amount for refund/change. If the`status`indicates free refund/change, then this field will be either`0`or`null`.|
|»»»»» currency|string¦null|false|none||The currency of penalty|
|»»» serviceElements|[object]¦null|false|none||This function is used to fetch the other service rules of the fare. There is only one array for one way, and two arrays for round-trip. The first array is for the outbound, and the second array is for the inbound.|
|»»»» hasFreeSeat|integer|false|none||A marker used to indicate whether free seat selection is included.<br />- `0`: Not included<br />- `1`: Included<br />- `2`: Partially free|
|»»»» hasFreeMeal|integer|false|none||A marker used to indicate whether free meals are included.<br />- `0`: Not included<br />- `1`: Included|
|»» ancillaryProductElements|[[AncillaryProduct](#schemaancillaryproduct)]¦null|false|none||none|
|»»» ancillaryCode|string|true|none||A code that is relatively readable by humans and contains information about auxiliary business specifications (such as weight and quantity limitations of luggage). <br />**Note:** <br />This content is only for display purposes and should not be used for programming purposes. That is to say, do not attempt to parse the information about auxiliary business specifications from this code. If you want to access the auxiliary business specifications, please use structured fields. For example, for luggage, please use`auxBaggageElement`.|
|»»» auxBaggageElement|object¦null|false|none||Baggage specification limitations. This node is valid only when the ancillary type (`categoryCode`) is baggage.|
|»»»» isAllWeight|boolean|true|none||Mark whether the`weight`field restricts the total weight or the weight of a single piece.<br />- `true`: The weight is for all the pieces<br />- `false`: The weight is for each piece|
|»»»» piece|integer|true|none||The maximum number of pieces that can be purchased per person.<br />- `0`: No Limitation about piece<br />- `>0`: Maximum pieces|
|»»»» size|string¦null|false|none||Maximum size for the baggage|
|»»»» weight|integer|true|none||The maximum weight that can be purchased per person.<br />- `0`: No limitation for weight<br />- `>0`: Weight limit (KG)|
|»»» canPurchasePostTicket|integer|true|none||A flag used to mark if this ancillary product can be purchased in the post-ticketing flow.<br />- `0`: No<br />- `1`: Yes|
|»»» canPurchaseWithTicket|integer|true|none||A flag used to mark if this ancillary product can be purchased during the booking flow.<br />- `0`: No<br />- `1`: Yes|
|»»» categoryCode|[AncillaryCategory](#schemaancillarycategory)|true|none||Type of the ancillary.<br /><br />- StandardCheckInBaggage: Standard Check-in Baggage.<br />- CabinBaggage: Usually refers to the Cabin Baggage Overhead Locker. Transition value. It will gradually transition to `CabinBaggageOverheadLocker`.<br />- CabinBaggageOverheadLocker: Cabin Baggage Overhead Locker.<br />- CabinBaggageUnderSeat: Cabin Baggage Under Seat. Usually refers to the personal item.|
|»»» clientTechnicalServiceFee|number¦null|false|none||The service fee charged by Atlas for the purchase of the ancillary.|
|»»» currency|string|true|none||The currency in which Atlas settles transactions with you|
|»»» maxQty|integer|true|none||The maximum number of purchases allowed per person per flight segment|
|»»» minQty|integer|true|none||The minimum quantity allowed to be purchased per person per flight segment.|
|»»» price|number|true|none||Price for this ancillary.|
|»»» productCode|string|true|none||Unique identifier for the ancillary product. It would be used in the order request.|
|»»» segmentIndex|integer|true|none||The index of segment the ancillary applies to.|
|»»» vendorCurrency|string|true|none||The currency in which the vendor charges for the ancillary. If the fare does not allow for the VCC pass-through or BYOA payment, this information will be`null`.|
|»»» vendorPrice|integer|true|none||The price charged by the vendor for the ancillary. If the fare does not allow for the VCC pass-through or BYOA payment, this information will be`null`.|
|»» vendorFare|object|true|none||To identify the vendor’s fare with vendor’s currency. It is only available when`supportPaymentMethods`contains`3`or`4`.|
|»»» vendorAdultPrice|number|true|none||Adult fare per passenger in vendor’s currency|
|»»» vendorAdultTax|number|true|none||Adult tax per passenger in vendor’s currency|
|»»» vendorChildPrice|number|true|none||Child fare per passenger in vendor’s currency|
|»»» vendorChildTax|number|true|none||Child tax per passenger in vendor’s currency|
|»»» vendorInfantPrice|number|true|none||Infant fare per passenger in vendor’s currency|
|»»» vendorInfantTax|integer|true|none||Infant tax per passenger in vendor’s currency|
|»»» vendorCurrency|string|true|none||Vendor’s currency|
|»» links|[TAndCLink](#schematandclink)|true|none||The terms and conditions links of the airlines. Will only return in verify response.|
|»»» carrier|string|true|none||IATA code for the airline|
|»»» kind|string|true|none||always:`terms`|
|»»» link|string|true|none||URL to the carrier's terms and conditions|
|»»» description|string|true|none||Carrier terms and conditions|
|»» separateBookings|boolean|true|none||When the outbound and inbound of round trip need to be booked separately, it will be true.|
|»» refreshTime|string|true|none||If the fare is from the cache of Atlas, this field is used to indicate the refresh time of the cache. The time is a certain moment in the past (UTC), and the format is:`yyyy-MM-dd'T'HH:mm:ss'Z'`.|
|»» expireTime|string|true|none||If the current fare comes from the cache of Atlas, this field is used to indicate the estimated expiration time of the cache. This time is a certain moment in the future (UTC), and the format is:`yyyy-MM-dd'T'HH:mm:ss'Z'`.<br />**Note:** <br />This time is estimated, which means Atlas may refresh the cache before or after that time.|
|»» ancillarySupported|[string]|true|none||A list of ancillary service types that the fare allows for additional purchase. Possible value contains:<br />- `luggage`<br />- `seat`: You can carry out the subsequent seat selection process through our seat map interface.|
|»» cardChargeList|[[CardCharge](#schemacardcharge)]¦null|false|none||Payment handling fee for MoR/VCC|
|»»» cardType|[CardType](#schemacardtype)|true|none||Card types, such as Visa, MasterCard|
|»»» percentage|number¦null|false|none||Percentage of payment handling fee|
|»»» charge|number¦null|false|none||The amount of payment handling fee|
|»»» currency|string¦null|false|none||Currency of `charge`|

#### 枚举值

|属性|值|
|---|---|
|status|100|
|status|101|
|status|102|
|status|105|
|status|106|
|status|107|
|status|108|
|status|109|
|status|110|
|status|111|
|status|112|
|status|113|
|status|114|
|status|116|
|status|123|
|status|124|
|status|126|
|status|900|
|status|9999|
|supportCreditTransPayment|0|
|supportCreditTransPayment|1|
|type|base|
|type|tax|
|type|fee|
|type|base|
|type|tax|
|type|fee|
|type|base|
|type|tax|
|type|fee|
|transactionFeeMode|PER_SEGMENT|
|transactionFeeMode|PER_TICKET|
|transactionFeeMode|PER_PAX|
|transactionFeeMode|PER_BOOKING|
|cabinClass|1|
|cabinClass|2|
|cabinClass|3|
|cabinClass|4|
|cabinClass|1|
|cabinClass|2|
|cabinClass|3|
|cabinClass|4|
|baggageType|StandardCheckInBaggage|
|baggageType|CabinBaggage|
|baggageType|CabinBaggageUnderSeat|
|baggageType|CabinBaggageOverheadLocker|
|passengerType|0|
|passengerType|1|
|passengerType|2|
|refundStatus|T|
|refundStatus|H|
|refundStatus|F|
|refundMethod|CashBackToOriginalPayment|
|refundMethod|Voucher|
|status|T|
|status|H|
|status|F|
|refundMethod|CashBackToOriginalPayment|
|refundMethod|Voucher|
|changesStatus|T|
|changesStatus|H|
|changesStatus|F|
|status|T|
|status|H|
|status|F|
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

## POST Verify

POST /verify.do

**Dependency:**
The `search` function should be called prior to this call.

> - When there is no price change, the "original" and the "new" price and tax will always be the same.
> - When there is price change, there will be some difference between the "original" and the "new" price and tax.
> - If paymentMethod in the request is 5（MoR）the MoR currency will be returned and amount in “VendorFare” and it’s paymentFee in cardChargeList. The paymentFee amount will not be added to the “VendorFare”.
> - If paymentMethod in the request is 3（VCC Passthrough）the VCC Passthrough currency will be returned and amount in “VendorFare” and it’s paymentFee in cardChargeList (if any). The paymentFee amount will be added to the “VendorFare”.

**Endpoint:**
https://sandbox.atriptech.com/verify.do

> Body 请求参数

```json
{
  "routingIdentifier": "TE9OX1BBUl8yXzIwMjUwODE4XzIwMjUwODIwXzFfMF8wfHR2aWluNjU0Mjh8MnwyMzIuMzhfMjMyLjM4XzYwLjE5XzQuMDBfNTI4Ljk1X1VTRHxMT05fUEFSXzFfMjAyNTA4MThfXzFfMF8wXkxHVy1VMjg0MDUtLUNERy0yMDI1MDgxODE2NDAtMjAyNTA4MTgxODU1LVN0YW5kYXJkLTEtXjE3MC4xNV8xNzAuMTVfMzUuMTZfMi4wMF8zNzcuNDZeQUVDQUVVUl9BRUNeXkFFQzFMT05QQVIyMDAyMDI1MDgxOF5HQlBeMTI1LjMwXjEyNS4zMF4yNS44OV4xJFBBUl9MT05fMl8yMDI1MDgyMF9fMV8wXzBeQ0RHLVUyODQxMC0tTEdXLTIwMjUwODIwMTkxMC0yMDI1MDgyMDE5MjAtU3RhbmRhcmQtMS1eNjIuMjNfNjIuMjNfMjUuMDNfMi4wMF8xNTEuNDleQUVDQUVVUl9BRUNeXkFFQzFQQVJMT04yMDAyMDI1MDgyMF5FVVJeNTMuMTJeNTMuMTJeMjEuMzZeMXwwfDIwMjUwODE2MTUyNzU2fDB8MTc1NTMyOTI3MTAyNFJ2VzdJfHx8fDF8Mi4wMHwzfDB8fG5vcm1hbHxmYWxzZQ==.zkLMRkU3ohHS9/5p28KK1Jw4PTWTsICx24yIQoygMMw=",
  "maxResponseTime": null,
  "requestSource": null
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
|» routingIdentifier|body|string| 是 |The`routingIdentifier`from search response.|
|» maxResponseTime|body|integer¦null| 否 |The interface timeout(in milliseconds), with a default of 5000ms. |
|» requestSource|body|[RequestSource](#schemarequestsource)¦null| 否 |The tag to identify which channel does this traffic come from. For example: SkyScanner,Google,Oganic search,etc…|
|» outboundSegments|body|[object]¦null| 否 |Return flight segments are arranged in the order of flight.|
|»» departureAirport|body|string| 是 |IATA code of the departure airport.|
|»» arrivalAirport|body|string| 是 |IATA code of the arrival airport|
|»» flightNumber|body|string| 是 |Marketing flight number without airline code prefix.|
|»» departureDate|body|string| 是 |Departure date of the flight. We do not require users to specify departure times. We do not support return segments based on specific departure time as well. Considering that the externally transmitted time may not match the actual flight segment time on the supplier's (airline's) side, this can lead to search results being lost. Therefore, we will return flights with the specified flight number departing on the specified date.|
|»» carrier|body|string| 是 |IATA two letter code of marketing carrier.|
|» inboundSegments|body|[object]¦null| 否 |Arrange the outbound flight segments in the order of flight. Optional, null or [] indicates one-way.|
|»» departureAirport|body|string| 是 |IATA code of the departure airport.|
|»» arrivalAirport|body|string| 是 |IATA code of the arrival airport|
|»» flightNumber|body|string| 是 |Marketing flight number without airline code prefix.|
|»» departureDate|body|string| 是 |Departure date of the flight. We do not require users to specify departure times. We do not support return segments based on specific departure time as well. Considering that the externally transmitted time may not match the actual flight segment time on the supplier's (airline's) side, this can lead to search results being lost. Therefore, we will return flights with the specified flight number departing on the specified date.|
|»» carrier|body|string| 是 |IATA two letter code of marketing carrier.|

#### 详细说明

**» maxResponseTime**: The interface timeout(in milliseconds), with a default of 5000ms. 
**Note:** 
Due to the influence of network transmission and computational performance, the client may still receive a normal result (instead of a timeout) when the response duration exceeds. This time is used to control the overall response duration of the interface within a certain range, and the error generally will not exceed several hundred milliseconds. If you have strict requirements for the timeout time, it is recommended that you set the timeout time of your HTTP tool library. If the HTTP tool library you use does not support this capability, you may need to use other tools to achieve it, and most programming languages provide relevant capabilities.

> 返回示例

> 200 Response

```json
{
  "status": 0,
  "msg": "success",
  "sessionId": "a39fc063-3192-4058-b179-998ebfb2fed8",
  "maxSeats": 9,
  "routing": {
    "routingIdentifier": "TE9OX1BBUl8yXzIwMjUwODE4XzIwMjUwODIwXzFfMF8wfHR2aWluNjU0Mjh8MXwyNDIuMTRfMjQyLjE0XzY0LjE3XzIuMDBfNTUwLjQ1X1VTRHxMT05fUEFSXzFfMjAyNTA4MThfMjAyNTA4MjBfMV8wXzBeTEdXLVUyODQwNS0tQ0RHLTIwMjUwODE4MTY0MC0yMDI1MDgxODE4NTUtU3RhbmRhcmQtMS0jQ0RHLVUyODQxMC0tTEdXLTIwMjUwODIwMTkxMC0yMDI1MDgyMDE5MjAtU3RhbmRhcmQtMi1eMjQyLjE0XzI0Mi4xNF82NC4xN18yLjAwXzU1MC40NV5BRUNBRVVSX0FFQ15eQUVDMkxPTlBBUjIwMDIwMjUwODE4MjAyNTA4MjBeR0JQXjE3OC4zMl4xNzguMzJeNDcuMjVeMHwwfDIwMjUwODE2MTU1NzQ1fDB8MTc1NTMzMTA2NTU0MkJOYm1HfHx8fHwyLjAwfDN8MHx8bm9ybWFsfGZhbHNl.5FDcOQsu5zTUOBN/jPsM23gT5WuaPAs7g8AmH8q/m0U=",
    "supportCreditTransPayment": "0",
    "supportPaymentMethods": [
      1,
      5
    ],
    "currency": "USD",
    "adultPrice": 242.14,
    "adultTax": 0,
    "adultDetails": [
      {
        "code": "farePrice",
        "type": "base",
        "amount": 242.14,
        "description": ""
      },
      {
        "code": "tax",
        "type": "tax",
        "amount": 0,
        "description": ""
      }
    ],
    "childPrice": 242.14,
    "childTax": 0,
    "childDetails": [
      {
        "code": "farePrice",
        "type": "base",
        "amount": 242.14,
        "description": ""
      },
      {
        "code": "tax",
        "type": "tax",
        "amount": 0,
        "description": ""
      }
    ],
    "infantPrice": 64.17,
    "infantTax": 0,
    "infantDetails": [
      {
        "code": "farePrice",
        "type": "base",
        "amount": 64.17,
        "description": ""
      },
      {
        "code": "tax",
        "type": "tax",
        "amount": 0,
        "description": ""
      }
    ],
    "infantAllowed": true,
    "childMandatorySeatingFee": null,
    "transactionFeePerPax": 2,
    "transactionFee": 2,
    "transactionFeeMode": "PER_PAX",
    "fromSegments": [
      {
        "segmentIndex": 1,
        "carrier": "U2",
        "flightNumber": "U28405",
        "depAirport": "LGW",
        "depTime": "202508181640",
        "arrAirport": "CDG",
        "arrTime": "202508181855",
        "stopCities": null,
        "duration": 75,
        "codeShare": false,
        "cabin": "",
        "cabinClass": 1,
        "seatCount": 9,
        "aircraftCode": "",
        "depTerminal": "",
        "arrTerminal": "",
        "operatingCarrier": "",
        "operatingFlightnumber": "",
        "fareFamily": "Standard"
      }
    ],
    "retSegments": [
      {
        "segmentIndex": 2,
        "carrier": "U2",
        "flightNumber": "U28410",
        "depAirport": "CDG",
        "depTime": "202508201910",
        "arrAirport": "LGW",
        "arrTime": "202508201920",
        "stopCities": null,
        "duration": 70,
        "codeShare": false,
        "cabin": "",
        "cabinClass": 1,
        "seatCount": 9,
        "aircraftCode": "",
        "depTerminal": "",
        "arrTerminal": "",
        "operatingCarrier": "",
        "operatingFlightnumber": "",
        "fareFamily": "Standard"
      }
    ],
    "rule": {
      "hasBaggage": 1,
      "baggageElements": [
        {
          "segmentNo": 1,
          "baggageType": "CabinBaggageUnderSeat",
          "passengerType": 0,
          "baggagePiece": 1,
          "baggageWeight": 15,
          "baggageSize": "45*36*20cm"
        },
        {
          "segmentNo": 1,
          "baggageType": "StandardCheckInBaggage",
          "passengerType": 0,
          "baggagePiece": 0,
          "baggageWeight": 0,
          "baggageSize": ""
        },
        {
          "segmentNo": 2,
          "baggageType": "CabinBaggageUnderSeat",
          "passengerType": 0,
          "baggagePiece": 1,
          "baggageWeight": 15,
          "baggageSize": "45*36*20cm"
        },
        {
          "segmentNo": 2,
          "baggageType": "StandardCheckInBaggage",
          "passengerType": 0,
          "baggagePiece": 0,
          "baggageWeight": 0,
          "baggageSize": ""
        }
      ],
      "refundRules": [
        {
          "refundType": 0,
          "refundStatus": "T",
          "refundMethod": "CASH_BACK_TO_ORIGINAL_PAYMENT",
          "refundFee": 0,
          "currency": "GBP",
          "refNoshow": "T",
          "refNoShowCondition": 0,
          "refNoshowFee": 0,
          "ruleDetailList": [
            {
              "status": "T",
              "refundMethod": "CashBackToOriginalPayment",
              "startMinute": 525600,
              "endMinute": 0,
              "amount": 0,
              "currency": "GBP"
            },
            {
              "status": "T",
              "refundMethod": "CashBackToOriginalPayment",
              "startMinute": 0,
              "endMinute": -525600,
              "amount": 0,
              "currency": "GBP"
            }
          ]
        },
        {
          "refundType": 0,
          "refundStatus": "T",
          "refundMethod": "CASH_BACK_TO_ORIGINAL_PAYMENT",
          "refundFee": 0,
          "currency": "GBP",
          "refNoshow": "T",
          "refNoShowCondition": 0,
          "refNoshowFee": 0,
          "ruleDetailList": [
            {
              "status": "T",
              "refundMethod": "CashBackToOriginalPayment",
              "startMinute": 525600,
              "endMinute": 0,
              "amount": 0,
              "currency": "GBP"
            },
            {
              "status": "T",
              "refundMethod": "CashBackToOriginalPayment",
              "startMinute": 0,
              "endMinute": -525600,
              "amount": 0,
              "currency": "GBP"
            }
          ]
        }
      ],
      "changesRules": [
        {
          "changesType": 0,
          "changesStatus": "T",
          "changesFee": 0,
          "currency": "GBP",
          "revNoshow": "T",
          "revNoShowCondition": 0,
          "revNoshowFee": 0,
          "ruleDetailList": [
            {
              "status": "H",
              "startMinute": 525600,
              "endMinute": 86400,
              "amount": 30,
              "currency": "GBP"
            },
            {
              "status": "H",
              "startMinute": 86400,
              "endMinute": 120,
              "amount": 49,
              "currency": "GBP"
            },
            {
              "status": "T",
              "startMinute": 120,
              "endMinute": 0,
              "amount": 0,
              "currency": "GBP"
            },
            {
              "status": "T",
              "startMinute": 0,
              "endMinute": -525600,
              "amount": 0,
              "currency": "GBP"
            }
          ]
        },
        {
          "changesType": 0,
          "changesStatus": "T",
          "changesFee": 0,
          "currency": "GBP",
          "revNoshow": "T",
          "revNoShowCondition": 0,
          "revNoshowFee": 0,
          "ruleDetailList": [
            {
              "status": "H",
              "startMinute": 525600,
              "endMinute": 86400,
              "amount": 30,
              "currency": "GBP"
            },
            {
              "status": "H",
              "startMinute": 86400,
              "endMinute": 120,
              "amount": 49,
              "currency": "GBP"
            },
            {
              "status": "T",
              "startMinute": 120,
              "endMinute": 0,
              "amount": 0,
              "currency": "GBP"
            },
            {
              "status": "T",
              "startMinute": 0,
              "endMinute": -525600,
              "amount": 0,
              "currency": "GBP"
            }
          ]
        }
      ],
      "serviceElements": [
        {
          "hasFreeSeat": 0,
          "hasFreeMeal": 0
        },
        {
          "hasFreeSeat": 0,
          "hasFreeMeal": 0
        }
      ]
    },
    "ancillaryProductElements": [
      {
        "ancillaryCode": "CBOL_1PC_15KG_MAXIMUM SIZE 56 X 45 X 25 CM",
        "auxBaggageElement": {
          "piece": 1,
          "weight": 15,
          "isAllWeight": true,
          "size": "Maximum Size 56 x 45 x 25 cm"
        },
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 0,
        "categoryCode": "CabinBaggageOverheadLocker",
        "clientTechnicalServiceFee": 0,
        "currency": "USD",
        "maxQty": 1,
        "minQty": 1,
        "price": 26.57,
        "productCode": "CBOL_1PC_15KG_MAXIMUM SIZE 56 X 45 X 25 CM",
        "segmentIndex": 1,
        "vendorPrice": 19.56,
        "vendorCurrency": "GBP"
      },
      {
        "segmentIndex": 1,
        "productCode": "SCI_BAG_1PC_15KG",
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 0,
        "price": 27.12,
        "currency": "USD",
        "vendorPrice": 19.97,
        "vendorCurrency": "GBP",
        "clientTechnicalServiceFee": 0,
        "auxBaggageElement": {
          "piece": 1,
          "weight": 15,
          "isAllWeight": true,
          "size": ""
        },
        "maxQty": 1,
        "minQty": 1,
        "categoryCode": "StandardCheckInBaggage",
        "ancillaryCode": "SCI_BAG_1PC_15KG"
      },
      {
        "segmentIndex": 1,
        "productCode": "SCI_BAG_2PC_30KG",
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 0,
        "price": 39.95,
        "currency": "USD",
        "vendorPrice": 29.42,
        "vendorCurrency": "GBP",
        "clientTechnicalServiceFee": 0,
        "auxBaggageElement": {
          "piece": 2,
          "weight": 30,
          "isAllWeight": true,
          "size": ""
        },
        "maxQty": 1,
        "minQty": 1,
        "categoryCode": "StandardCheckInBaggage",
        "ancillaryCode": "SCI_BAG_2PC_30KG"
      },
      {
        "segmentIndex": 2,
        "productCode": "CBOL_1PC_15KG_MAXIMUM SIZE 56 X 45 X 25 CM",
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 0,
        "price": 41.67,
        "currency": "USD",
        "vendorPrice": 30.69,
        "vendorCurrency": "GBP",
        "clientTechnicalServiceFee": 0,
        "auxBaggageElement": {
          "piece": 1,
          "weight": 15,
          "isAllWeight": true,
          "size": "Maximum Size 56 x 45 x 25 cm"
        },
        "maxQty": 1,
        "minQty": 1,
        "categoryCode": "CabinBaggageOverheadLocker",
        "ancillaryCode": "CBOL_1PC_15KG_MAXIMUM SIZE 56 X 45 X 25 CM"
      },
      {
        "segmentIndex": 2,
        "productCode": "SCI_BAG_1PC_15KG",
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 0,
        "price": 31.09,
        "currency": "USD",
        "vendorPrice": 22.9,
        "vendorCurrency": "GBP",
        "clientTechnicalServiceFee": 0,
        "auxBaggageElement": {
          "piece": 1,
          "weight": 15,
          "isAllWeight": true,
          "size": ""
        },
        "maxQty": 1,
        "minQty": 1,
        "categoryCode": "StandardCheckInBaggage",
        "ancillaryCode": "SCI_BAG_1PC_15KG"
      },
      {
        "segmentIndex": 2,
        "productCode": "SCI_BAG_2PC_30KG",
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 0,
        "price": 74.57,
        "currency": "USD",
        "vendorPrice": 54.91,
        "vendorCurrency": "GBP",
        "clientTechnicalServiceFee": 0,
        "auxBaggageElement": {
          "piece": 2,
          "weight": 30,
          "isAllWeight": true,
          "size": ""
        },
        "maxQty": 1,
        "minQty": 1,
        "categoryCode": "StandardCheckInBaggage",
        "ancillaryCode": "SCI_BAG_2PC_30KG"
      }
    ],
    "vendorFare": null,
    "links": [],
    "separateBookings": false,
    "refreshTime": null,
    "expireTime": null,
    "ancillarySupported": [
      "seat",
      "luggage"
    ],
    "cardChargeList": [
      {
        "cardType": "Visa",
        "percentage": 0.03,
        "charge": null,
        "currency": ""
      },
      {
        "cardType": "MasterCard",
        "percentage": 0.03,
        "charge": null,
        "currency": ""
      }
    ]
  },
  "bookingRequirement": {
    "passenger": {
      "cardIssuePlace": {
        "required": false
      },
      "birthday": {
        "required": true
      },
      "cardNum": {
        "required": false
      },
      "passengerType": {
        "required": true
      },
      "nationality": {
        "required": false
      },
      "gender": {
        "required": true
      },
      "cardExpired": {
        "required": false
      },
      "cardType": {
        "required": false
      },
      "name": {
        "required": true
      }
    }
  },
  "priceChange": {
    "isPriceChange": true,
    "originalAdultPrice": 232.38,
    "originalAdultTax": 0,
    "originalChildPrice": 232.38,
    "originalChildTax": 0,
    "originalInfantPrice": 60.19,
    "originalInfantTax": 0,
    "newAdultPrice": 242.14,
    "newAdultTax": 0,
    "newChildPrice": 242.14,
    "newChildTax": 0,
    "newInfantPrice": 64.17,
    "newInfantTax": 0
  }
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
|» status|[VerifyResponseStatus](#schemaverifyresponsestatus)|true|none||- 200: Illegal routing identifier. Description: The "routingIdentifier" in request contains invalid content. Please check the content of this field to ensure that the content returned by the search is passed back exactly as it is.<br />- 201: Invalid routing. Description: The airline has flights and quotations, but Atlas has closed sales for some reasons. The reasons can be 1) The sales were manually closed 2) The system has detected a risk of sold out 3) Prohibitions on nearby flights. Try booking after some time.<br />- 202: Routing identifier expired. Description: The routingIdentifier has a certain validity period. If the “routingIdentifier” is used after this time period, then this error is displayed. Conduct “Search” again and use the new “routingIdentifier”.<br />- 203: Airline closed. Description: The airline is no longer in business.<br />- 205: Timed out. Description: <br />- 207: Flight not available. Description: The required flight is no longer available at the airline's side, possibly due to the flight being sold out.<br />- 210: Fare family sold out. Description: The flight or the fare family is no longer available with the airline. Conduct the search again and rebook.<br />- 212: Illegal Request Parameter. Description: Some parameters do not meet the requirements. Please adjust them according to the error message.<br />- 213: Flight information changed. Description: Conduct the search again and rebook.<br />- 222: Fail to obtain baggage from airline. Description: Fail to obtain baggage from airline, pls retry the request.<br />- 299: Verify failed. Description: This is an error for which Atlas needs to take action. In some uncontrollable situations, such as network issues, upgrades, and restarts, 299 errors may occur. It is possible that the airline is not available or there are challenges at Atlas' end. Atlas needs to handle these errors internally.|
|» msg|[ResponseMessage](#schemaresponsemessage)¦null|false|none||It serves as an additional description of the response result. Especially when the interface reports an error (`status` !=`0`), it is usually a human-readable error message. Note: Do not use this field in any programming scenarios. For example, do not judge whether the interface responds successfully based on this field. Instead, you should only determine it by checking whether the status is equal to`0`at any time.|
|» sessionId|string|true|none||The unique identifier for this verification. It is required when you call order function to make a reservation to identify which flight and fare the client is choosing.|
|» maxSeats|integer|true|none||Max seats allowed when booking. Please refer this element and prevent the end-users to choose more passengers than seat count.|
|» routing|[Routing](#schemarouting)|true|none||none|
|»» routingIdentifier|string|true|none||This unique string identifier is used to verify requests for a particular route.<br />**Note:**<br />Has a certain validity period (generally not exceeding 6 hours).|
|»» supportCreditTransPayment|string|true|none||This tag is used to identify if the fare is support to be paid using the client's credit card(known as vcc passthrough). This field has been deprecated, please use `supportPaymentMethods` instead.|
|»» supportPaymentMethods|[[PaymentMethod](#schemapaymentmethod)]|true|none||Support payment methods for this fare. If payment is not supported in any way, this will be `null`or`[]`. Each item in this array is one of the following:<br />- 1: deposit<br />- 3: vcc passthrough<br />- 4: BYOA(Bring Your Own Account)<br />- 5: MoR|
|»» currency|string|true|none||The currency in which Atlas settles transactions with you.|
|»» adultPrice|number|true|none||Adult fare per passenger.|
|»» adultTax|number|true|none||Adult tax per passenger.|
|»» adultDetails|[[PriceItem](#schemapriceitem)]¦null|false|none||Details of the adult price composition.|
|»»» code|string|true|none||Machine readable code used to identify this price item.|
|»»» type|string|true|none||Type of this price item.|
|»»» amount|number|true|none||none|
|»»» description|string¦null|false|none||Human-readable description for this price item.|
|»» childPrice|number|true|none||Child fare per passenger.|
|»» childTax|number|true|none||Child tax per passenger.|
|»» childDetails|[[PriceItem](#schemapriceitem)]¦null|false|none||Details of the child price composition.|
|»»» code|string|true|none||Machine readable code used to identify this price item.|
|»»» type|string|true|none||Type of this price item.|
|»»» amount|number|true|none||none|
|»»» description|string¦null|false|none||Human-readable description for this price item.|
|»» infantPrice|number|true|none||Infant fare per passenger.|
|»» infantTax|integer|true|none||Infant tax per passenger.|
|»» infantDetails|[[PriceItem](#schemapriceitem)]¦null|false|none||Details of the child infant composition.|
|»»» code|string|true|none||Machine readable code used to identify this price item.|
|»»» type|string|true|none||Type of this price item.|
|»»» amount|number|true|none||none|
|»»» description|string¦null|false|none||Human-readable description for this price item.|
|»» infantAllowed|boolean¦null|false|none||Since `infantPrice` and `infantTax` will never be `null`, when the fare does not support infants or is free for infants, both `infantPrice` and `infantTax` display `0`. In this case, you need this field to distinguish which situation it is.<br />**Scenario description:**<br />- `true`: infants is supported by this fare, `infantPrice` and `infantTax` will >= `0`<br />- `false`: infants is not supported by this fare, `infantPrice` and `infantTax`will be displayed as `0`|
|»» childMandatorySeatingFee|number¦null|false|none||Only valid for FR integration.<br /><br />**FR Seat Selection Rules:**<br />- Children under 12 years old are provided with free seats.<br />- Children must be seated in the same row as an adult.<br />- Each adult may accompany up to 4 children.<br /><br />For fare families that do not include seat selection fees (e.g., Basic or Family Plus), FR offers discounted seat selection fees for adults traveling with children. The`childMandatorySeatingFee`field displays this discounted fee.<br />For fare families that already include seat selection fees, this field will be `null`.<br /><br />**Handling by Atlas for Fare Families Without Seat Selection Fees:**<br />- The number of children cannot exceed 4.<br />- Customers cannot select seats manually.<br />- Atlas will automatically assign seats randomly to one adult and all children according to FR's rules. The adult will be charged the `childMandatorySeatingFee` for their seat.<br /><br />**For Fare Families That Include Seat Selection Fees:**<br />- Seat selection is free.<br />- Users may call the seat map API to select seats; otherwise, Atlas will automatically assign seats.|
|»» transactionFeePerPax|number|true|none||Technical service fee per passenger. This field has been deprecated and final total transaction fee will calculated based on `transactionFee` and `transactionFeeMode`.|
|»» transactionFee|number|true|none||Technical service fee as per `transactionFeeMode`. The following lists the calculation methods for the final technical service fee in various situations.<br />- `transactionFeeMode`=`PER_SEGMENT`:`transactionFee` * number of passengers * number of segments.<br />- `transactionFeeMode`=`PER_TICKET`:`transactionFee` * number of passengers * number of orders on airline side.<br />- `transactionFeeMode`=`PER_PAX`:`transactionFee` * number of passengers.<br />- `transactionFeeMode`=`PER_BOOKING`:`transactionFee`.|
|»» transactionFeeMode|[TransactionFeeMode](#schematransactionfeemode)|true|none||Calculation method for technical service fee.<br />- PER_SEGMENT: Calculate based on the number of segments in the order (number of travel segments * number of passengers)<br />- PER_TICKET: Calculate based on the number of orders on the airline's side<br />- PER_PAX: Calculate based on the number of passengers<br />- PER_BOOKING: Calculate based on each order|
|»» fromSegments|[[RoutingSegment](#schemaroutingsegment)]|true|none||For outbound segments.|
|»»» aircraftCode|string¦null|false|none||IATA Code of aircraft type|
|»»» arrAirport|string|true|none||3-letter iata code for the arrival airport at which the segment is scheduled to arrive.|
|»»» arrTerminal|string¦null|false|none||The terminal at the destination airport where the segment is scheduled to arrive.|
|»»» arrTime|string|true|none||The datetime at which the segment is scheduled to arrive, in the arrival airport timezone. The format is `YYYYMMDD`.|
|»»» cabin|string¦null|false|none||RBD(known as Reservation Booking Designator) displayed by the airline.|
|»»» cabinClass|[CabinClass](#schemacabinclass)|true|none||Cabin class of the segment.<br />- 1: economy<br />- 2: business<br />- 3: first<br />- 4: premium economy|
|»»» carrier|string|true|none||IATA code of marketing carrier.|
|»»» codeShare|boolean|true|none||A flag used to identify whether it is a code share flight.|
|»»» depAirport|string|true|none||3-letter iata code for the airport at which the segment is scheduled to depart.|
|»»» depTerminal|string¦null|false|none||The terminal at the departure airport from which the segment is scheduled to depart.|
|»»» depTime|string|true|none||The datetime at which the segment is scheduled to depart, in the departure airport timezone. The format is`YYYYMMSS`.|
|»»» duration|integer|true|none||The duration of the segment in munites.|
|»»» fareFamily|string|true|none||Fare Family as per the information received from the airline|
|»»» flightNumber|string|true|none||Marketing flight number. The format is: CA123 or TR021 or FR1290, with the first two letters representing the carrier and the following number representing the flight number.|
|»»» operatingCarrier|string¦null|false|none||2-letter iata code for the operating carrier. The airline actually operating this segment. This may differ from the marketing carrier in the case of a "codeshare", where one airline sells flights operated by another airline.|
|»»» operatingFlightnumber|string¦null|false|none||Operating flight number.|
|»»» seatCount|integer|true|none||Max booking seats for the fare.|
|»»» segmentIndex|integer|true|none||Segment sequence. Starts from 1. If it is return trip, sequence for outbound trip and inbound trip would be together. The segment index also represents the flight sequence of the segment.|
|»»» stopCities|string¦null|false|none||IATA code/Name of cities from where the passengers will take stopover flights. Include IATA code of cities and use a comma in case of multiple cities to separate transfer airports count is higher than 1. For example: `CGK, SUB`. <br />`null` or blank means non-stop flight.|
|»» retSegments|[[RoutingSegment](#schemaroutingsegment)]¦null|false|none||For inbound segments. For one-way, this field will be `null` or `[]`.|
|»»» aircraftCode|string¦null|false|none||IATA Code of aircraft type|
|»»» arrAirport|string|true|none||3-letter iata code for the arrival airport at which the segment is scheduled to arrive.|
|»»» arrTerminal|string¦null|false|none||The terminal at the destination airport where the segment is scheduled to arrive.|
|»»» arrTime|string|true|none||The datetime at which the segment is scheduled to arrive, in the arrival airport timezone. The format is `YYYYMMDD`.|
|»»» cabin|string¦null|false|none||RBD(known as Reservation Booking Designator) displayed by the airline.|
|»»» cabinClass|[CabinClass](#schemacabinclass)|true|none||Cabin class of the segment.<br />- 1: economy<br />- 2: business<br />- 3: first<br />- 4: premium economy|
|»»» carrier|string|true|none||IATA code of marketing carrier.|
|»»» codeShare|boolean|true|none||A flag used to identify whether it is a code share flight.|
|»»» depAirport|string|true|none||3-letter iata code for the airport at which the segment is scheduled to depart.|
|»»» depTerminal|string¦null|false|none||The terminal at the departure airport from which the segment is scheduled to depart.|
|»»» depTime|string|true|none||The datetime at which the segment is scheduled to depart, in the departure airport timezone. The format is`YYYYMMSS`.|
|»»» duration|integer|true|none||The duration of the segment in munites.|
|»»» fareFamily|string|true|none||Fare Family as per the information received from the airline|
|»»» flightNumber|string|true|none||Marketing flight number. The format is: CA123 or TR021 or FR1290, with the first two letters representing the carrier and the following number representing the flight number.|
|»»» operatingCarrier|string¦null|false|none||2-letter iata code for the operating carrier. The airline actually operating this segment. This may differ from the marketing carrier in the case of a "codeshare", where one airline sells flights operated by another airline.|
|»»» operatingFlightnumber|string¦null|false|none||Operating flight number.|
|»»» seatCount|integer|true|none||Max booking seats for the fare.|
|»»» segmentIndex|integer|true|none||Segment sequence. Starts from 1. If it is return trip, sequence for outbound trip and inbound trip would be together. The segment index also represents the flight sequence of the segment.|
|»»» stopCities|string¦null|false|none||IATA code/Name of cities from where the passengers will take stopover flights. Include IATA code of cities and use a comma in case of multiple cities to separate transfer airports count is higher than 1. For example: `CGK, SUB`. <br />`null` or blank means non-stop flight.|
|»» rule|object|true|none||none|
|»»» hasBaggage|integer|true|none||This tag is used to identify if the fare includes free checked-in or cabin baggage.<br />- `0`: Not included<br />- `1`: Included|
|»»» baggageElements|[object]|true|none||The free baggage allowance|
|»»»» segmentNo|integer|true|none||The index of segment the baggage allowance applies to.|
|»»»» baggageType|[AncillaryCategory](#schemaancillarycategory)|true|none||Type of the baggage.|
|»»»» passengerType|[PassengerType](#schemapassengertype)|true|none||The type of passenger the baggage allowance applies to.<br />- 0: Adult<br />- 1: Child<br />- 2: Infant|
|»»»» baggagePiece|integer|true|none||Baggage pieces:<br />- `0`: No limitation<br />- `>0`: Maximum pieces|
|»»»» baggageWeight|integer|true|none||Baggage Weight, with the unit of KG.<br />- `0`: No Free baggage<br />- `-1`: No limitation on weight<br />- `>0`: Maximum weight|
|»»»» baggageSize|string|true|none||Baggage Size:<br />length＊width＊height and units. eg. `56＊36＊23cm`, `18＊14＊8inch`.<br />Or Total dimensions (length + width + height) of each piece. eg. `L+W+H<=158cm`.<br />Empty means no limitation.|
|»»»» isAllWeight|boolean¦null|false|none||Baggage is all weight: true or false|
|»»» refundRules|[object]|true|none||This node is used to fetch the refund rules of the fare. There is only one array element for one way, and two elements for round-trip. The first element is for the outbound, and the second element is for the inbound.|
|»»»» refundType|integer|true|none||Type of refund allowed.<br />- 0: Wholly unused ticket<br />- 1: Partially used ticket (For example, when the passenger has used an outbound flight and wants to refund an inbound flight.)|
|»»»» refundStatus|[RefundStatus](#schemarefundstatus)|false|none||Refund rule types (for the most restrictive condition).<br />- T: Non refundable<br />- H: Refundable with restrictions<br />- F: Full refundable|
|»»»» refundFee|integer¦null|false|none||Refund penalty amount (for the most restrictive condition)|
|»»»» currency|string¦null|false|none||The currency of refund penalty|
|»»»» refNoshow|string|true|none||Indicates if a no-show affects refunds (for the most restrictive condition).<br />- T: Non refundable<br />- H: Refundable with restrictions<br />- F: Free for refund|
|»»»» refNoShowCondition|integer|true|none||Time before scheduled flight departure|
|»»»» refNoshowFee|number|true|none||Total refund fee (for the most restrictive condition): If refNoshow = H, it should not be "null". This value includes the refund fee and no-show penalty|
|»»»» refundMethod|string¦null|false|none||Refund method: CashBackToOriginalPayment or Voucher.<br />- CashBackToOriginalPayment: Refund cash back to the original form of payment.<br />- Voucher: Refund in the form of a voucher.|
|»»»» ruleDetailList|[[AirlineRuleRes](#schemaairlineruleres)]|false|none||none|
|»»»»» status|[RefundStatus](#schemarefundstatus)|true|none||Level of refund/change.<br />- T: Non refundable<br />- H: Refundable with restrictions<br />- F: Full refundable|
|»»»»» startMinute|string|true|none||Starting time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|»»»»» endMinute|string|true|none||Ending time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|»»»»» amount|string¦null|false|none||Penalty amount for refund/change. If the`status`indicates free refund/change, then this field will be either`0`or`null`.|
|»»»»» currency|string¦null|false|none||The currency of penalty|
|»»»»» refundMethod|string¦null|false|none||Refund method: CashBackToOriginalPayment or Voucher.<br />- CashBackToOriginalPayment: Refund cash back to the original form of payment.<br />- Voucher: Refund in the form of a voucher.|
|»»» changesRules|[object]|true|none||This node is used to fetch the change rules of the fare. There is only one array element for one way, and two elements for round-trip. The first element is for the outbound, and the second element is for the inbound.|
|»»»» changesType|integer|true|none||Change flight type.<br />- `0`: Wholly unused ticket<br />- `1`: Partially used ticket (For example. When the passenger has used an outbound flight and wants to change an inbound flight)|
|»»»» changesStatus|[ChangeStatus](#schemachangestatus)|false|none||Change flight rule type (for the most restrictive condition):<br />- T: Non changeable<br />- H: Changeable with restrictions<br />- F: Free rescheduling|
|»»»» changesFee|number¦null|false|none||Change flight fee (for the most restrictive condition):<br />- If`changesStatus`=`H`, it should not be`null`<br />- If`changesStatus`=`T/F`, it can be`null`|
|»»»» currency|string¦null|false|none||The currency of change flight fee|
|»»»» revNoshow|string|true|none||Indicates if a no-show affects changes (for the most restrictive condition).<br />Valid values:<br />- T: Non changeable<br />- H: Changeable with restrictions<br />- F: Free flight change|
|»»»» revNoShowCondition|integer|true|none||Time before scheduled flight departure.|
|»»»» revNoshowFee|number|true|none||The total fee charged to change flight in case of no show. If revNoshow = H, it should not be "null." This value includes the change flight fee and no-show penalty.|
|»»»» ruleDetailList|[object]|false|none||Change conditions|
|»»»»» status|[RefundStatus](#schemarefundstatus)|true|none||Level of refund/change.<br />- T: Non refundable<br />- H: Refundable with restrictions<br />- F: Full refundable|
|»»»»» startMinute|string|true|none||Starting time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|»»»»» endMinute|string|true|none||Ending time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|»»»»» amount|string¦null|false|none||Penalty amount for refund/change. If the`status`indicates free refund/change, then this field will be either`0`or`null`.|
|»»»»» currency|string¦null|false|none||The currency of penalty|
|»»» serviceElements|[object]¦null|false|none||This function is used to fetch the other service rules of the fare. There is only one array for one way, and two arrays for round-trip. The first array is for the outbound, and the second array is for the inbound.|
|»»»» hasFreeSeat|integer|false|none||A marker used to indicate whether free seat selection is included.<br />- `0`: Not included<br />- `1`: Included<br />- `2`: Partially free|
|»»»» hasFreeMeal|integer|false|none||A marker used to indicate whether free meals are included.<br />- `0`: Not included<br />- `1`: Included|
|»» ancillaryProductElements|[[AncillaryProduct](#schemaancillaryproduct)]¦null|false|none||none|
|»»» ancillaryCode|string|true|none||A code that is relatively readable by humans and contains information about auxiliary business specifications (such as weight and quantity limitations of luggage). <br />**Note:** <br />This content is only for display purposes and should not be used for programming purposes. That is to say, do not attempt to parse the information about auxiliary business specifications from this code. If you want to access the auxiliary business specifications, please use structured fields. For example, for luggage, please use`auxBaggageElement`.|
|»»» auxBaggageElement|object¦null|false|none||Baggage specification limitations. This node is valid only when the ancillary type (`categoryCode`) is baggage.|
|»»»» isAllWeight|boolean|true|none||Mark whether the`weight`field restricts the total weight or the weight of a single piece.<br />- `true`: The weight is for all the pieces<br />- `false`: The weight is for each piece|
|»»»» piece|integer|true|none||The maximum number of pieces that can be purchased per person.<br />- `0`: No Limitation about piece<br />- `>0`: Maximum pieces|
|»»»» size|string¦null|false|none||Maximum size for the baggage|
|»»»» weight|integer|true|none||The maximum weight that can be purchased per person.<br />- `0`: No limitation for weight<br />- `>0`: Weight limit (KG)|
|»»» canPurchasePostTicket|integer|true|none||A flag used to mark if this ancillary product can be purchased in the post-ticketing flow.<br />- `0`: No<br />- `1`: Yes|
|»»» canPurchaseWithTicket|integer|true|none||A flag used to mark if this ancillary product can be purchased during the booking flow.<br />- `0`: No<br />- `1`: Yes|
|»»» categoryCode|[AncillaryCategory](#schemaancillarycategory)|true|none||Type of the ancillary.<br /><br />- StandardCheckInBaggage: Standard Check-in Baggage.<br />- CabinBaggage: Usually refers to the Cabin Baggage Overhead Locker. Transition value. It will gradually transition to `CabinBaggageOverheadLocker`.<br />- CabinBaggageOverheadLocker: Cabin Baggage Overhead Locker.<br />- CabinBaggageUnderSeat: Cabin Baggage Under Seat. Usually refers to the personal item.|
|»»» clientTechnicalServiceFee|number¦null|false|none||The service fee charged by Atlas for the purchase of the ancillary.|
|»»» currency|string|true|none||The currency in which Atlas settles transactions with you|
|»»» maxQty|integer|true|none||The maximum number of purchases allowed per person per flight segment|
|»»» minQty|integer|true|none||The minimum quantity allowed to be purchased per person per flight segment.|
|»»» price|number|true|none||Price for this ancillary.|
|»»» productCode|string|true|none||Unique identifier for the ancillary product. It would be used in the order request.|
|»»» segmentIndex|integer|true|none||The index of segment the ancillary applies to.|
|»»» vendorCurrency|string|true|none||The currency in which the vendor charges for the ancillary. If the fare does not allow for the VCC pass-through or BYOA payment, this information will be`null`.|
|»»» vendorPrice|integer|true|none||The price charged by the vendor for the ancillary. If the fare does not allow for the VCC pass-through or BYOA payment, this information will be`null`.|
|»» vendorFare|object|true|none||To identify the vendor’s fare with vendor’s currency. It is only available when`supportPaymentMethods`contains`3`or`4`.|
|»»» vendorAdultPrice|number|true|none||Adult fare per passenger in vendor’s currency|
|»»» vendorAdultTax|number|true|none||Adult tax per passenger in vendor’s currency|
|»»» vendorChildPrice|number|true|none||Child fare per passenger in vendor’s currency|
|»»» vendorChildTax|number|true|none||Child tax per passenger in vendor’s currency|
|»»» vendorInfantPrice|number|true|none||Infant fare per passenger in vendor’s currency|
|»»» vendorInfantTax|integer|true|none||Infant tax per passenger in vendor’s currency|
|»»» vendorCurrency|string|true|none||Vendor’s currency|
|»» links|[TAndCLink](#schematandclink)|true|none||The terms and conditions links of the airlines. Will only return in verify response.|
|»»» carrier|string|true|none||IATA code for the airline|
|»»» kind|string|true|none||always:`terms`|
|»»» link|string|true|none||URL to the carrier's terms and conditions|
|»»» description|string|true|none||Carrier terms and conditions|
|»» separateBookings|boolean|true|none||When the outbound and inbound of round trip need to be booked separately, it will be true.|
|»» refreshTime|string|true|none||If the fare is from the cache of Atlas, this field is used to indicate the refresh time of the cache. The time is a certain moment in the past (UTC), and the format is:`yyyy-MM-dd'T'HH:mm:ss'Z'`.|
|»» expireTime|string|true|none||If the current fare comes from the cache of Atlas, this field is used to indicate the estimated expiration time of the cache. This time is a certain moment in the future (UTC), and the format is:`yyyy-MM-dd'T'HH:mm:ss'Z'`.<br />**Note:** <br />This time is estimated, which means Atlas may refresh the cache before or after that time.|
|»» ancillarySupported|[string]|true|none||A list of ancillary service types that the fare allows for additional purchase. Possible value contains:<br />- `luggage`<br />- `seat`: You can carry out the subsequent seat selection process through our seat map interface.|
|»» cardChargeList|[[CardCharge](#schemacardcharge)]¦null|false|none||Payment handling fee for MoR/VCC|
|»»» cardType|[CardType](#schemacardtype)|true|none||Card types, such as Visa, MasterCard|
|»»» percentage|number¦null|false|none||Percentage of payment handling fee|
|»»» charge|number¦null|false|none||The amount of payment handling fee|
|»»» currency|string¦null|false|none||Currency of `charge`|
|» bookingRequirement|[BookingRequirement](#schemabookingrequirement)|true|none||none|
|»» passenger|object|true|none||Passenger information requirements|
|»»» birthday|[BookingRequirementConstraint](#schemabookingrequirementconstraint)|true|none||Requirements for birthday.|
|»»»» required|boolean|true|none||Required or not|
|»»» cardIssuePlace|[BookingRequirementConstraint](#schemabookingrequirementconstraint)|true|none||Requirements for the country where the identity document is issued.|
|»»»» required|boolean|true|none||Required or not|
|»»» cardNum|[BookingRequirementConstraint](#schemabookingrequirementconstraint)|true|none||Requirements for the number of identity document.|
|»»»» required|boolean|true|none||Required or not|
|»»» passengerType|[BookingRequirementConstraint](#schemabookingrequirementconstraint)|true|none||Requirements for the type of passenger(Adult, Child, Infant).|
|»»»» required|boolean|true|none||Required or not|
|»»» gender|[BookingRequirementConstraint](#schemabookingrequirementconstraint)|true|none||Requirements for passenger's gender|
|»»»» required|boolean|true|none||Required or not|
|»»» nationality|[BookingRequirementConstraint](#schemabookingrequirementconstraint)|true|none||Requirements for passenger's nationality|
|»»»» required|boolean|true|none||Required or not|
|»»» cardExpired|[BookingRequirementConstraint](#schemabookingrequirementconstraint)|true|none||Requirements for the expiration date of identity document|
|»»»» required|boolean|true|none||Required or not|
|»»» name|[BookingRequirementConstraint](#schemabookingrequirementconstraint)|true|none||Requirements for passenger's name|
|»»»» required|boolean|true|none||Required or not|
|»»» cardType|[BookingRequirementConstraint](#schemabookingrequirementconstraint)|true|none||Requirements for the type of identity document.|
|»»»» required|boolean|true|none||Required or not|
|» priceChange|object|true|none||none|
|»» isPriceChange|boolean|true|none||Indicate whether the price has changed (compared to the search result)|
|»» originalAdultPrice|number|true|none||Original adult fare price returned in search response|
|»» originalAdultTax|number|true|none||Original adult tax returned in search response|
|»» originalChildPrice|number|true|none||Original child fare price returned in search response|
|»» originalChildTax|number|true|none||Original child tax returned in search response|
|»» originalInfantPrice|number|true|none||Original infant fare price returned in search response|
|»» originalInfantTax|integer|true|none||Original infant tax returned in search response|
|»» newAdultPrice|number|true|none||Current adult fare price returned in search response|
|»» newAdultTax|number|true|none||Current adult tax returned in search response|
|»» newChildPrice|number|true|none||Current child fare price returned in search response|
|»» newChildTax|number|true|none||Current child tax returned in search response|
|»» newInfantPrice|number|true|none||Current infant fare price returned in search response|
|»» newInfantTax|integer|true|none||Current infant tax returned in search response|

#### 枚举值

|属性|值|
|---|---|
|status|200|
|status|201|
|status|202|
|status|203|
|status|205|
|status|207|
|status|210|
|status|212|
|status|213|
|status|222|
|status|299|
|supportCreditTransPayment|0|
|supportCreditTransPayment|1|
|type|base|
|type|tax|
|type|fee|
|type|base|
|type|tax|
|type|fee|
|type|base|
|type|tax|
|type|fee|
|transactionFeeMode|PER_SEGMENT|
|transactionFeeMode|PER_TICKET|
|transactionFeeMode|PER_PAX|
|transactionFeeMode|PER_BOOKING|
|cabinClass|1|
|cabinClass|2|
|cabinClass|3|
|cabinClass|4|
|cabinClass|1|
|cabinClass|2|
|cabinClass|3|
|cabinClass|4|
|baggageType|StandardCheckInBaggage|
|baggageType|CabinBaggage|
|baggageType|CabinBaggageUnderSeat|
|baggageType|CabinBaggageOverheadLocker|
|passengerType|0|
|passengerType|1|
|passengerType|2|
|refundStatus|T|
|refundStatus|H|
|refundStatus|F|
|refundMethod|CashBackToOriginalPayment|
|refundMethod|Voucher|
|status|T|
|status|H|
|status|F|
|refundMethod|CashBackToOriginalPayment|
|refundMethod|Voucher|
|changesStatus|T|
|changesStatus|H|
|changesStatus|F|
|status|T|
|status|H|
|status|F|
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

## POST Order

POST /order.do

**Dependency:**
`Verify` function should be called in prior to this call.

> The booking requirements need to be read from the "bookingRequirement" array in the "verify.do" response. The "Booking Requirements" can be different at the route level. Alternatively, you can add all the details but please note that all the fields should have actual data and not fictitious information. Please follow this approach.

**Endpoint:**
https://sandbox.atriptech.com/order.do

> Body 请求参数

```json
{
  "sessionId": "a39fc063-3192-4058-b179-998ebfb2fed8",
  "offerId": "",
  "passengers": [
    {
      "name": "For/Test",
      "passengerType": 0,
      "gender": "M",
      "birthday": "19900101",
      "cardType": "PP",
      "cardNum": "636940383",
      "cardIssuePlace": "PT",
      "cardExpired": "20250101",
      "nationality": "US",
      "ffpCardNo": null,
      "ffpCarrier": null,
      "ancillaries": [
        {
          "productCode": "SCI_BAG_1PC_15KG",
          "segmentIndex": 1
        },
        {
          "productCode": "SCI_BAG_1PC_15KG",
          "segmentIndex": 2
        }
      ]
    }
  ],
  "contact": {
    "name": "For/Test",
    "address": "For test",
    "postcode": "",
    "email": "for-test@example.com",
    "mobile": "0001-12345678900"
  },
  "useAtlasMailForContact": false,
  "locale": "",
  "requestSource": "",
  "ifSeatOccupied": "",
  "payment": null
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
|» sessionId|body|string¦null| 否 |`sessionId`returned by verify response. If you got offer by verify api, then this parameter is required.|
|» offerId|body|string¦null| 否 |`offerID`returned by get offer response. If you got offer by "get offer" api, then this parameter is required.|
|» passengers|body|[object]| 是 |Passengers' information|
|»» name|body|string| 是 |The passenger's name. Please send it in the following format: Family Name/Given Name|
|»» passengerType|body|[PassengerType](#schemapassengertype)| 是 |Type of passenger.|
|»» gender|body|string| 是 |The passenger's gender.|
|»» birthday|body|string¦null| 否 |The passenger's date of birth. Format:`YYYYMMDD`. Please fill in according to the passenger information requirements(`bookingRequirement`) returned by the Verification / Get Offer API.|
|»» cardType|body|string¦null| 否 |The type of the identity document.|
|»» cardNum|body|string¦null| 否 |The unique identifier of the identity document. e.g. the passport number. Please fill in according to the passenger information requirements(`bookingRequirement`) returned by the Verification / Get Offer API.|
|»» cardIssuePlace|body|string¦null| 否 |The ISO 3166-1 alpha-2 code for the country where the identity document is issued. Please fill in according to the passenger information requirements(`bookingRequirement`) returned by the Verification / Get Offer API.|
|»» cardExpired|body|string¦null| 否 |The date on which the identity document expires. Format:`YYYYMMDD`.Please fill in according to the passenger information requirements(`bookingRequirement`) returned by the Verification / Get Offer API.|
|»» nationality|body|string¦null| 否 |The ISO 3166-1 alpha-2 code for the nationality of passenger. Please fill in according to the passenger information requirements(`bookingRequirement`) returned by the Verification / Get Offer API.|
|»» ffpCardNo|body|string¦null| 否 |The passenger's account number for this frequent flyer account|
|»» ffpCarrier|body|string¦null| 否 |The IATA code for the airline that this frequent flyer account belongs to|
|»» ancillaries|body|[object]¦null| 否 |Ancillaries selection for the specific passenger|
|»»» productCode|body|string| 是 |Ancillary product code(`productCode`). Got from routing element in the search/revalidation response.|
|»»» segmentIndex|body|integer| 是 |Segment sequence|
|»» residentInfo|body|object¦null| 否 |Resident Info|
|»»» docType|body|string| 是 |Certificate types supported by resident' prices|
|»»» docNum|body|string¦null| 否 |ID number, if the ID type is D, E|
|»»» municipality|body|string¦null| 否 |Municipal district code|
|»»» largeFamilyCert|body|string¦null| 否 |Large Family Cert|
|»»» community|body|string¦null| 否 |Community Region Code|
|» contact|body|object| 是 |none|
|»» name|body|string| 是 |Contact name, please follow this format: Family Name/Given Name. The contact name can only accept Latin letters, /, and spaces.|
|»» address|body|string¦null| 否 |Contact address.|
|»» postcode|body|string¦null| 否 |Contact post code.|
|»» email|body|string¦null| 否 |Contact email.|
|»» mobile|body|string¦null| 否 |Contact mobile, please follow this format : XXXX(digital country code)-XXXXXXXX(phone number), here're the examples: 0001-87291810, 0086-13928109091, 0971-19201998|
|» clientContact|body|object¦null| 否 |Customer's contact. Currently only required in FR.|
|»» email|body|string| 是 |Contact email.|
|»» companyName|body|string¦null| 否 |Company name.|
|» useAtlasMailForContact|body|boolean¦null| 否 |The tag denoting whether to use Atlas email id for contact information.|
|» requestSource|body|[RequestSource](#schemarequestsource)¦null| 否 |The tag to identify which channel does this traffic come from. For example: SkyScanner,Google,Oganic search,etc…|
|» ifSeatOccupied|body|[IfSeatOccupied](#schemaifseatoccupied)¦null| 否 |Configuration of ordering when the seat is occupied.|
|» payment|body|[OrderPayment](#schemaorderpayment)¦null| 否 |Payment information|
|»» cardType|body|[CardType](#schemacardtype)| 是 |The card type you wish to use for payment. Send this information when generating an order can be used to calculate the payment handling fee. This parameter is only effective and required in the MoR payment scenario.|
|» locale|body|string¦null| 否 |The country and language environment preferences of the ticket purchaser/contact person. This information may be useful for certain airlines. For example, airlines will use this information to communicate with users in appropriate languages (e.g., via emails). We have prepared the language environments supported by each airline for your reference: [Locale](apifox://link/pages/6811327)|

#### 详细说明

**»» passengerType**: Type of passenger.
- 0: Adult
- 1: Child
- 2: Infant

**»» gender**: The passenger's gender.
- `M`: Male
- `F`: Female

**»» cardType**: The type of the identity document.
- PP: Passport
- GA: Hong Kong Macau Pass for China mainland citizens
- TW: Taiwan Pass for China mainland citizens
- TB: China mainland pass for Taiwanese
- HY: International Seaman's Certificate

**» useAtlasMailForContact**: The tag denoting whether to use Atlas email id for contact information.
- `true`: Use Atlas email as contact email.
- `false`: It is determined according to the strategy agreed upon with the customer or the default strategy of the system.

Please refer to the [terms and conditions](https://resources.atriptech.com/terms-of-service/atlas-email-service) for usage of Atlas email.

**» ifSeatOccupied**: Configuration of ordering when the seat is occupied.
- SIMILAR_SEAT: Select a similar seat automatically
- STOP_SEAT: Stop seat and continue ticketing
- STOP_TICKET: Stop ticketing and cancel the order
The default value is`SIMILAR_SEAT`.

#### 枚举值

|属性|值|
|---|---|
|»» passengerType|0|
|»» passengerType|1|
|»» passengerType|2|
|»» cardType|PP|
|»» cardType|GA|
|»» cardType|TW|
|»» cardType|TB|
|»» cardType|HY|
|» ifSeatOccupied|SIMILAR_SEAT|
|» ifSeatOccupied|STOP_SEAT|
|» ifSeatOccupied|STOP_TICKET|
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
  "sessionId": "a39fc063-3192-4058-b179-998ebfb2fed8",
  "offerId": "",
  "orderNo": "TESTA20250816160804096",
  "pnrCode": "MDQZ7U",
  "totalPrice": 300.35,
  "totalTransactionFee": 2,
  "currency": "USD",
  "vendorTotalPrice": 221.19,
  "vendorCurrency": "GBP",
  "tktLimitTime": "2025-08-16 16:58:04",
  "paxTicketInfos": [
    {
      "name": "For/Test",
      "passengerType": 0,
      "birthday": "19900101",
      "gender": "M",
      "cardNum": "636940383",
      "cardType": "NATIONAL_ID_CARD",
      "cardIssuePlace": "PT",
      "cardExpired": "20250101",
      "nationality": "US",
      "ticketNos": [],
      "airlinePNRs": [],
      "contactEmails": [
        "for-test@example.com"
      ],
      "contactPhones": [
        "0001-12345678900"
      ],
      "ancillaries": [
        {
          "productCode": "SCI_BAG_1PC_15KG",
          "segmentIndex": 1,
          "currency": "USD",
          "ancillaryPrice": 27.12,
          "auxBaggageElement": {
            "piece": 1,
            "weight": 15,
            "isAllWeight": true,
            "size": ""
          },
          "vendorPrice": null,
          "vendorCurrency": null
        },
        {
          "productCode": "SCI_BAG_1PC_15KG",
          "segmentIndex": 2,
          "currency": "USD",
          "ancillaryPrice": 31.09,
          "auxBaggageElement": {
            "piece": 1,
            "weight": 15,
            "isAllWeight": true,
            "size": ""
          },
          "vendorPrice": null,
          "vendorCurrency": null
        }
      ]
    }
  ],
  "routing": {
    "routingIdentifier": "TE9OX1BBUl8yXzIwMjUwODE4XzIwMjUwODIwXzFfMF8wfHR2aWluNjU0Mjh8MXwyNDIuMTRfMjQyLjE0XzY0LjE3XzIuMDBfNTUwLjQ1X1VTRHxMT05fUEFSXzFfMjAyNTA4MThfMjAyNTA4MjBfMV8wXzBeTEdXLVUyODQwNS0tQ0RHLTIwMjUwODE4MTY0MC0yMDI1MDgxODE4NTUtU3RhbmRhcmQtMS0jQ0RHLVUyODQxMC0tTEdXLTIwMjUwODIwMTkxMC0yMDI1MDgyMDE5MjAtU3RhbmRhcmQtMi1eMjQyLjE0XzI0Mi4xNF82NC4xN18yLjAwXzU1MC40NV5BRUNBRVVSX0FFQ15eQUVDMkxPTlBBUjIwMDIwMjUwODE4MjAyNTA4MjBeR0JQXjE3OC4zMl4xNzguMzJeNDcuMjVeMHwwfDIwMjUwODE2MTU1NzQ1fDB8MTc1NTMzMTA2NTU0MkJOYm1HfHx8fHwyLjAwfDN8MHx8bm9ybWFsfGZhbHNl.5FDcOQsu5zTUOBN/jPsM23gT5WuaPAs7g8AmH8q/m0U=",
    "supportCreditTransPayment": "0",
    "supportPaymentMethods": [
      1,
      5
    ],
    "currency": "USD",
    "adultPrice": 242.14,
    "adultTax": 0,
    "adultDetails": [
      {
        "code": "farePrice",
        "type": "base",
        "amount": 242.14,
        "description": ""
      },
      {
        "code": "tax",
        "type": "tax",
        "amount": 0,
        "description": ""
      }
    ],
    "childPrice": 242.14,
    "childTax": 0,
    "childDetails": [
      {
        "code": "farePrice",
        "type": "base",
        "amount": 242.14,
        "description": ""
      },
      {
        "code": "tax",
        "type": "tax",
        "amount": 0,
        "description": ""
      }
    ],
    "infantPrice": 64.17,
    "infantTax": 0,
    "infantDetails": [
      {
        "code": "farePrice",
        "type": "base",
        "amount": 64.17,
        "description": ""
      },
      {
        "code": "tax",
        "type": "tax",
        "amount": 0,
        "description": ""
      }
    ],
    "infantAllowed": true,
    "childMandatorySeatingFee": null,
    "transactionFeePerPax": 2,
    "transactionFee": 2,
    "transactionFeeMode": "PER_PAX",
    "fromSegments": [
      {
        "segmentIndex": 1,
        "carrier": "U2",
        "flightNumber": "U28405",
        "depAirport": "LGW",
        "depTime": "202508181640",
        "arrAirport": "CDG",
        "arrTime": "202508181855",
        "stopCities": null,
        "duration": 75,
        "codeShare": false,
        "cabin": "",
        "cabinClass": 1,
        "seatCount": 9,
        "aircraftCode": "",
        "depTerminal": "",
        "arrTerminal": "",
        "operatingCarrier": "",
        "operatingFlightnumber": "",
        "fareFamily": "Standard"
      }
    ],
    "retSegments": [
      {
        "segmentIndex": 2,
        "carrier": "U2",
        "flightNumber": "U28410",
        "depAirport": "CDG",
        "depTime": "202508201910",
        "arrAirport": "LGW",
        "arrTime": "202508201920",
        "stopCities": null,
        "duration": 70,
        "codeShare": false,
        "cabin": "",
        "cabinClass": 1,
        "seatCount": 9,
        "aircraftCode": "",
        "depTerminal": "",
        "arrTerminal": "",
        "operatingCarrier": "",
        "operatingFlightnumber": "",
        "fareFamily": "Standard"
      }
    ],
    "rule": {
      "hasBaggage": 1,
      "baggageElements": [
        {
          "segmentNo": 1,
          "baggageType": "CabinBaggageUnderSeat",
          "passengerType": 0,
          "baggagePiece": 1,
          "baggageWeight": 15,
          "baggageSize": "45*36*20cm"
        },
        {
          "segmentNo": 1,
          "baggageType": "StandardCheckInBaggage",
          "passengerType": 0,
          "baggagePiece": 0,
          "baggageWeight": 0,
          "baggageSize": ""
        },
        {
          "segmentNo": 2,
          "baggageType": "CabinBaggageUnderSeat",
          "passengerType": 0,
          "baggagePiece": 1,
          "baggageWeight": 15,
          "baggageSize": "45*36*20cm"
        },
        {
          "segmentNo": 2,
          "baggageType": "StandardCheckInBaggage",
          "passengerType": 0,
          "baggagePiece": 0,
          "baggageWeight": 0,
          "baggageSize": ""
        }
      ],
      "refundRules": [
        {
          "refundType": 0,
          "refundStatus": "T",
          "refundMethod": "CASH_BACK_TO_ORIGINAL_PAYMENT",
          "refundFee": 0,
          "currency": "GBP",
          "refNoshow": "T",
          "refNoShowCondition": 0,
          "refNoshowFee": 0,
          "ruleDetailList": [
            {
              "status": "T",
              "refundMethod": "CashBackToOriginalPayment",
              "startMinute": 525600,
              "endMinute": 0,
              "amount": 0,
              "currency": "GBP"
            },
            {
              "status": "T",
              "refundMethod": "CashBackToOriginalPayment",
              "startMinute": 0,
              "endMinute": -525600,
              "amount": 0,
              "currency": "GBP"
            }
          ]
        },
        {
          "refundType": 0,
          "refundStatus": "T",
          "refundMethod": "CASH_BACK_TO_ORIGINAL_PAYMENT",
          "refundFee": 0,
          "currency": "GBP",
          "refNoshow": "T",
          "refNoShowCondition": 0,
          "refNoshowFee": 0,
          "ruleDetailList": [
            {
              "status": "T",
              "refundMethod": "CashBackToOriginalPayment",
              "startMinute": 525600,
              "endMinute": 0,
              "amount": 0,
              "currency": "GBP"
            },
            {
              "status": "T",
              "refundMethod": "CashBackToOriginalPayment",
              "startMinute": 0,
              "endMinute": -525600,
              "amount": 0,
              "currency": "GBP"
            }
          ]
        }
      ],
      "changesRules": [
        {
          "changesType": 0,
          "changesStatus": "T",
          "changesFee": 0,
          "currency": "GBP",
          "revNoshow": "T",
          "revNoShowCondition": 0,
          "revNoshowFee": 0,
          "ruleDetailList": [
            {
              "status": "H",
              "startMinute": 525600,
              "endMinute": 86400,
              "amount": 30,
              "currency": "GBP"
            },
            {
              "status": "H",
              "startMinute": 86400,
              "endMinute": 120,
              "amount": 49,
              "currency": "GBP"
            },
            {
              "status": "T",
              "startMinute": 120,
              "endMinute": 0,
              "amount": 0,
              "currency": "GBP"
            },
            {
              "status": "T",
              "startMinute": 0,
              "endMinute": -525600,
              "amount": 0,
              "currency": "GBP"
            }
          ]
        },
        {
          "changesType": 0,
          "changesStatus": "T",
          "changesFee": 0,
          "currency": "GBP",
          "revNoshow": "T",
          "revNoShowCondition": 0,
          "revNoshowFee": 0,
          "ruleDetailList": [
            {
              "status": "H",
              "startMinute": 525600,
              "endMinute": 86400,
              "amount": 30,
              "currency": "GBP"
            },
            {
              "status": "H",
              "startMinute": 86400,
              "endMinute": 120,
              "amount": 49,
              "currency": "GBP"
            },
            {
              "status": "T",
              "startMinute": 120,
              "endMinute": 0,
              "amount": 0,
              "currency": "GBP"
            },
            {
              "status": "T",
              "startMinute": 0,
              "endMinute": -525600,
              "amount": 0,
              "currency": "GBP"
            }
          ]
        }
      ],
      "serviceElements": [
        {
          "hasFreeSeat": 0,
          "hasFreeMeal": 0
        },
        {
          "hasFreeSeat": 0,
          "hasFreeMeal": 0
        }
      ]
    },
    "ancillaryProductElements": [
      {
        "ancillaryCode": "CBOL_1PC_15KG_MAXIMUM SIZE 56 X 45 X 25 CM",
        "auxBaggageElement": {
          "piece": 1,
          "weight": 15,
          "isAllWeight": true,
          "size": "Maximum Size 56 x 45 x 25 cm"
        },
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 0,
        "categoryCode": "CabinBaggageOverheadLocker",
        "clientTechnicalServiceFee": 0,
        "currency": "USD",
        "maxQty": 1,
        "minQty": 1,
        "price": 26.57,
        "productCode": "CBOL_1PC_15KG_MAXIMUM SIZE 56 X 45 X 25 CM",
        "segmentIndex": 1,
        "vendorPrice": 19.56,
        "vendorCurrency": "GBP"
      },
      {
        "segmentIndex": 1,
        "productCode": "SCI_BAG_1PC_15KG",
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 0,
        "price": 27.12,
        "currency": "USD",
        "vendorPrice": 19.97,
        "vendorCurrency": "GBP",
        "clientTechnicalServiceFee": 0,
        "auxBaggageElement": {
          "piece": 1,
          "weight": 15,
          "isAllWeight": true,
          "size": ""
        },
        "maxQty": 1,
        "minQty": 1,
        "categoryCode": "StandardCheckInBaggage",
        "ancillaryCode": "SCI_BAG_1PC_15KG"
      },
      {
        "segmentIndex": 1,
        "productCode": "SCI_BAG_2PC_30KG",
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 0,
        "price": 39.95,
        "currency": "USD",
        "vendorPrice": 29.42,
        "vendorCurrency": "GBP",
        "clientTechnicalServiceFee": 0,
        "auxBaggageElement": {
          "piece": 2,
          "weight": 30,
          "isAllWeight": true,
          "size": ""
        },
        "maxQty": 1,
        "minQty": 1,
        "categoryCode": "StandardCheckInBaggage",
        "ancillaryCode": "SCI_BAG_2PC_30KG"
      },
      {
        "segmentIndex": 2,
        "productCode": "CBOL_1PC_15KG_MAXIMUM SIZE 56 X 45 X 25 CM",
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 0,
        "price": 41.67,
        "currency": "USD",
        "vendorPrice": 30.69,
        "vendorCurrency": "GBP",
        "clientTechnicalServiceFee": 0,
        "auxBaggageElement": {
          "piece": 1,
          "weight": 15,
          "isAllWeight": true,
          "size": "Maximum Size 56 x 45 x 25 cm"
        },
        "maxQty": 1,
        "minQty": 1,
        "categoryCode": "CabinBaggageOverheadLocker",
        "ancillaryCode": "CBOL_1PC_15KG_MAXIMUM SIZE 56 X 45 X 25 CM"
      },
      {
        "segmentIndex": 2,
        "productCode": "SCI_BAG_1PC_15KG",
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 0,
        "price": 31.09,
        "currency": "USD",
        "vendorPrice": 22.9,
        "vendorCurrency": "GBP",
        "clientTechnicalServiceFee": 0,
        "auxBaggageElement": {
          "piece": 1,
          "weight": 15,
          "isAllWeight": true,
          "size": ""
        },
        "maxQty": 1,
        "minQty": 1,
        "categoryCode": "StandardCheckInBaggage",
        "ancillaryCode": "SCI_BAG_1PC_15KG"
      },
      {
        "segmentIndex": 2,
        "productCode": "SCI_BAG_2PC_30KG",
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 0,
        "price": 74.57,
        "currency": "USD",
        "vendorPrice": 54.91,
        "vendorCurrency": "GBP",
        "clientTechnicalServiceFee": 0,
        "auxBaggageElement": {
          "piece": 2,
          "weight": 30,
          "isAllWeight": true,
          "size": ""
        },
        "maxQty": 1,
        "minQty": 1,
        "categoryCode": "StandardCheckInBaggage",
        "ancillaryCode": "SCI_BAG_2PC_30KG"
      }
    ],
    "vendorFare": null,
    "links": [],
    "separateBookings": false,
    "refreshTime": null,
    "expireTime": null,
    "ancillarySupported": [
      "seat",
      "luggage"
    ],
    "cardChargeList": [
      {
        "cardType": "Visa",
        "percentage": 0.03,
        "charge": null,
        "currency": ""
      },
      {
        "cardType": "MasterCard",
        "percentage": 0.03,
        "charge": null,
        "currency": ""
      }
    ]
  },
  "duplicateOrders": null,
  "paymentOptions": [
    {
      "paymentMethod": 1,
      "serviceFee": {
        "amount": 2,
        "currency": "USD",
        "deductFrom": "DEPOSIT"
      },
      "ticketFare": {
        "amount": 300.35,
        "currency": "USD",
        "deductFrom": "DEPOSIT"
      },
      "paymentFee": {
        "amount": 0,
        "currency": "USD",
        "deductFrom": "CARD"
      },
      "cardType": null
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
|» status|[OrderResponseStatus](#schemaorderresponsestatus)|true|none||- 301: Session does not exist or timed out. Description: The "sessionID" has a validity of 2 hrs. If the “sessionID” is used after this time period, then this error is displayed<br />- 302: The target flight is no longer available. Description: In the period between verify and book, the flight has been sold out. This can also be due to the number of passengers booked. The number of pax when booking and the number of pax when verifying may be different. When create a booking, the price is verified based on the actual number of pax booked<br />- 303: Airline closed. Description: Airline has either ceased to exist or not operational.<br />- 304: Verify failed. Description: In some uncontrollable situations, such as network issues, upgrades, and restarts, 304 error may occur, but not many. If there are many 304 errors, it is possible that the airline is not available or some technical issue at Atlas' end. Contact your account manager if this error keeps on repeating.<br />- 305: Invalid routing. Description: When generating an order, the system found that the flight was no longer sold for various reasons, such as 1) L2B 2) The system has identified that there may be a risk of the flight being sold out 3) The airline's sales have been closed<br />- 307: Illegal booking request parameters. Description: Some request parameters have problem. Please check the message.<br />- 308: Price changed. Description: The price has changed between the price verification and order. Please verify the price again and generate the order.<br />- 309: Ancillary not found. Description: Incorrect ancillary product code has been entered. Check and enter the correct ancillary product code.<br />- 310: Infant not allowed. Description: The offer does not support infant. Create a new booking without infant passenger type.<br />- 312: Too many seats booked. Description: The number of pax booked exceeds the remaining (or allowed) seats on the current flight.<br />- 313: Fare family sold out. Description: Selected offer is no longer available. Conduct the search again and rebook.<br />- 315: Not enough seats. Description: Seats have been sold out<br />- 316: Timed out. Description: There is a time-out error at the airline’s end<br />- 317: Booking unsuccessful with Airline. Description: An error has happened at the airline’s end.<br />- 318: Check if a booking with the same passenger details and flight numbers exists. After confirming, ignore this booking.<br />- 319: Flight information has changed. Description: Re-verify the price (query the latest flight information) and generate the order.<br />- 320: The requested seats were not found or they are already occupied. Description: Rebook seats and submit a new order.<br />- 321: <br />- 322: Seat price changed. Description: Seat price changed. Re-query the seat map and select seats<br />- 323: The format of the e-mail in the contact information is incorrect<br />- 324: Airline system issues. Description: Retry after some time. If the issue persists, please contact our operations team.<br />- 325: The airline has deemed the passenger unserviceable<br />- 326: Your account balance on the airline side is insufficient(BYOA scenario)<br />- 327: Passenger information does not meet the requirements. Description: Check and correct the passenger information according to the error message<br />- 328: Selected seat is no longer available. Description: The selected seat has been occupied.<br />- 329: No payment method is available. Description: No payment method is available. Please check whether the quotation currency or account configuration is correct.<br />- 330: operation is in progress. Description: operation is in progress<br />- 407: Some mandatory element for the passenger has not been submitted.. Description: Check the information and correct the same and resubmit.<br />- 408: Passenger can not board alone. Description: Create a new order and add an adult passenger with the child passenger<br />- 409: Additional baggage does not match the flight segment. Description: Luggage purchased for each segment of a connecting flight must be the same.<br />- 410: The contact information is not in the correct format.. Description: Check the contact information and confirm that it matches the required format.|
|» msg|[ResponseMessage](#schemaresponsemessage)|true|none||It serves as an additional description of the response result. Especially when the interface reports an error (`status` !=`0`), it is usually a human-readable error message. Note: Do not use this field in any programming scenarios. For example, do not judge whether the interface responds successfully based on this field. Instead, you should only determine it by checking whether the status is equal to`0`at any time.|
|» sessionId|string|true|none||Echo the`sessionId`in the request parameters.|
|» offerId|string¦null|false|none||Echo the`offerId`in the request parameters.|
|» orderNo|string|true|none||Order number of the created order.|
|» pnrCode|string|true|none||The pnrCode is the single reference for the booking. This is the Atlas PNR, not airline's.|
|» totalPrice|number|true|none||Total price(not including service fee) of this order in the currency TheAtlas settled with you|
|» totalTransactionFee|number|true|none||Total technical fees for this order in the currency TheAtlas settled with you.|
|» currency|string|true|none||The currency TheAtlas settled with you.|
|» vendorTotalPrice|number¦null|false|none||Total price of this order in the vendor's currency, reference for you to generate the specific credit card.|
|» vendorCurrency|string¦null|false|none||Vendor's currency.|
|» tktLimitTime|string|true|none||Payment deadline for this order. This time will be displayed in SGT (GMT +8). The fromat is:`yyyy-MM-dd HH:mm:ss`.|
|» paxTicketInfos|[object]|true|none||Ticket information for passengers. The number of elements is the same as the number of passengers, with each passenger corresponding to one element.|
|»» name|string|true|none||Echo the passenger's name, in the format of last name/first name|
|»» passengerType|[PassengerType](#schemapassengertype)|true|none||Echo the passenger's type.<br />- 0: Adult<br />- 1: Child<br />- 2: Infant|
|»» birthday|string|true|none||Echo the passenger's birthday|
|»» gender|string|true|none||Echo the passenger's gender|
|»» cardNum|string¦null|false|none||Echo the passenger's  identity document number|
|»» cardType|string¦null|false|none||Echo the passenger's  identity document type|
|»» cardIssuePlace|string¦null|false|none||Echo the country where the passenger's identification document was issued.|
|»» cardExpired|string¦null|false|none||Echo the expiration date of the passenger's identification document.|
|»» nationality|string¦null|false|none||Echo the passenger's nationality|
|»» ticketNos|[string]|true|none||Ticket numbers. Since the ticket hasn't been issued at this moment, the array will be empty(`[]`).|
|»» airlinePNRs|[string]|true|none||Since the airline side hasn't generated the order yet, the array is empty(`[]`).|
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
|» routing|[Routing](#schemarouting)|true|none||none|
|»» routingIdentifier|string|true|none||This unique string identifier is used to verify requests for a particular route.<br />**Note:**<br />Has a certain validity period (generally not exceeding 6 hours).|
|»» supportCreditTransPayment|string|true|none||This tag is used to identify if the fare is support to be paid using the client's credit card(known as vcc passthrough). This field has been deprecated, please use `supportPaymentMethods` instead.|
|»» supportPaymentMethods|[[PaymentMethod](#schemapaymentmethod)]|true|none||Support payment methods for this fare. If payment is not supported in any way, this will be `null`or`[]`. Each item in this array is one of the following:<br />- 1: deposit<br />- 3: vcc passthrough<br />- 4: BYOA(Bring Your Own Account)<br />- 5: MoR|
|»» currency|string|true|none||The currency in which Atlas settles transactions with you.|
|»» adultPrice|number|true|none||Adult fare per passenger.|
|»» adultTax|number|true|none||Adult tax per passenger.|
|»» adultDetails|[[PriceItem](#schemapriceitem)]¦null|false|none||Details of the adult price composition.|
|»»» code|string|true|none||Machine readable code used to identify this price item.|
|»»» type|string|true|none||Type of this price item.|
|»»» amount|number|true|none||none|
|»»» description|string¦null|false|none||Human-readable description for this price item.|
|»» childPrice|number|true|none||Child fare per passenger.|
|»» childTax|number|true|none||Child tax per passenger.|
|»» childDetails|[[PriceItem](#schemapriceitem)]¦null|false|none||Details of the child price composition.|
|»»» code|string|true|none||Machine readable code used to identify this price item.|
|»»» type|string|true|none||Type of this price item.|
|»»» amount|number|true|none||none|
|»»» description|string¦null|false|none||Human-readable description for this price item.|
|»» infantPrice|number|true|none||Infant fare per passenger.|
|»» infantTax|integer|true|none||Infant tax per passenger.|
|»» infantDetails|[[PriceItem](#schemapriceitem)]¦null|false|none||Details of the child infant composition.|
|»»» code|string|true|none||Machine readable code used to identify this price item.|
|»»» type|string|true|none||Type of this price item.|
|»»» amount|number|true|none||none|
|»»» description|string¦null|false|none||Human-readable description for this price item.|
|»» infantAllowed|boolean¦null|false|none||Since `infantPrice` and `infantTax` will never be `null`, when the fare does not support infants or is free for infants, both `infantPrice` and `infantTax` display `0`. In this case, you need this field to distinguish which situation it is.<br />**Scenario description:**<br />- `true`: infants is supported by this fare, `infantPrice` and `infantTax` will >= `0`<br />- `false`: infants is not supported by this fare, `infantPrice` and `infantTax`will be displayed as `0`|
|»» childMandatorySeatingFee|number¦null|false|none||Only valid for FR integration.<br /><br />**FR Seat Selection Rules:**<br />- Children under 12 years old are provided with free seats.<br />- Children must be seated in the same row as an adult.<br />- Each adult may accompany up to 4 children.<br /><br />For fare families that do not include seat selection fees (e.g., Basic or Family Plus), FR offers discounted seat selection fees for adults traveling with children. The`childMandatorySeatingFee`field displays this discounted fee.<br />For fare families that already include seat selection fees, this field will be `null`.<br /><br />**Handling by Atlas for Fare Families Without Seat Selection Fees:**<br />- The number of children cannot exceed 4.<br />- Customers cannot select seats manually.<br />- Atlas will automatically assign seats randomly to one adult and all children according to FR's rules. The adult will be charged the `childMandatorySeatingFee` for their seat.<br /><br />**For Fare Families That Include Seat Selection Fees:**<br />- Seat selection is free.<br />- Users may call the seat map API to select seats; otherwise, Atlas will automatically assign seats.|
|»» transactionFeePerPax|number|true|none||Technical service fee per passenger. This field has been deprecated and final total transaction fee will calculated based on `transactionFee` and `transactionFeeMode`.|
|»» transactionFee|number|true|none||Technical service fee as per `transactionFeeMode`. The following lists the calculation methods for the final technical service fee in various situations.<br />- `transactionFeeMode`=`PER_SEGMENT`:`transactionFee` * number of passengers * number of segments.<br />- `transactionFeeMode`=`PER_TICKET`:`transactionFee` * number of passengers * number of orders on airline side.<br />- `transactionFeeMode`=`PER_PAX`:`transactionFee` * number of passengers.<br />- `transactionFeeMode`=`PER_BOOKING`:`transactionFee`.|
|»» transactionFeeMode|[TransactionFeeMode](#schematransactionfeemode)|true|none||Calculation method for technical service fee.<br />- PER_SEGMENT: Calculate based on the number of segments in the order (number of travel segments * number of passengers)<br />- PER_TICKET: Calculate based on the number of orders on the airline's side<br />- PER_PAX: Calculate based on the number of passengers<br />- PER_BOOKING: Calculate based on each order|
|»» fromSegments|[[RoutingSegment](#schemaroutingsegment)]|true|none||For outbound segments.|
|»»» aircraftCode|string¦null|false|none||IATA Code of aircraft type|
|»»» arrAirport|string|true|none||3-letter iata code for the arrival airport at which the segment is scheduled to arrive.|
|»»» arrTerminal|string¦null|false|none||The terminal at the destination airport where the segment is scheduled to arrive.|
|»»» arrTime|string|true|none||The datetime at which the segment is scheduled to arrive, in the arrival airport timezone. The format is `YYYYMMDD`.|
|»»» cabin|string¦null|false|none||RBD(known as Reservation Booking Designator) displayed by the airline.|
|»»» cabinClass|[CabinClass](#schemacabinclass)|true|none||Cabin class of the segment.<br />- 1: economy<br />- 2: business<br />- 3: first<br />- 4: premium economy|
|»»» carrier|string|true|none||IATA code of marketing carrier.|
|»»» codeShare|boolean|true|none||A flag used to identify whether it is a code share flight.|
|»»» depAirport|string|true|none||3-letter iata code for the airport at which the segment is scheduled to depart.|
|»»» depTerminal|string¦null|false|none||The terminal at the departure airport from which the segment is scheduled to depart.|
|»»» depTime|string|true|none||The datetime at which the segment is scheduled to depart, in the departure airport timezone. The format is`YYYYMMSS`.|
|»»» duration|integer|true|none||The duration of the segment in munites.|
|»»» fareFamily|string|true|none||Fare Family as per the information received from the airline|
|»»» flightNumber|string|true|none||Marketing flight number. The format is: CA123 or TR021 or FR1290, with the first two letters representing the carrier and the following number representing the flight number.|
|»»» operatingCarrier|string¦null|false|none||2-letter iata code for the operating carrier. The airline actually operating this segment. This may differ from the marketing carrier in the case of a "codeshare", where one airline sells flights operated by another airline.|
|»»» operatingFlightnumber|string¦null|false|none||Operating flight number.|
|»»» seatCount|integer|true|none||Max booking seats for the fare.|
|»»» segmentIndex|integer|true|none||Segment sequence. Starts from 1. If it is return trip, sequence for outbound trip and inbound trip would be together. The segment index also represents the flight sequence of the segment.|
|»»» stopCities|string¦null|false|none||IATA code/Name of cities from where the passengers will take stopover flights. Include IATA code of cities and use a comma in case of multiple cities to separate transfer airports count is higher than 1. For example: `CGK, SUB`. <br />`null` or blank means non-stop flight.|
|»» retSegments|[[RoutingSegment](#schemaroutingsegment)]¦null|false|none||For inbound segments. For one-way, this field will be `null` or `[]`.|
|»»» aircraftCode|string¦null|false|none||IATA Code of aircraft type|
|»»» arrAirport|string|true|none||3-letter iata code for the arrival airport at which the segment is scheduled to arrive.|
|»»» arrTerminal|string¦null|false|none||The terminal at the destination airport where the segment is scheduled to arrive.|
|»»» arrTime|string|true|none||The datetime at which the segment is scheduled to arrive, in the arrival airport timezone. The format is `YYYYMMDD`.|
|»»» cabin|string¦null|false|none||RBD(known as Reservation Booking Designator) displayed by the airline.|
|»»» cabinClass|[CabinClass](#schemacabinclass)|true|none||Cabin class of the segment.<br />- 1: economy<br />- 2: business<br />- 3: first<br />- 4: premium economy|
|»»» carrier|string|true|none||IATA code of marketing carrier.|
|»»» codeShare|boolean|true|none||A flag used to identify whether it is a code share flight.|
|»»» depAirport|string|true|none||3-letter iata code for the airport at which the segment is scheduled to depart.|
|»»» depTerminal|string¦null|false|none||The terminal at the departure airport from which the segment is scheduled to depart.|
|»»» depTime|string|true|none||The datetime at which the segment is scheduled to depart, in the departure airport timezone. The format is`YYYYMMSS`.|
|»»» duration|integer|true|none||The duration of the segment in munites.|
|»»» fareFamily|string|true|none||Fare Family as per the information received from the airline|
|»»» flightNumber|string|true|none||Marketing flight number. The format is: CA123 or TR021 or FR1290, with the first two letters representing the carrier and the following number representing the flight number.|
|»»» operatingCarrier|string¦null|false|none||2-letter iata code for the operating carrier. The airline actually operating this segment. This may differ from the marketing carrier in the case of a "codeshare", where one airline sells flights operated by another airline.|
|»»» operatingFlightnumber|string¦null|false|none||Operating flight number.|
|»»» seatCount|integer|true|none||Max booking seats for the fare.|
|»»» segmentIndex|integer|true|none||Segment sequence. Starts from 1. If it is return trip, sequence for outbound trip and inbound trip would be together. The segment index also represents the flight sequence of the segment.|
|»»» stopCities|string¦null|false|none||IATA code/Name of cities from where the passengers will take stopover flights. Include IATA code of cities and use a comma in case of multiple cities to separate transfer airports count is higher than 1. For example: `CGK, SUB`. <br />`null` or blank means non-stop flight.|
|»» rule|object|true|none||none|
|»»» hasBaggage|integer|true|none||This tag is used to identify if the fare includes free checked-in or cabin baggage.<br />- `0`: Not included<br />- `1`: Included|
|»»» baggageElements|[object]|true|none||The free baggage allowance|
|»»»» segmentNo|integer|true|none||The index of segment the baggage allowance applies to.|
|»»»» baggageType|[AncillaryCategory](#schemaancillarycategory)|true|none||Type of the baggage.|
|»»»» passengerType|[PassengerType](#schemapassengertype)|true|none||The type of passenger the baggage allowance applies to.<br />- 0: Adult<br />- 1: Child<br />- 2: Infant|
|»»»» baggagePiece|integer|true|none||Baggage pieces:<br />- `0`: No limitation<br />- `>0`: Maximum pieces|
|»»»» baggageWeight|integer|true|none||Baggage Weight, with the unit of KG.<br />- `0`: No Free baggage<br />- `-1`: No limitation on weight<br />- `>0`: Maximum weight|
|»»»» baggageSize|string|true|none||Baggage Size:<br />length＊width＊height and units. eg. `56＊36＊23cm`, `18＊14＊8inch`.<br />Or Total dimensions (length + width + height) of each piece. eg. `L+W+H<=158cm`.<br />Empty means no limitation.|
|»»»» isAllWeight|boolean¦null|false|none||Baggage is all weight: true or false|
|»»» refundRules|[object]|true|none||This node is used to fetch the refund rules of the fare. There is only one array element for one way, and two elements for round-trip. The first element is for the outbound, and the second element is for the inbound.|
|»»»» refundType|integer|true|none||Type of refund allowed.<br />- 0: Wholly unused ticket<br />- 1: Partially used ticket (For example, when the passenger has used an outbound flight and wants to refund an inbound flight.)|
|»»»» refundStatus|[RefundStatus](#schemarefundstatus)|false|none||Refund rule types (for the most restrictive condition).<br />- T: Non refundable<br />- H: Refundable with restrictions<br />- F: Full refundable|
|»»»» refundFee|integer¦null|false|none||Refund penalty amount (for the most restrictive condition)|
|»»»» currency|string¦null|false|none||The currency of refund penalty|
|»»»» refNoshow|string|true|none||Indicates if a no-show affects refunds (for the most restrictive condition).<br />- T: Non refundable<br />- H: Refundable with restrictions<br />- F: Free for refund|
|»»»» refNoShowCondition|integer|true|none||Time before scheduled flight departure|
|»»»» refNoshowFee|number|true|none||Total refund fee (for the most restrictive condition): If refNoshow = H, it should not be "null". This value includes the refund fee and no-show penalty|
|»»»» refundMethod|string¦null|false|none||Refund method: CashBackToOriginalPayment or Voucher.<br />- CashBackToOriginalPayment: Refund cash back to the original form of payment.<br />- Voucher: Refund in the form of a voucher.|
|»»»» ruleDetailList|[[AirlineRuleRes](#schemaairlineruleres)]|false|none||none|
|»»»»» status|[RefundStatus](#schemarefundstatus)|true|none||Level of refund/change.<br />- T: Non refundable<br />- H: Refundable with restrictions<br />- F: Full refundable|
|»»»»» startMinute|string|true|none||Starting time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|»»»»» endMinute|string|true|none||Ending time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|»»»»» amount|string¦null|false|none||Penalty amount for refund/change. If the`status`indicates free refund/change, then this field will be either`0`or`null`.|
|»»»»» currency|string¦null|false|none||The currency of penalty|
|»»»»» refundMethod|string¦null|false|none||Refund method: CashBackToOriginalPayment or Voucher.<br />- CashBackToOriginalPayment: Refund cash back to the original form of payment.<br />- Voucher: Refund in the form of a voucher.|
|»»» changesRules|[object]|true|none||This node is used to fetch the change rules of the fare. There is only one array element for one way, and two elements for round-trip. The first element is for the outbound, and the second element is for the inbound.|
|»»»» changesType|integer|true|none||Change flight type.<br />- `0`: Wholly unused ticket<br />- `1`: Partially used ticket (For example. When the passenger has used an outbound flight and wants to change an inbound flight)|
|»»»» changesStatus|[ChangeStatus](#schemachangestatus)|false|none||Change flight rule type (for the most restrictive condition):<br />- T: Non changeable<br />- H: Changeable with restrictions<br />- F: Free rescheduling|
|»»»» changesFee|number¦null|false|none||Change flight fee (for the most restrictive condition):<br />- If`changesStatus`=`H`, it should not be`null`<br />- If`changesStatus`=`T/F`, it can be`null`|
|»»»» currency|string¦null|false|none||The currency of change flight fee|
|»»»» revNoshow|string|true|none||Indicates if a no-show affects changes (for the most restrictive condition).<br />Valid values:<br />- T: Non changeable<br />- H: Changeable with restrictions<br />- F: Free flight change|
|»»»» revNoShowCondition|integer|true|none||Time before scheduled flight departure.|
|»»»» revNoshowFee|number|true|none||The total fee charged to change flight in case of no show. If revNoshow = H, it should not be "null." This value includes the change flight fee and no-show penalty.|
|»»»» ruleDetailList|[object]|false|none||Change conditions|
|»»»»» status|[RefundStatus](#schemarefundstatus)|true|none||Level of refund/change.<br />- T: Non refundable<br />- H: Refundable with restrictions<br />- F: Full refundable|
|»»»»» startMinute|string|true|none||Starting time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|»»»»» endMinute|string|true|none||Ending time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|»»»»» amount|string¦null|false|none||Penalty amount for refund/change. If the`status`indicates free refund/change, then this field will be either`0`or`null`.|
|»»»»» currency|string¦null|false|none||The currency of penalty|
|»»» serviceElements|[object]¦null|false|none||This function is used to fetch the other service rules of the fare. There is only one array for one way, and two arrays for round-trip. The first array is for the outbound, and the second array is for the inbound.|
|»»»» hasFreeSeat|integer|false|none||A marker used to indicate whether free seat selection is included.<br />- `0`: Not included<br />- `1`: Included<br />- `2`: Partially free|
|»»»» hasFreeMeal|integer|false|none||A marker used to indicate whether free meals are included.<br />- `0`: Not included<br />- `1`: Included|
|»» ancillaryProductElements|[[AncillaryProduct](#schemaancillaryproduct)]¦null|false|none||none|
|»»» ancillaryCode|string|true|none||A code that is relatively readable by humans and contains information about auxiliary business specifications (such as weight and quantity limitations of luggage). <br />**Note:** <br />This content is only for display purposes and should not be used for programming purposes. That is to say, do not attempt to parse the information about auxiliary business specifications from this code. If you want to access the auxiliary business specifications, please use structured fields. For example, for luggage, please use`auxBaggageElement`.|
|»»» auxBaggageElement|object¦null|false|none||Baggage specification limitations. This node is valid only when the ancillary type (`categoryCode`) is baggage.|
|»»»» isAllWeight|boolean|true|none||Mark whether the`weight`field restricts the total weight or the weight of a single piece.<br />- `true`: The weight is for all the pieces<br />- `false`: The weight is for each piece|
|»»»» piece|integer|true|none||The maximum number of pieces that can be purchased per person.<br />- `0`: No Limitation about piece<br />- `>0`: Maximum pieces|
|»»»» size|string¦null|false|none||Maximum size for the baggage|
|»»»» weight|integer|true|none||The maximum weight that can be purchased per person.<br />- `0`: No limitation for weight<br />- `>0`: Weight limit (KG)|
|»»» canPurchasePostTicket|integer|true|none||A flag used to mark if this ancillary product can be purchased in the post-ticketing flow.<br />- `0`: No<br />- `1`: Yes|
|»»» canPurchaseWithTicket|integer|true|none||A flag used to mark if this ancillary product can be purchased during the booking flow.<br />- `0`: No<br />- `1`: Yes|
|»»» categoryCode|[AncillaryCategory](#schemaancillarycategory)|true|none||Type of the ancillary.<br /><br />- StandardCheckInBaggage: Standard Check-in Baggage.<br />- CabinBaggage: Usually refers to the Cabin Baggage Overhead Locker. Transition value. It will gradually transition to `CabinBaggageOverheadLocker`.<br />- CabinBaggageOverheadLocker: Cabin Baggage Overhead Locker.<br />- CabinBaggageUnderSeat: Cabin Baggage Under Seat. Usually refers to the personal item.|
|»»» clientTechnicalServiceFee|number¦null|false|none||The service fee charged by Atlas for the purchase of the ancillary.|
|»»» currency|string|true|none||The currency in which Atlas settles transactions with you|
|»»» maxQty|integer|true|none||The maximum number of purchases allowed per person per flight segment|
|»»» minQty|integer|true|none||The minimum quantity allowed to be purchased per person per flight segment.|
|»»» price|number|true|none||Price for this ancillary.|
|»»» productCode|string|true|none||Unique identifier for the ancillary product. It would be used in the order request.|
|»»» segmentIndex|integer|true|none||The index of segment the ancillary applies to.|
|»»» vendorCurrency|string|true|none||The currency in which the vendor charges for the ancillary. If the fare does not allow for the VCC pass-through or BYOA payment, this information will be`null`.|
|»»» vendorPrice|integer|true|none||The price charged by the vendor for the ancillary. If the fare does not allow for the VCC pass-through or BYOA payment, this information will be`null`.|
|»» vendorFare|object|true|none||To identify the vendor’s fare with vendor’s currency. It is only available when`supportPaymentMethods`contains`3`or`4`.|
|»»» vendorAdultPrice|number|true|none||Adult fare per passenger in vendor’s currency|
|»»» vendorAdultTax|number|true|none||Adult tax per passenger in vendor’s currency|
|»»» vendorChildPrice|number|true|none||Child fare per passenger in vendor’s currency|
|»»» vendorChildTax|number|true|none||Child tax per passenger in vendor’s currency|
|»»» vendorInfantPrice|number|true|none||Infant fare per passenger in vendor’s currency|
|»»» vendorInfantTax|integer|true|none||Infant tax per passenger in vendor’s currency|
|»»» vendorCurrency|string|true|none||Vendor’s currency|
|»» links|[TAndCLink](#schematandclink)|true|none||The terms and conditions links of the airlines. Will only return in verify response.|
|»»» carrier|string|true|none||IATA code for the airline|
|»»» kind|string|true|none||always:`terms`|
|»»» link|string|true|none||URL to the carrier's terms and conditions|
|»»» description|string|true|none||Carrier terms and conditions|
|»» separateBookings|boolean|true|none||When the outbound and inbound of round trip need to be booked separately, it will be true.|
|»» refreshTime|string|true|none||If the fare is from the cache of Atlas, this field is used to indicate the refresh time of the cache. The time is a certain moment in the past (UTC), and the format is:`yyyy-MM-dd'T'HH:mm:ss'Z'`.|
|»» expireTime|string|true|none||If the current fare comes from the cache of Atlas, this field is used to indicate the estimated expiration time of the cache. This time is a certain moment in the future (UTC), and the format is:`yyyy-MM-dd'T'HH:mm:ss'Z'`.<br />**Note:** <br />This time is estimated, which means Atlas may refresh the cache before or after that time.|
|»» ancillarySupported|[string]|true|none||A list of ancillary service types that the fare allows for additional purchase. Possible value contains:<br />- `luggage`<br />- `seat`: You can carry out the subsequent seat selection process through our seat map interface.|
|»» cardChargeList|[[CardCharge](#schemacardcharge)]¦null|false|none||Payment handling fee for MoR/VCC|
|»»» cardType|[CardType](#schemacardtype)|true|none||Card types, such as Visa, MasterCard|
|»»» percentage|number¦null|false|none||Percentage of payment handling fee|
|»»» charge|number¦null|false|none||The amount of payment handling fee|
|»»» currency|string¦null|false|none||Currency of `charge`|
|» duplicateOrders|[string]¦null|false|none||If the api returns error code`318`(duplicate booking), then the list will contain duplicate order numbers.|
|» paymentOptions|[object]|true|none||none|
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

#### 枚举值

|属性|值|
|---|---|
|status|301|
|status|302|
|status|303|
|status|304|
|status|305|
|status|307|
|status|308|
|status|309|
|status|310|
|status|312|
|status|313|
|status|315|
|status|316|
|status|317|
|status|318|
|status|319|
|status|320|
|status|321|
|status|322|
|status|323|
|status|324|
|status|325|
|status|326|
|status|327|
|status|328|
|status|329|
|status|330|
|status|407|
|status|408|
|status|409|
|status|410|
|passengerType|0|
|passengerType|1|
|passengerType|2|
|supportCreditTransPayment|0|
|supportCreditTransPayment|1|
|type|base|
|type|tax|
|type|fee|
|type|base|
|type|tax|
|type|fee|
|type|base|
|type|tax|
|type|fee|
|transactionFeeMode|PER_SEGMENT|
|transactionFeeMode|PER_TICKET|
|transactionFeeMode|PER_PAX|
|transactionFeeMode|PER_BOOKING|
|cabinClass|1|
|cabinClass|2|
|cabinClass|3|
|cabinClass|4|
|cabinClass|1|
|cabinClass|2|
|cabinClass|3|
|cabinClass|4|
|baggageType|StandardCheckInBaggage|
|baggageType|CabinBaggage|
|baggageType|CabinBaggageUnderSeat|
|baggageType|CabinBaggageOverheadLocker|
|passengerType|0|
|passengerType|1|
|passengerType|2|
|refundStatus|T|
|refundStatus|H|
|refundStatus|F|
|refundMethod|CashBackToOriginalPayment|
|refundMethod|Voucher|
|status|T|
|status|H|
|status|F|
|refundMethod|CashBackToOriginalPayment|
|refundMethod|Voucher|
|changesStatus|T|
|changesStatus|H|
|changesStatus|F|
|status|T|
|status|H|
|status|F|
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

## POST Order Commit

POST /orderCommit.do

This API is only required in the FR integration process. After create an order and before payment, you need to call this API to obtain the link of the FR order confirmation page and display it to users. Users should confirm the order through this page, and finally customer pay to Atlas.

**Endpoint:**
https://sandbox.atriptech.com/orderCommit.do

> Body 请求参数

```json
{
  "orderNo": "AMSEA20250816154139093",
  "redirectUri": "https://your_confirmation_url",
  "iframe": false,
  "timeout": 30000
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
|» orderNo|body|string| 是 |Order number|
|» redirectUri|body|string¦null| 否 |The redirect localtion to which when users confirm an order on the |
|» iframe|body|string¦null| 否 |If you want to display the FR's order confirmation page in `iframe` mode, please specify `iframe=true`, and in this case, the `redirectUri` will be ignored.|
|» timeout|body|integer¦null| 否 |Maximum response time of the API in milliseconds.|

#### 详细说明

**» redirectUri**: The redirect localtion to which when users confirm an order on the 
FR's confirmation page. If you choose to display the confirmation page in `Popup` mode, please specify this.

> 返回示例

> 200 Response

```json
{
  "confirmationUrl": "https://www.ryanair.com/gb/en/flights-confirmation?partnerId=ATLAS&session=63361e2d-50fa-409c-bdc6-019d87660889&redirectUri=https://your_confirmation_url",
  "status": 0,
  "msg": null
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
|» status|[OrderCommitResponseStatus](#schemaordercommitresponsestatus)|true|none||- 307: illegal booking request param<br />- 800: order not exists<br />- 316: timed out<br />- 317: airline error|
|» msg|[ResponseMessage](#schemaresponsemessage)¦null|false|none||It serves as an additional description of the response result. Especially when the interface reports an error (`status` !=`0`), it is usually a human-readable error message. Note: Do not use this field in any programming scenarios. For example, do not judge whether the interface responds successfully based on this field. Instead, you should only determine it by checking whether the status is equal to`0`at any time.|
|» confirmationUrl|string|true|none||The FR order confirmation page link.|

#### 枚举值

|属性|值|
|---|---|
|status|307|
|status|800|
|status|316|
|status|317|

## POST Payment

POST /pay.do

**Dependency:**
`Order` function should be called in prior to this call.

> - Atlas provides the information from the search.do API response itself whether VCC can be accepted as a mode of payment for an order. Please read the "supportCreditTransPayment" field in the search.do and verify.do responses. When this field is equal to "0" (zero), it means that only "deposit" mode of payment can be used and when this field is equal to "1" (one), it means that both the "deposit" as well as the "VCC" mode of payment can be used.
> - For VCC payments, the Test Cards to be used for testing in SANDBOX:
> Visa:
>    &#9702; 4532015112830366
>    &#9702; 4916931584764308
>    &#9702; 4485275742308327
>    &#9702; 4556737586899855
>    &#9702; 4532644189324563
> Mastercard:
>    &#9702; 5555555555554444
>    &#9702; 5105105105105100
>    &#9702; 5223456789012346
>    &#9702; 5301250070000191
>    &#9702; 5454545454545454
> American Express:
>    &#9702; 378282246310005
>    &#9702; 371449635398431
>    &#9702; 340000000000009
>    &#9702; 370000000000002
>    &#9702; 375987654321001
> Discover:
>    &#9702; 6011111111111117
>    &#9702; 6011000990139424
>    &#9702; 6011987612345678
> JCB:
>    &#9702; 3566002020360505

**Endpoint:**
https://sandbox.atriptech.com/pay.do

> Body 请求参数

```json
{
  "orderNo": "AFKMN20250819153129241",
  "paymentMethod": 3,
  "creditCard": {
    "cardNumber": "525797******8735",
    "cardCVV": "***",
    "cardExpireMonth": "07",
    "cardExpireYear": "2027",
    "cardHolderLastName": "C***",
    "cardHolderFirstName": "J******",
    "cardHolderCountry": "C*",
    "cardHolderProvince": "G*",
    "cardHolderCity": "S*******",
    "cardHolderPostCode": "5*****",
    "cardHolderAddress": "S************",
    "threeDS": null,
    "reusable": null,
    "paymentLimit": null
  },
  "clientOrderNo": null,
  "requestSource": null
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
|» orderNo|body|string| 是 |Order number you want to do the payment.|
|» paymentMethod|body|[PaymentMethod](#schemapaymentmethod)| 是 |The payment method you want to use|
|» creditCard|body|object¦null| 否 |Credit card. It is necessary when using MoR(`paymentMethod`=`5`) or VCC passthrough(`paymentMethod`=`3`) payment.|
|»» cardNumber|body|string| 是 |Credit card number that conforms to the Luhn algorithm.|
|»» cardCVV|body|string| 是 |The Card Verification Value (CVV). For vcc passthrough, CVV is required. When using MoR, the CVV is mandatory if the card is being used for the first time, and for subsequent uses, it can be left as `null` (not empty string `""`).|
|»» cardExpireMonth|body|string| 是 |The card expiry month as an integer with two digits(01-12), e.g. for February use 02.|
|»» cardExpireYear|body|string| 是 |The card expiry year as an integer with two digits, e.g. for 2026 use 26.|
|»» cardHolderLastName|body|string| 是 |Last name of the card holder|
|»» cardHolderFirstName|body|string| 是 |First name of the card holder|
|»» cardHolderCountry|body|string¦null| 否 |The ISO 3166-1 alpha-2 code for the country of the billing address associated with the card.|
|»» cardHolderProvince|body|string¦null| 否 |The state/province of the billing address associated with the card. Only use tow-letter code, for example, use "CA" and not "California".|
|»» cardHolderCity|body|string¦null| 否 |The city of the billing address associated with the card.|
|»» cardHolderPostCode|body|string¦null| 否 |The postal code of the billing address associated with the card.|
|»» cardHolderAddress|body|string¦null| 否 |The first/second line of the billing address associated with the card.|
|»» reusable|body|boolean¦null| 否 |A flag used to indicate whether it is a single-use card or a multi-use card.|
|»» paymentLimit|body|integer¦null| 否 |Certain airlines may experience fare change after payment submission due to their inability to hold seat reservations. You can use this parameter to set a maximum acceptable payment amount(in vendor currency) threshold. This is the maximum amount which can be used to create the booking using a VCC.|
|»» threeDS|body|object¦null| 否 |The information used for the 3DS verification. It is only required in the MoR payment scenario.|
|»»» ip|body|string| 是 |The device IP of the end user. By default, the system will use the source IP of the current request.|
|» clientOrderNo|body|string¦null| 否 |Order number at the customer side.|
|» requestSource|body|[RequestSource](#schemarequestsource)¦null| 否 |The tag to identify which channel does this traffic come from. For example: SkyScanner,Google,Oganic search,etc…|

#### 详细说明

**» paymentMethod**: The payment method you want to use
- 1: balance
- 3: vcc passthough
- 4: BYOA
- 5: MoR

**»» reusable**: A flag used to indicate whether it is a single-use card or a multi-use card.
-`true`: multiple-use card
-`false`: single-use card

**Explanation:**
Atlas hopes that users can inform us of this information because Atlas is cautious when making payments for multiple cards.
For example, when encountering unknown errors in payment to the airline, Atlas will not easily attempt to retry, as this may result in multiple deductions.

#### 枚举值

|属性|值|
|---|---|
|» paymentMethod|1|
|» paymentMethod|3|
|» paymentMethod|4|
|» paymentMethod|5|

> 返回示例

> 200 Response

```json
{
  "orderNo": "AFKMN20250819153129241",
  "pnrCode": "SOVID9",
  "paymentMethod": 3,
  "airlines": [
    "5J"
  ],
  "status": 0,
  "msg": "success"
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
|» status|[PaymentResponseStatus](#schemapaymentresponsestatus)|true|none||- 400: Illegal request param. Description: Check and correct the request parameters according to the error message.<br />- 401: Later than the payment deadline. Description: Payment for the booking was initiated later than the payment deadline.<br />- 402: Order status does not support payment. Description: The order status maybe “ticketing” or “ticketed” where the payment has already been made. Check if the order status is unpaid<br />- 403: Unsupported payment method. Description: The payment method is not supported for this order.<br />- 404: The order is already paid. Description: Check if the order has been paid. If “yes”, do not send the payment request<br />- 406: Payment operation is in progress. Description: The previous payment request is still in process. Wait for the airline PNR to be received in the PNR details response.<br />- 407: Some mandatory element for the passenger has not been submitted.. Description: Check the information and correct the same and resubmit.<br />- 408: Passenger can not board alone. Description: Create a new order and add an adult passenger with the child passenger<br />- 409: Additional baggage does not match the flight segment. Description: Luggage purchased for each segment of a connecting flight must be the same.<br />- 410: The contact information is not in the correct format.. Description: Check the contact information and confirm that it matches the required format.<br />- 411: Some error happened with the payment gateway. Description: Some error happened with the payment gateway<br />- 412: No available payment methods. Description: No available payment methods for this order<br />- 413: Card is not supported. Description: For MoR, the brand of the card sent by customer is not supported by Atlas.<br />- 414: Card mismatch. Description: The brand of the card sent during payment is inconsistent with the "cardType" sent when generating the order.<br />- 415: order is not confirmed by user. Description: order is not confirmed by user|
|» msg|[ResponseMessage](#schemaresponsemessage)¦null|false|none||It serves as an additional description of the response result. Especially when the interface reports an error (`status` !=`0`), it is usually a human-readable error message. Note: Do not use this field in any programming scenarios. For example, do not judge whether the interface responds successfully based on this field. Instead, you should only determine it by checking whether the status is equal to`0`at any time.|
|» orderNo|string|true|none||Echo the order number|
|» paymentMethod|[PaymentMethod](#schemapaymentmethod)|true|none||Payment method|

#### 枚举值

|属性|值|
|---|---|
|status|400|
|status|401|
|status|402|
|status|403|
|status|404|
|status|406|
|status|407|
|status|408|
|status|409|
|status|410|
|status|411|
|status|412|
|status|413|
|status|414|
|status|415|
|paymentMethod|1|
|paymentMethod|3|
|paymentMethod|4|
|paymentMethod|5|

## POST Retrieve Booking

POST /queryOrderDetails.do

**Dependency:**
`Order` function should be called in prior to this call.

> Please refer to the below information for the usage of the queryOrderDetails.do API.
>   1. All the parameters can be used together, if required.
>   2. “OrderNo” is “required” if “airlinePNR” and “carrier” cannot be provided upon calling the API. Inversely, “airlinePNR” and “carrier” are “required” if “OrderNo” cannot be provided. All remaining fields in the request are optional.
>   3. The PNR (Passenger Name Record) for an airline ticket order or a luggage purchase order must be kept consistent, as per airline regulations.
>   4. The input parameters orderNo, airlinePNR, carrier, and other optional fields will be validated together to ensure they belong to the same order data source. If any of these input parameters do not match with others, the API will return an error.
>   5. Airline ticket orders and associated post-booking ancillary orders can be retrieved using the following methods: (airline ticket orders + post-booking ancillary orders):
>      * orderNo
>      * airlinePNR + carrier
>      * orderNo + airlinePNR + carrier
>      * orderNo + airlinePNR + carrier + other optional parameters
>   6. In case the parameters of “airlinePNR” and “carrier” cannot identify an unique order (e.g BC - PNR is made up with 4 number), customer needs to enter additional parameters such as "name" for identification. In such scenarios, API will respond with error msg ”Multi-orderNos are identified, please request again with extra parameters added.”

**Endpoint:**
https://sandbox.atriptech.com/queryOrderDetails.do

> Body 请求参数

```json
{
  "orderNo": "TESTA20250816160804096"
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
|» orderNo|body|string¦null| 否 |Order number of the order you want to retrieve|
|» pnrCode|body|string¦null| 否 |The pnrCode is the single reference for the booking. This is the Atlas PNR.|

> 返回示例

```json
{
  "status": 0,
  "msg": "success",
  "orderNo": "TESTA20250210154142832",
  "pnrCode": "XVOCMN",
  "orderStatus": "2",
  "ticketStatus": "1",
  "paxTicketInfos": [
    {
      "name": "aaaaa/aaaaaabs",
      "passengerType": 0,
      "birthday": "19900101",
      "gender": "M",
      "cardNum": "636940383",
      "cardType": "NATIONAL_ID_CARD",
      "cardIssuePlace": "PT",
      "cardExpired": "20250101",
      "nationality": "US",
      "ticketNos": [
        "S77182"
      ],
      "airlinePNRs": [
        "S77182"
      ],
      "contactEmails": [
        "jane.smith@example.com"
      ],
      "contactPhones": [
        "0001-982736245"
      ],
      "ancillaries": []
    }
  ],
  "totalPrice": 114.99,
  "currency": "USD",
  "tktLimitTime": "2025-02-11 16:31:43",
  "vendorTotalPrice": 1281.9,
  "vendorCost": 1346,
  "vendorTotalAncillaryPrice": 0,
  "vendorCurrency": "NOK",
  "adultTotalFare": 114.99,
  "childTotalFare": 114.99,
  "infantTotalFare": 96.74,
  "totalAncillaryPrice": 0,
  "totalTransactionFee": 5,
  "supportPaymentMethod": 3,
  "supportPaymentMethods": [
    1,
    3,
    5
  ],
  "paymentMethod": 5,
  "routing": {
    "routingIdentifier": "TE9OX1BBUl8yXzIwMjUwODE4XzIwMjUwODIwXzFfMF8wfHR2aWluNjU0Mjh8MXwyNDIuMTRfMjQyLjE0XzY0LjE3XzIuMDBfNTUwLjQ1X1VTRHxMT05fUEFSXzFfMjAyNTA4MThfMjAyNTA4MjBfMV8wXzBeTEdXLVUyODQwNS0tQ0RHLTIwMjUwODE4MTY0MC0yMDI1MDgxODE4NTUtU3RhbmRhcmQtMS0jQ0RHLVUyODQxMC0tTEdXLTIwMjUwODIwMTkxMC0yMDI1MDgyMDE5MjAtU3RhbmRhcmQtMi1eMjQyLjE0XzI0Mi4xNF82NC4xN18yLjAwXzU1MC40NV5BRUNBRVVSX0FFQ15eQUVDMkxPTlBBUjIwMDIwMjUwODE4MjAyNTA4MjBeR0JQXjE3OC4zMl4xNzguMzJeNDcuMjVeMHwwfDIwMjUwODE2MTU1NzQ1fDB8MTc1NTMzMTA2NTU0MkJOYm1HfHx8fHwyLjAwfDN8MHx8bm9ybWFsfGZhbHNl.5FDcOQsu5zTUOBN/jPsM23gT5WuaPAs7g8AmH8q/m0U=",
    "supportCreditTransPayment": "0",
    "supportPaymentMethods": [
      1,
      5
    ],
    "currency": "USD",
    "adultPrice": 242.14,
    "adultTax": 0,
    "adultDetails": [
      {
        "code": "farePrice",
        "type": "base",
        "amount": 242.14,
        "description": ""
      },
      {
        "code": "tax",
        "type": "tax",
        "amount": 0,
        "description": ""
      }
    ],
    "childPrice": 242.14,
    "childTax": 0,
    "childDetails": [
      {
        "code": "farePrice",
        "type": "base",
        "amount": 242.14,
        "description": ""
      },
      {
        "code": "tax",
        "type": "tax",
        "amount": 0,
        "description": ""
      }
    ],
    "infantPrice": 64.17,
    "infantTax": 0,
    "infantDetails": [
      {
        "code": "farePrice",
        "type": "base",
        "amount": 64.17,
        "description": ""
      },
      {
        "code": "tax",
        "type": "tax",
        "amount": 0,
        "description": ""
      }
    ],
    "infantAllowed": true,
    "childMandatorySeatingFee": null,
    "transactionFeePerPax": 2,
    "transactionFee": 2,
    "transactionFeeMode": "PER_PAX",
    "fromSegments": [
      {
        "segmentIndex": 1,
        "carrier": "U2",
        "flightNumber": "U28405",
        "depAirport": "LGW",
        "depTime": "202508181640",
        "arrAirport": "CDG",
        "arrTime": "202508181855",
        "stopCities": null,
        "duration": 75,
        "codeShare": false,
        "cabin": "",
        "cabinClass": 1,
        "seatCount": 9,
        "aircraftCode": "",
        "depTerminal": "",
        "arrTerminal": "",
        "operatingCarrier": "",
        "operatingFlightnumber": "",
        "fareFamily": "Standard"
      }
    ],
    "retSegments": [
      {
        "segmentIndex": 2,
        "carrier": "U2",
        "flightNumber": "U28410",
        "depAirport": "CDG",
        "depTime": "202508201910",
        "arrAirport": "LGW",
        "arrTime": "202508201920",
        "stopCities": null,
        "duration": 70,
        "codeShare": false,
        "cabin": "",
        "cabinClass": 1,
        "seatCount": 9,
        "aircraftCode": "",
        "depTerminal": "",
        "arrTerminal": "",
        "operatingCarrier": "",
        "operatingFlightnumber": "",
        "fareFamily": "Standard"
      }
    ],
    "rule": {
      "hasBaggage": 1,
      "baggageElements": [
        {
          "segmentNo": 1,
          "baggageType": "CabinBaggageUnderSeat",
          "passengerType": 0,
          "baggagePiece": 1,
          "baggageWeight": 15,
          "baggageSize": "45*36*20cm"
        },
        {
          "segmentNo": 1,
          "baggageType": "StandardCheckInBaggage",
          "passengerType": 0,
          "baggagePiece": 0,
          "baggageWeight": 0,
          "baggageSize": ""
        },
        {
          "segmentNo": 2,
          "baggageType": "CabinBaggageUnderSeat",
          "passengerType": 0,
          "baggagePiece": 1,
          "baggageWeight": 15,
          "baggageSize": "45*36*20cm"
        },
        {
          "segmentNo": 2,
          "baggageType": "StandardCheckInBaggage",
          "passengerType": 0,
          "baggagePiece": 0,
          "baggageWeight": 0,
          "baggageSize": ""
        }
      ],
      "refundRules": [
        {
          "refundType": 0,
          "refundStatus": "T",
          "refundMethod": "CASH_BACK_TO_ORIGINAL_PAYMENT",
          "refundFee": 0,
          "currency": "GBP",
          "refNoshow": "T",
          "refNoShowCondition": 0,
          "refNoshowFee": 0,
          "ruleDetailList": [
            {
              "status": "T",
              "refundMethod": "CashBackToOriginalPayment",
              "startMinute": 525600,
              "endMinute": 0,
              "amount": 0,
              "currency": "GBP"
            },
            {
              "status": "T",
              "refundMethod": "CashBackToOriginalPayment",
              "startMinute": 0,
              "endMinute": -525600,
              "amount": 0,
              "currency": "GBP"
            }
          ]
        },
        {
          "refundType": 0,
          "refundStatus": "T",
          "refundMethod": "CASH_BACK_TO_ORIGINAL_PAYMENT",
          "refundFee": 0,
          "currency": "GBP",
          "refNoshow": "T",
          "refNoShowCondition": 0,
          "refNoshowFee": 0,
          "ruleDetailList": [
            {
              "status": "T",
              "refundMethod": "CashBackToOriginalPayment",
              "startMinute": 525600,
              "endMinute": 0,
              "amount": 0,
              "currency": "GBP"
            },
            {
              "status": "T",
              "refundMethod": "CashBackToOriginalPayment",
              "startMinute": 0,
              "endMinute": -525600,
              "amount": 0,
              "currency": "GBP"
            }
          ]
        }
      ],
      "changesRules": [
        {
          "changesType": 0,
          "changesStatus": "T",
          "changesFee": 0,
          "currency": "GBP",
          "revNoshow": "T",
          "revNoShowCondition": 0,
          "revNoshowFee": 0,
          "ruleDetailList": [
            {
              "status": "H",
              "startMinute": 525600,
              "endMinute": 86400,
              "amount": 30,
              "currency": "GBP"
            },
            {
              "status": "H",
              "startMinute": 86400,
              "endMinute": 120,
              "amount": 49,
              "currency": "GBP"
            },
            {
              "status": "T",
              "startMinute": 120,
              "endMinute": 0,
              "amount": 0,
              "currency": "GBP"
            },
            {
              "status": "T",
              "startMinute": 0,
              "endMinute": -525600,
              "amount": 0,
              "currency": "GBP"
            }
          ]
        },
        {
          "changesType": 0,
          "changesStatus": "T",
          "changesFee": 0,
          "currency": "GBP",
          "revNoshow": "T",
          "revNoShowCondition": 0,
          "revNoshowFee": 0,
          "ruleDetailList": [
            {
              "status": "H",
              "startMinute": 525600,
              "endMinute": 86400,
              "amount": 30,
              "currency": "GBP"
            },
            {
              "status": "H",
              "startMinute": 86400,
              "endMinute": 120,
              "amount": 49,
              "currency": "GBP"
            },
            {
              "status": "T",
              "startMinute": 120,
              "endMinute": 0,
              "amount": 0,
              "currency": "GBP"
            },
            {
              "status": "T",
              "startMinute": 0,
              "endMinute": -525600,
              "amount": 0,
              "currency": "GBP"
            }
          ]
        }
      ],
      "serviceElements": [
        {
          "hasFreeSeat": 0,
          "hasFreeMeal": 0
        },
        {
          "hasFreeSeat": 0,
          "hasFreeMeal": 0
        }
      ]
    },
    "ancillaryProductElements": [
      {
        "ancillaryCode": "CBOL_1PC_15KG_MAXIMUM SIZE 56 X 45 X 25 CM",
        "auxBaggageElement": {
          "piece": 1,
          "weight": 15,
          "isAllWeight": true,
          "size": "Maximum Size 56 x 45 x 25 cm"
        },
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 0,
        "categoryCode": "CabinBaggageOverheadLocker",
        "clientTechnicalServiceFee": 0,
        "currency": "USD",
        "maxQty": 1,
        "minQty": 1,
        "price": 26.57,
        "productCode": "CBOL_1PC_15KG_MAXIMUM SIZE 56 X 45 X 25 CM",
        "segmentIndex": 1,
        "vendorPrice": 19.56,
        "vendorCurrency": "GBP"
      },
      {
        "segmentIndex": 1,
        "productCode": "SCI_BAG_1PC_15KG",
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 0,
        "price": 27.12,
        "currency": "USD",
        "vendorPrice": 19.97,
        "vendorCurrency": "GBP",
        "clientTechnicalServiceFee": 0,
        "auxBaggageElement": {
          "piece": 1,
          "weight": 15,
          "isAllWeight": true,
          "size": ""
        },
        "maxQty": 1,
        "minQty": 1,
        "categoryCode": "StandardCheckInBaggage",
        "ancillaryCode": "SCI_BAG_1PC_15KG"
      },
      {
        "segmentIndex": 1,
        "productCode": "SCI_BAG_2PC_30KG",
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 0,
        "price": 39.95,
        "currency": "USD",
        "vendorPrice": 29.42,
        "vendorCurrency": "GBP",
        "clientTechnicalServiceFee": 0,
        "auxBaggageElement": {
          "piece": 2,
          "weight": 30,
          "isAllWeight": true,
          "size": ""
        },
        "maxQty": 1,
        "minQty": 1,
        "categoryCode": "StandardCheckInBaggage",
        "ancillaryCode": "SCI_BAG_2PC_30KG"
      },
      {
        "segmentIndex": 2,
        "productCode": "CBOL_1PC_15KG_MAXIMUM SIZE 56 X 45 X 25 CM",
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 0,
        "price": 41.67,
        "currency": "USD",
        "vendorPrice": 30.69,
        "vendorCurrency": "GBP",
        "clientTechnicalServiceFee": 0,
        "auxBaggageElement": {
          "piece": 1,
          "weight": 15,
          "isAllWeight": true,
          "size": "Maximum Size 56 x 45 x 25 cm"
        },
        "maxQty": 1,
        "minQty": 1,
        "categoryCode": "CabinBaggageOverheadLocker",
        "ancillaryCode": "CBOL_1PC_15KG_MAXIMUM SIZE 56 X 45 X 25 CM"
      },
      {
        "segmentIndex": 2,
        "productCode": "SCI_BAG_1PC_15KG",
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 0,
        "price": 31.09,
        "currency": "USD",
        "vendorPrice": 22.9,
        "vendorCurrency": "GBP",
        "clientTechnicalServiceFee": 0,
        "auxBaggageElement": {
          "piece": 1,
          "weight": 15,
          "isAllWeight": true,
          "size": ""
        },
        "maxQty": 1,
        "minQty": 1,
        "categoryCode": "StandardCheckInBaggage",
        "ancillaryCode": "SCI_BAG_1PC_15KG"
      },
      {
        "segmentIndex": 2,
        "productCode": "SCI_BAG_2PC_30KG",
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 0,
        "price": 74.57,
        "currency": "USD",
        "vendorPrice": 54.91,
        "vendorCurrency": "GBP",
        "clientTechnicalServiceFee": 0,
        "auxBaggageElement": {
          "piece": 2,
          "weight": 30,
          "isAllWeight": true,
          "size": ""
        },
        "maxQty": 1,
        "minQty": 1,
        "categoryCode": "StandardCheckInBaggage",
        "ancillaryCode": "SCI_BAG_2PC_30KG"
      }
    ],
    "vendorFare": null,
    "links": [],
    "separateBookings": false,
    "refreshTime": null,
    "expireTime": null,
    "ancillarySupported": [
      "seat",
      "luggage"
    ],
    "cardChargeList": [
      {
        "cardType": "Visa",
        "percentage": 0.03,
        "charge": null,
        "currency": ""
      },
      {
        "cardType": "MasterCard",
        "percentage": 0.03,
        "charge": null,
        "currency": ""
      }
    ]
  },
  "airlineBookings": [
    {
      "airlineCode": "D8",
      "airlineName": "Norwegian Air Sweden",
      "airlinePnr": "S77182",
      "airlineWebSiteAddress": "https://www.norwegian.com",
      "mmbEmail": "jane.smith@example.com",
      "tailDigitsOfPaymentCard": null
    }
  ],
  "itineraryDownload": "http://121.40.236.223:8081/itineraryDownload.do?orderNo=FKEm34znpwya%2FiJBirhBW5YFgj2M7dX4",
  "contact": {
    "name": "Smith/Jane",
    "address": "189, Sky Garden Walk/London/US/US",
    "postcode": "EC3M 8AF",
    "email": "jane.smith@example.com",
    "mobile": "0001-982736245"
  },
  "errorCode": null,
  "errorMessage": null,
  "airlineMessage": null,
  "locale": "",
  "refundRules": [
    {
      "airline": "D8",
      "ruleType": "1",
      "passengerType": "",
      "penaltyAmount": null,
      "penaltyPercent": null,
      "penaltyPercentBase": null,
      "airlineFee": null,
      "taxRefundable": false,
      "fareRefundable": false,
      "refundableAncillaries": null,
      "startMinute": 525600,
      "endMinute": 0,
      "refundMethod": "CashBackToOriginalPayment"
    },
    {
      "airline": "D8",
      "ruleType": "1",
      "passengerType": "",
      "penaltyAmount": null,
      "penaltyPercent": null,
      "penaltyPercentBase": null,
      "airlineFee": null,
      "taxRefundable": false,
      "fareRefundable": false,
      "refundableAncillaries": null,
      "startMinute": 0,
      "endMinute": -525600,
      "refundMethod": "CashBackToOriginalPayment"
    },
    {
      "airline": "D8",
      "ruleType": "0",
      "passengerType": "",
      "penaltyAmount": "0",
      "penaltyPercent": 0,
      "penaltyPercentBase": null,
      "airlineFee": "0",
      "taxRefundable": true,
      "fareRefundable": true,
      "refundableAncillaries": [],
      "startMinute": 525600,
      "endMinute": 300,
      "refundMethod": "CashBackToOriginalPayment"
    },
    {
      "airline": "D8",
      "ruleType": "0",
      "passengerType": "",
      "penaltyAmount": "0",
      "penaltyPercent": 0,
      "penaltyPercentBase": null,
      "airlineFee": "0",
      "taxRefundable": true,
      "fareRefundable": true,
      "refundableAncillaries": [],
      "startMinute": 525600,
      "endMinute": -525600,
      "refundMethod": "CashBackToOriginalPayment"
    },
    {
      "airline": "D8",
      "ruleType": "0",
      "passengerType": "",
      "penaltyAmount": null,
      "penaltyPercent": null,
      "penaltyPercentBase": null,
      "airlineFee": null,
      "taxRefundable": false,
      "fareRefundable": false,
      "refundableAncillaries": null,
      "startMinute": 300,
      "endMinute": -300,
      "refundMethod": "CashBackToOriginalPayment"
    },
    {
      "airline": "D8",
      "ruleType": "0",
      "passengerType": "",
      "penaltyAmount": "0",
      "penaltyPercent": 0,
      "penaltyPercentBase": null,
      "airlineFee": "0",
      "taxRefundable": true,
      "fareRefundable": true,
      "refundableAncillaries": [],
      "startMinute": -300,
      "endMinute": -525600,
      "refundMethod": "CashBackToOriginalPayment"
    }
  ],
  "ifSeatOccupied": "SIMILAR_SEAT",
  "paymentOptions": null,
  "payment": {
    "paymentMethod": 5,
    "serviceFee": {
      "amount": 5,
      "currency": "USD",
      "deductFrom": "DEPOSIT"
    },
    "ticketFare": {
      "amount": 111.41,
      "currency": "EUR",
      "deductFrom": "CARD"
    },
    "paymentFee": {
      "amount": 4.8,
      "currency": "EUR",
      "deductFrom": "CARD"
    },
    "cardType": null
  },
  "paymentAttempted": null
}
```

```json
{
  "status": 0,
  "msg": "success",
  "orderNo": "TESTA20250210154142832",
  "pnrCode": "XVOCMN",
  "orderStatus": "2",
  "ticketStatus": "1",
  "paxTicketInfos": [
    {
      "name": "aaaaa/aaaaaabs",
      "passengerType": 0,
      "birthday": "19900101",
      "gender": "M",
      "cardNum": "636940383",
      "cardType": "NATIONAL_ID_CARD",
      "cardIssuePlace": "PT",
      "cardExpired": "20250101",
      "nationality": "US",
      "ticketNos": [
        "S77182",
        "X67745"
      ],
      "airlinePNRs": [
        "S77182",
        "X67745"
      ],
      "contactEmails": [
        "jane.smith@example.com",
        "jane.smith@example.com"
      ],
      "contactPhones": [
        "0001-982736245",
        "0001-982736245"
      ],
      "ancillaries": []
    }
  ],
  "totalPrice": 114.99,
  "currency": "USD",
  "tktLimitTime": "2025-02-11 16:31:43",
  "vendorTotalPrice": 1281.9,
  "vendorCost": 1346,
  "vendorTotalAncillaryPrice": 0,
  "vendorCurrency": "NOK",
  "adultTotalFare": 114.99,
  "childTotalFare": 114.99,
  "infantTotalFare": 96.74,
  "totalAncillaryPrice": 0,
  "totalTransactionFee": 5,
  "supportPaymentMethod": 3,
  "supportPaymentMethods": [
    1,
    3,
    5
  ],
  "paymentMethod": 5,
  "routing": {
    "routingIdentifier": "TE9OX1BBUl8yXzIwMjUwODE4XzIwMjUwODIwXzFfMF8wfHR2aWluNjU0Mjh8MXwyNDIuMTRfMjQyLjE0XzY0LjE3XzIuMDBfNTUwLjQ1X1VTRHxMT05fUEFSXzFfMjAyNTA4MThfMjAyNTA4MjBfMV8wXzBeTEdXLVUyODQwNS0tQ0RHLTIwMjUwODE4MTY0MC0yMDI1MDgxODE4NTUtU3RhbmRhcmQtMS0jQ0RHLVUyODQxMC0tTEdXLTIwMjUwODIwMTkxMC0yMDI1MDgyMDE5MjAtU3RhbmRhcmQtMi1eMjQyLjE0XzI0Mi4xNF82NC4xN18yLjAwXzU1MC40NV5BRUNBRVVSX0FFQ15eQUVDMkxPTlBBUjIwMDIwMjUwODE4MjAyNTA4MjBeR0JQXjE3OC4zMl4xNzguMzJeNDcuMjVeMHwwfDIwMjUwODE2MTU1NzQ1fDB8MTc1NTMzMTA2NTU0MkJOYm1HfHx8fHwyLjAwfDN8MHx8bm9ybWFsfGZhbHNl.5FDcOQsu5zTUOBN/jPsM23gT5WuaPAs7g8AmH8q/m0U=",
    "supportCreditTransPayment": "0",
    "supportPaymentMethods": [
      1,
      5
    ],
    "currency": "USD",
    "adultPrice": 242.14,
    "adultTax": 0,
    "adultDetails": [
      {
        "code": "farePrice",
        "type": "base",
        "amount": 242.14,
        "description": ""
      },
      {
        "code": "tax",
        "type": "tax",
        "amount": 0,
        "description": ""
      }
    ],
    "childPrice": 242.14,
    "childTax": 0,
    "childDetails": [
      {
        "code": "farePrice",
        "type": "base",
        "amount": 242.14,
        "description": ""
      },
      {
        "code": "tax",
        "type": "tax",
        "amount": 0,
        "description": ""
      }
    ],
    "infantPrice": 64.17,
    "infantTax": 0,
    "infantDetails": [
      {
        "code": "farePrice",
        "type": "base",
        "amount": 64.17,
        "description": ""
      },
      {
        "code": "tax",
        "type": "tax",
        "amount": 0,
        "description": ""
      }
    ],
    "infantAllowed": true,
    "childMandatorySeatingFee": null,
    "transactionFeePerPax": 2,
    "transactionFee": 2,
    "transactionFeeMode": "PER_PAX",
    "fromSegments": [
      {
        "segmentIndex": 1,
        "carrier": "U2",
        "flightNumber": "U28405",
        "depAirport": "LGW",
        "depTime": "202508181640",
        "arrAirport": "CDG",
        "arrTime": "202508181855",
        "stopCities": null,
        "duration": 75,
        "codeShare": false,
        "cabin": "",
        "cabinClass": 1,
        "seatCount": 9,
        "aircraftCode": "",
        "depTerminal": "",
        "arrTerminal": "",
        "operatingCarrier": "",
        "operatingFlightnumber": "",
        "fareFamily": "Standard"
      }
    ],
    "retSegments": [
      {
        "segmentIndex": 2,
        "carrier": "U2",
        "flightNumber": "U28410",
        "depAirport": "CDG",
        "depTime": "202508201910",
        "arrAirport": "LGW",
        "arrTime": "202508201920",
        "stopCities": null,
        "duration": 70,
        "codeShare": false,
        "cabin": "",
        "cabinClass": 1,
        "seatCount": 9,
        "aircraftCode": "",
        "depTerminal": "",
        "arrTerminal": "",
        "operatingCarrier": "",
        "operatingFlightnumber": "",
        "fareFamily": "Standard"
      }
    ],
    "rule": {
      "hasBaggage": 1,
      "baggageElements": [
        {
          "segmentNo": 1,
          "baggageType": "CabinBaggageUnderSeat",
          "passengerType": 0,
          "baggagePiece": 1,
          "baggageWeight": 15,
          "baggageSize": "45*36*20cm"
        },
        {
          "segmentNo": 1,
          "baggageType": "StandardCheckInBaggage",
          "passengerType": 0,
          "baggagePiece": 0,
          "baggageWeight": 0,
          "baggageSize": ""
        },
        {
          "segmentNo": 2,
          "baggageType": "CabinBaggageUnderSeat",
          "passengerType": 0,
          "baggagePiece": 1,
          "baggageWeight": 15,
          "baggageSize": "45*36*20cm"
        },
        {
          "segmentNo": 2,
          "baggageType": "StandardCheckInBaggage",
          "passengerType": 0,
          "baggagePiece": 0,
          "baggageWeight": 0,
          "baggageSize": ""
        }
      ],
      "refundRules": [
        {
          "refundType": 0,
          "refundStatus": "T",
          "refundMethod": "CASH_BACK_TO_ORIGINAL_PAYMENT",
          "refundFee": 0,
          "currency": "GBP",
          "refNoshow": "T",
          "refNoShowCondition": 0,
          "refNoshowFee": 0,
          "ruleDetailList": [
            {
              "status": "T",
              "refundMethod": "CashBackToOriginalPayment",
              "startMinute": 525600,
              "endMinute": 0,
              "amount": 0,
              "currency": "GBP"
            },
            {
              "status": "T",
              "refundMethod": "CashBackToOriginalPayment",
              "startMinute": 0,
              "endMinute": -525600,
              "amount": 0,
              "currency": "GBP"
            }
          ]
        },
        {
          "refundType": 0,
          "refundStatus": "T",
          "refundMethod": "CASH_BACK_TO_ORIGINAL_PAYMENT",
          "refundFee": 0,
          "currency": "GBP",
          "refNoshow": "T",
          "refNoShowCondition": 0,
          "refNoshowFee": 0,
          "ruleDetailList": [
            {
              "status": "T",
              "refundMethod": "CashBackToOriginalPayment",
              "startMinute": 525600,
              "endMinute": 0,
              "amount": 0,
              "currency": "GBP"
            },
            {
              "status": "T",
              "refundMethod": "CashBackToOriginalPayment",
              "startMinute": 0,
              "endMinute": -525600,
              "amount": 0,
              "currency": "GBP"
            }
          ]
        }
      ],
      "changesRules": [
        {
          "changesType": 0,
          "changesStatus": "T",
          "changesFee": 0,
          "currency": "GBP",
          "revNoshow": "T",
          "revNoShowCondition": 0,
          "revNoshowFee": 0,
          "ruleDetailList": [
            {
              "status": "H",
              "startMinute": 525600,
              "endMinute": 86400,
              "amount": 30,
              "currency": "GBP"
            },
            {
              "status": "H",
              "startMinute": 86400,
              "endMinute": 120,
              "amount": 49,
              "currency": "GBP"
            },
            {
              "status": "T",
              "startMinute": 120,
              "endMinute": 0,
              "amount": 0,
              "currency": "GBP"
            },
            {
              "status": "T",
              "startMinute": 0,
              "endMinute": -525600,
              "amount": 0,
              "currency": "GBP"
            }
          ]
        },
        {
          "changesType": 0,
          "changesStatus": "T",
          "changesFee": 0,
          "currency": "GBP",
          "revNoshow": "T",
          "revNoShowCondition": 0,
          "revNoshowFee": 0,
          "ruleDetailList": [
            {
              "status": "H",
              "startMinute": 525600,
              "endMinute": 86400,
              "amount": 30,
              "currency": "GBP"
            },
            {
              "status": "H",
              "startMinute": 86400,
              "endMinute": 120,
              "amount": 49,
              "currency": "GBP"
            },
            {
              "status": "T",
              "startMinute": 120,
              "endMinute": 0,
              "amount": 0,
              "currency": "GBP"
            },
            {
              "status": "T",
              "startMinute": 0,
              "endMinute": -525600,
              "amount": 0,
              "currency": "GBP"
            }
          ]
        }
      ],
      "serviceElements": [
        {
          "hasFreeSeat": 0,
          "hasFreeMeal": 0
        },
        {
          "hasFreeSeat": 0,
          "hasFreeMeal": 0
        }
      ]
    },
    "ancillaryProductElements": [
      {
        "ancillaryCode": "CBOL_1PC_15KG_MAXIMUM SIZE 56 X 45 X 25 CM",
        "auxBaggageElement": {
          "piece": 1,
          "weight": 15,
          "isAllWeight": true,
          "size": "Maximum Size 56 x 45 x 25 cm"
        },
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 0,
        "categoryCode": "CabinBaggageOverheadLocker",
        "clientTechnicalServiceFee": 0,
        "currency": "USD",
        "maxQty": 1,
        "minQty": 1,
        "price": 26.57,
        "productCode": "CBOL_1PC_15KG_MAXIMUM SIZE 56 X 45 X 25 CM",
        "segmentIndex": 1,
        "vendorPrice": 19.56,
        "vendorCurrency": "GBP"
      },
      {
        "segmentIndex": 1,
        "productCode": "SCI_BAG_1PC_15KG",
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 0,
        "price": 27.12,
        "currency": "USD",
        "vendorPrice": 19.97,
        "vendorCurrency": "GBP",
        "clientTechnicalServiceFee": 0,
        "auxBaggageElement": {
          "piece": 1,
          "weight": 15,
          "isAllWeight": true,
          "size": ""
        },
        "maxQty": 1,
        "minQty": 1,
        "categoryCode": "StandardCheckInBaggage",
        "ancillaryCode": "SCI_BAG_1PC_15KG"
      },
      {
        "segmentIndex": 1,
        "productCode": "SCI_BAG_2PC_30KG",
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 0,
        "price": 39.95,
        "currency": "USD",
        "vendorPrice": 29.42,
        "vendorCurrency": "GBP",
        "clientTechnicalServiceFee": 0,
        "auxBaggageElement": {
          "piece": 2,
          "weight": 30,
          "isAllWeight": true,
          "size": ""
        },
        "maxQty": 1,
        "minQty": 1,
        "categoryCode": "StandardCheckInBaggage",
        "ancillaryCode": "SCI_BAG_2PC_30KG"
      },
      {
        "segmentIndex": 2,
        "productCode": "CBOL_1PC_15KG_MAXIMUM SIZE 56 X 45 X 25 CM",
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 0,
        "price": 41.67,
        "currency": "USD",
        "vendorPrice": 30.69,
        "vendorCurrency": "GBP",
        "clientTechnicalServiceFee": 0,
        "auxBaggageElement": {
          "piece": 1,
          "weight": 15,
          "isAllWeight": true,
          "size": "Maximum Size 56 x 45 x 25 cm"
        },
        "maxQty": 1,
        "minQty": 1,
        "categoryCode": "CabinBaggageOverheadLocker",
        "ancillaryCode": "CBOL_1PC_15KG_MAXIMUM SIZE 56 X 45 X 25 CM"
      },
      {
        "segmentIndex": 2,
        "productCode": "SCI_BAG_1PC_15KG",
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 0,
        "price": 31.09,
        "currency": "USD",
        "vendorPrice": 22.9,
        "vendorCurrency": "GBP",
        "clientTechnicalServiceFee": 0,
        "auxBaggageElement": {
          "piece": 1,
          "weight": 15,
          "isAllWeight": true,
          "size": ""
        },
        "maxQty": 1,
        "minQty": 1,
        "categoryCode": "StandardCheckInBaggage",
        "ancillaryCode": "SCI_BAG_1PC_15KG"
      },
      {
        "segmentIndex": 2,
        "productCode": "SCI_BAG_2PC_30KG",
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 0,
        "price": 74.57,
        "currency": "USD",
        "vendorPrice": 54.91,
        "vendorCurrency": "GBP",
        "clientTechnicalServiceFee": 0,
        "auxBaggageElement": {
          "piece": 2,
          "weight": 30,
          "isAllWeight": true,
          "size": ""
        },
        "maxQty": 1,
        "minQty": 1,
        "categoryCode": "StandardCheckInBaggage",
        "ancillaryCode": "SCI_BAG_2PC_30KG"
      }
    ],
    "vendorFare": null,
    "links": [],
    "separateBookings": true,
    "refreshTime": null,
    "expireTime": null,
    "ancillarySupported": [
      "seat",
      "luggage"
    ],
    "cardChargeList": [
      {
        "cardType": "Visa",
        "percentage": 0.03,
        "charge": null,
        "currency": ""
      },
      {
        "cardType": "MasterCard",
        "percentage": 0.03,
        "charge": null,
        "currency": ""
      }
    ]
  },
  "airlineBookings": [
    {
      "airlineCode": "D8",
      "airlineName": "Norwegian Air Sweden",
      "airlinePnr": "S77182",
      "airlineWebSiteAddress": "https://www.norwegian.com",
      "mmbEmail": "jane.smith@example.com",
      "tailDigitsOfPaymentCard": null
    },
    {
      "airlineCode": "D8",
      "airlineName": "Norwegian Air Sweden",
      "airlinePnr": "X67745",
      "airlineWebSiteAddress": "https://www.norwegian.com",
      "mmbEmail": "jane.smith@example.com",
      "tailDigitsOfPaymentCard": null
    }
  ],
  "itineraryDownload": "http://121.40.236.223:8081/itineraryDownload.do?orderNo=FKEm34znpwya%2FiJBirhBW5YFgj2M7dX4",
  "contact": {
    "name": "Smith/Jane",
    "address": "189, Sky Garden Walk/London/US/US",
    "postcode": "EC3M 8AF",
    "email": "jane.smith@example.com",
    "mobile": "0001-982736245"
  },
  "errorCode": null,
  "errorMessage": null,
  "airlineMessage": null,
  "locale": "",
  "refundRules": [
    {
      "airline": "D8",
      "ruleType": "1",
      "passengerType": "",
      "penaltyAmount": null,
      "penaltyPercent": null,
      "penaltyPercentBase": null,
      "airlineFee": null,
      "taxRefundable": false,
      "fareRefundable": false,
      "refundableAncillaries": null,
      "startMinute": 525600,
      "endMinute": 0,
      "refundMethod": "CashBackToOriginalPayment"
    },
    {
      "airline": "D8",
      "ruleType": "1",
      "passengerType": "",
      "penaltyAmount": null,
      "penaltyPercent": null,
      "penaltyPercentBase": null,
      "airlineFee": null,
      "taxRefundable": false,
      "fareRefundable": false,
      "refundableAncillaries": null,
      "startMinute": 0,
      "endMinute": -525600,
      "refundMethod": "CashBackToOriginalPayment"
    },
    {
      "airline": "D8",
      "ruleType": "0",
      "passengerType": "",
      "penaltyAmount": "0",
      "penaltyPercent": 0,
      "penaltyPercentBase": null,
      "airlineFee": "0",
      "taxRefundable": true,
      "fareRefundable": true,
      "refundableAncillaries": [],
      "startMinute": 525600,
      "endMinute": 300,
      "refundMethod": "CashBackToOriginalPayment"
    },
    {
      "airline": "D8",
      "ruleType": "0",
      "passengerType": "",
      "penaltyAmount": "0",
      "penaltyPercent": 0,
      "penaltyPercentBase": null,
      "airlineFee": "0",
      "taxRefundable": true,
      "fareRefundable": true,
      "refundableAncillaries": [],
      "startMinute": 525600,
      "endMinute": -525600,
      "refundMethod": "CashBackToOriginalPayment"
    },
    {
      "airline": "D8",
      "ruleType": "0",
      "passengerType": "",
      "penaltyAmount": null,
      "penaltyPercent": null,
      "penaltyPercentBase": null,
      "airlineFee": null,
      "taxRefundable": false,
      "fareRefundable": false,
      "refundableAncillaries": null,
      "startMinute": 300,
      "endMinute": -300,
      "refundMethod": "CashBackToOriginalPayment"
    },
    {
      "airline": "D8",
      "ruleType": "0",
      "passengerType": "",
      "penaltyAmount": "0",
      "penaltyPercent": 0,
      "penaltyPercentBase": null,
      "airlineFee": "0",
      "taxRefundable": true,
      "fareRefundable": true,
      "refundableAncillaries": [],
      "startMinute": -300,
      "endMinute": -525600,
      "refundMethod": "CashBackToOriginalPayment"
    }
  ],
  "ifSeatOccupied": "SIMILAR_SEAT",
  "paymentOptions": null,
  "payment": {
    "paymentMethod": 5,
    "serviceFee": {
      "amount": 5,
      "currency": "USD",
      "deductFrom": "DEPOSIT"
    },
    "ticketFare": {
      "amount": 111.41,
      "currency": "EUR",
      "deductFrom": "CARD"
    },
    "paymentFee": {
      "amount": 4.8,
      "currency": "EUR",
      "deductFrom": "CARD"
    },
    "cardType": null
  },
  "paymentAttempted": null
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
|» status|[RetrieveBookingResponseStatus](#schemaretrievebookingresponsestatus)|true|none||- 800: Order not exists<br />- 701: Multi-order are identified, please request again with extra parameters added<br />- 702: airlinePNR and carrier are mandatory to fill in for order retrieval, please check and request again<br />- 703: No order found, please check the parameter<br />- 704: Parameters don't match, please check and retry<br />- 705: Timeout|
|» msg|[ResponseMessage](#schemaresponsemessage)¦null|false|none||It serves as an additional description of the response result. Especially when the interface reports an error (`status` !=`0`), it is usually a human-readable error message. Note: Do not use this field in any programming scenarios. For example, do not judge whether the interface responds successfully based on this field. Instead, you should only determine it by checking whether the status is equal to`0`at any time.|
|» orderNo|string|true|none||Order number|
|» pnrCode|string|true|none||The pnrCode is the single reference for the booking. This is the Atlas PNR.|
|» orderStatus|string|true|none||Order status<br />-`0`: Unpaid<br />-`1`: Ticketing-in-Process<br />-`2`: Ticketed<br />-`-3`: Cancelled|
|» ticketStatus|string|true|none||Ticket status<br />-`0`: Ticket not issued<br />-`1`: Ticket issued|
|» paxTicketInfos|[object]|true|none||Ticket information for passengers, the same format as the PAXTicketInfo in order response.|
|»» name|string|true|none||Echo the passenger's name, in the format of last name/first name|
|»» passengerType|[PassengerType](#schemapassengertype)|true|none||Echo the passenger's type.<br />- 0: Adult<br />- 1: Child<br />- 2: Infant|
|»» birthday|string|true|none||Echo the passenger's birthday|
|»» gender|string|true|none||Echo the passenger's gender|
|»» cardNum|string¦null|false|none||Echo the passenger's  identity document number|
|»» cardType|string¦null|false|none||Echo the passenger's  identity document type|
|»» cardIssuePlace|string¦null|false|none||Echo the country where the passenger's identification document was issued.|
|»» cardExpired|string¦null|false|none||Echo the expiration date of the passenger's identification document.|
|»» nationality|string¦null|false|none||Echo the passenger's nationality|
|»» ticketNos|[string]|true|none||If the ticket has been issued, the ticket number of the passenger will be included here. The number of elements corresponds to the number of airline ticket numbers. In cases where there are multiple airline PNRs, for example, when the round-trip tickets are issued **separately**, they respectively correspond to the ticket numbers of the outbound journey(the first element) and the return journey(the second element).<br /><br />**Note**: If and only if the round trip is split into two tickets, the array will contain 2 elements (corresponding to the tickets for the outbound trip and the return trip respectively); in all other cases, it will contain only one element.|
|»» airlinePNRs|[string]|true|none||The airline PNRs will be included here if they are generated. The number of elements corresponds to the number of airline's PNR. In cases where there are multiple airline PNRs, for example, when the round-trip tickets are issued separately, they respectively correspond to the PNRs of the outbound journey(the first element) and the return journey(the second element).<br /><br />**Note**: If and only if the round trip is split into two PNRs(or tickets), the array will contain 2 elements (corresponding to the PNRs for the outbound trip and the return trip respectively); in all other cases, it will contain only one element.|
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
|»» contactEmails|[string]¦null|false|none||The contact email used for the actual ticket issuance which may differ from the contact email provided by the customer when creating the order (when using an Atlas email). If and only if round trips are issued separately, the array will contain 2 elements, corresponding to the contact email for the outbound trip and the contact email for the return trip respectively.|
|»» contactPhones|[string]¦null|false|none||The contact phone used for the actual ticket issuance which may differ from the contact phone provided by the customer when creating the order (when using an Atlas email). If and only if round trips are issued separately, the array will contain 2 elements, corresponding to the contact phone for the outbound trip and the contact phone for the return trip respectively.|
|» totalPrice|number|true|none||Total price(not include the technical service fee) of this order in the currency TheAtlas settled with you.|
|» currency|string|true|none||The currency TheAtlas settled with you.|
|» tktLimitTime|string|true|none||Payment deadline for this order. This time will be displayed in SGT (GMT +8). The format is:`yyyy-MM-dd HH:mm:ss`|
|» vendorTotalPrice|number¦null|false|none||Total price of this order in the vendor's currency, reference for you to generate the specific credit card. If the order does not support VCC passthrough or BYOA, this fare will not be displayed.|
|» vendorCost|number¦null|false|none||The actual price charged by the airline, which is denominated in the airline's currency(`vendorCurrency`). We will only display the actual amount charged by the airline if the order supports VCC passthrough or BYOA, otherwise, this field will be`null`.|
|» vendorTotalAncillaryPrice|number¦null|false|none||Total ancillary price of this order in the vendor's currency. If the order does not support VCC passthrough or BYOA, this fare will not be displayed.|
|» vendorCurrency|string¦null|false|none||Vendor's currency.|
|» adultTotalFare|number|true|none||Total adult price of this order in the currency TheAtlas settled with you.|
|» childTotalFare|number|true|none||Total child price of this order in the currency TheAtlas settled with you.|
|» infantTotalFare|number¦null|false|none||Total infant price of this order in the currency TheAtlas settled with you.|
|» totalAncillaryPrice|number¦null|false|none||Total ancillary price of this order in the currency TheAtlas settled with you.|
|» totalTransactionFee|number|true|none||Total technical fees for this order in the currency TheAtlas settled with you.|
|» supportPaymentMethod|number|true|none||This tag shows which payment method is supported for that particular booking.<br />-`1`: Prepayment Only<br />-`3`: Both Credit Card Payment and Prepayment Available<br /><br />This field has been deprecated, pls use`supportPaymentMethods` instead.|
|» supportPaymentMethods|[[PaymentMethod](#schemapaymentmethod)]|true|none||The payment methods supported by the order.|
|» paymentMethod|[PaymentMethod](#schemapaymentmethod)¦null|false|none||This is the mode of payment used to pay for the booking. If the order is not paid, this field will be`null`.|
|» routing|[Routing](#schemarouting)|true|none||Route and fare details. The structure is the same format as "Routing" in search response.|
|»» routingIdentifier|string|true|none||This unique string identifier is used to verify requests for a particular route.<br />**Note:**<br />Has a certain validity period (generally not exceeding 6 hours).|
|»» supportCreditTransPayment|string|true|none||This tag is used to identify if the fare is support to be paid using the client's credit card(known as vcc passthrough). This field has been deprecated, please use `supportPaymentMethods` instead.|
|»» supportPaymentMethods|[[PaymentMethod](#schemapaymentmethod)]|true|none||Support payment methods for this fare. If payment is not supported in any way, this will be `null`or`[]`. Each item in this array is one of the following:<br />- 1: deposit<br />- 3: vcc passthrough<br />- 4: BYOA(Bring Your Own Account)<br />- 5: MoR|
|»» currency|string|true|none||The currency in which Atlas settles transactions with you.|
|»» adultPrice|number|true|none||Adult fare per passenger.|
|»» adultTax|number|true|none||Adult tax per passenger.|
|»» adultDetails|[[PriceItem](#schemapriceitem)]¦null|false|none||Details of the adult price composition.|
|»»» code|string|true|none||Machine readable code used to identify this price item.|
|»»» type|string|true|none||Type of this price item.|
|»»» amount|number|true|none||none|
|»»» description|string¦null|false|none||Human-readable description for this price item.|
|»» childPrice|number|true|none||Child fare per passenger.|
|»» childTax|number|true|none||Child tax per passenger.|
|»» childDetails|[[PriceItem](#schemapriceitem)]¦null|false|none||Details of the child price composition.|
|»»» code|string|true|none||Machine readable code used to identify this price item.|
|»»» type|string|true|none||Type of this price item.|
|»»» amount|number|true|none||none|
|»»» description|string¦null|false|none||Human-readable description for this price item.|
|»» infantPrice|number|true|none||Infant fare per passenger.|
|»» infantTax|integer|true|none||Infant tax per passenger.|
|»» infantDetails|[[PriceItem](#schemapriceitem)]¦null|false|none||Details of the child infant composition.|
|»»» code|string|true|none||Machine readable code used to identify this price item.|
|»»» type|string|true|none||Type of this price item.|
|»»» amount|number|true|none||none|
|»»» description|string¦null|false|none||Human-readable description for this price item.|
|»» infantAllowed|boolean¦null|false|none||Since `infantPrice` and `infantTax` will never be `null`, when the fare does not support infants or is free for infants, both `infantPrice` and `infantTax` display `0`. In this case, you need this field to distinguish which situation it is.<br />**Scenario description:**<br />- `true`: infants is supported by this fare, `infantPrice` and `infantTax` will >= `0`<br />- `false`: infants is not supported by this fare, `infantPrice` and `infantTax`will be displayed as `0`|
|»» childMandatorySeatingFee|number¦null|false|none||Only valid for FR integration.<br /><br />**FR Seat Selection Rules:**<br />- Children under 12 years old are provided with free seats.<br />- Children must be seated in the same row as an adult.<br />- Each adult may accompany up to 4 children.<br /><br />For fare families that do not include seat selection fees (e.g., Basic or Family Plus), FR offers discounted seat selection fees for adults traveling with children. The`childMandatorySeatingFee`field displays this discounted fee.<br />For fare families that already include seat selection fees, this field will be `null`.<br /><br />**Handling by Atlas for Fare Families Without Seat Selection Fees:**<br />- The number of children cannot exceed 4.<br />- Customers cannot select seats manually.<br />- Atlas will automatically assign seats randomly to one adult and all children according to FR's rules. The adult will be charged the `childMandatorySeatingFee` for their seat.<br /><br />**For Fare Families That Include Seat Selection Fees:**<br />- Seat selection is free.<br />- Users may call the seat map API to select seats; otherwise, Atlas will automatically assign seats.|
|»» transactionFeePerPax|number|true|none||Technical service fee per passenger. This field has been deprecated and final total transaction fee will calculated based on `transactionFee` and `transactionFeeMode`.|
|»» transactionFee|number|true|none||Technical service fee as per `transactionFeeMode`. The following lists the calculation methods for the final technical service fee in various situations.<br />- `transactionFeeMode`=`PER_SEGMENT`:`transactionFee` * number of passengers * number of segments.<br />- `transactionFeeMode`=`PER_TICKET`:`transactionFee` * number of passengers * number of orders on airline side.<br />- `transactionFeeMode`=`PER_PAX`:`transactionFee` * number of passengers.<br />- `transactionFeeMode`=`PER_BOOKING`:`transactionFee`.|
|»» transactionFeeMode|[TransactionFeeMode](#schematransactionfeemode)|true|none||Calculation method for technical service fee.<br />- PER_SEGMENT: Calculate based on the number of segments in the order (number of travel segments * number of passengers)<br />- PER_TICKET: Calculate based on the number of orders on the airline's side<br />- PER_PAX: Calculate based on the number of passengers<br />- PER_BOOKING: Calculate based on each order|
|»» fromSegments|[[RoutingSegment](#schemaroutingsegment)]|true|none||For outbound segments.|
|»»» aircraftCode|string¦null|false|none||IATA Code of aircraft type|
|»»» arrAirport|string|true|none||3-letter iata code for the arrival airport at which the segment is scheduled to arrive.|
|»»» arrTerminal|string¦null|false|none||The terminal at the destination airport where the segment is scheduled to arrive.|
|»»» arrTime|string|true|none||The datetime at which the segment is scheduled to arrive, in the arrival airport timezone. The format is `YYYYMMDD`.|
|»»» cabin|string¦null|false|none||RBD(known as Reservation Booking Designator) displayed by the airline.|
|»»» cabinClass|[CabinClass](#schemacabinclass)|true|none||Cabin class of the segment.<br />- 1: economy<br />- 2: business<br />- 3: first<br />- 4: premium economy|
|»»» carrier|string|true|none||IATA code of marketing carrier.|
|»»» codeShare|boolean|true|none||A flag used to identify whether it is a code share flight.|
|»»» depAirport|string|true|none||3-letter iata code for the airport at which the segment is scheduled to depart.|
|»»» depTerminal|string¦null|false|none||The terminal at the departure airport from which the segment is scheduled to depart.|
|»»» depTime|string|true|none||The datetime at which the segment is scheduled to depart, in the departure airport timezone. The format is`YYYYMMSS`.|
|»»» duration|integer|true|none||The duration of the segment in munites.|
|»»» fareFamily|string|true|none||Fare Family as per the information received from the airline|
|»»» flightNumber|string|true|none||Marketing flight number. The format is: CA123 or TR021 or FR1290, with the first two letters representing the carrier and the following number representing the flight number.|
|»»» operatingCarrier|string¦null|false|none||2-letter iata code for the operating carrier. The airline actually operating this segment. This may differ from the marketing carrier in the case of a "codeshare", where one airline sells flights operated by another airline.|
|»»» operatingFlightnumber|string¦null|false|none||Operating flight number.|
|»»» seatCount|integer|true|none||Max booking seats for the fare.|
|»»» segmentIndex|integer|true|none||Segment sequence. Starts from 1. If it is return trip, sequence for outbound trip and inbound trip would be together. The segment index also represents the flight sequence of the segment.|
|»»» stopCities|string¦null|false|none||IATA code/Name of cities from where the passengers will take stopover flights. Include IATA code of cities and use a comma in case of multiple cities to separate transfer airports count is higher than 1. For example: `CGK, SUB`. <br />`null` or blank means non-stop flight.|
|»» retSegments|[[RoutingSegment](#schemaroutingsegment)]¦null|false|none||For inbound segments. For one-way, this field will be `null` or `[]`.|
|»»» aircraftCode|string¦null|false|none||IATA Code of aircraft type|
|»»» arrAirport|string|true|none||3-letter iata code for the arrival airport at which the segment is scheduled to arrive.|
|»»» arrTerminal|string¦null|false|none||The terminal at the destination airport where the segment is scheduled to arrive.|
|»»» arrTime|string|true|none||The datetime at which the segment is scheduled to arrive, in the arrival airport timezone. The format is `YYYYMMDD`.|
|»»» cabin|string¦null|false|none||RBD(known as Reservation Booking Designator) displayed by the airline.|
|»»» cabinClass|[CabinClass](#schemacabinclass)|true|none||Cabin class of the segment.<br />- 1: economy<br />- 2: business<br />- 3: first<br />- 4: premium economy|
|»»» carrier|string|true|none||IATA code of marketing carrier.|
|»»» codeShare|boolean|true|none||A flag used to identify whether it is a code share flight.|
|»»» depAirport|string|true|none||3-letter iata code for the airport at which the segment is scheduled to depart.|
|»»» depTerminal|string¦null|false|none||The terminal at the departure airport from which the segment is scheduled to depart.|
|»»» depTime|string|true|none||The datetime at which the segment is scheduled to depart, in the departure airport timezone. The format is`YYYYMMSS`.|
|»»» duration|integer|true|none||The duration of the segment in munites.|
|»»» fareFamily|string|true|none||Fare Family as per the information received from the airline|
|»»» flightNumber|string|true|none||Marketing flight number. The format is: CA123 or TR021 or FR1290, with the first two letters representing the carrier and the following number representing the flight number.|
|»»» operatingCarrier|string¦null|false|none||2-letter iata code for the operating carrier. The airline actually operating this segment. This may differ from the marketing carrier in the case of a "codeshare", where one airline sells flights operated by another airline.|
|»»» operatingFlightnumber|string¦null|false|none||Operating flight number.|
|»»» seatCount|integer|true|none||Max booking seats for the fare.|
|»»» segmentIndex|integer|true|none||Segment sequence. Starts from 1. If it is return trip, sequence for outbound trip and inbound trip would be together. The segment index also represents the flight sequence of the segment.|
|»»» stopCities|string¦null|false|none||IATA code/Name of cities from where the passengers will take stopover flights. Include IATA code of cities and use a comma in case of multiple cities to separate transfer airports count is higher than 1. For example: `CGK, SUB`. <br />`null` or blank means non-stop flight.|
|»» rule|object|true|none||none|
|»»» hasBaggage|integer|true|none||This tag is used to identify if the fare includes free checked-in or cabin baggage.<br />- `0`: Not included<br />- `1`: Included|
|»»» baggageElements|[object]|true|none||The free baggage allowance|
|»»»» segmentNo|integer|true|none||The index of segment the baggage allowance applies to.|
|»»»» baggageType|[AncillaryCategory](#schemaancillarycategory)|true|none||Type of the baggage.|
|»»»» passengerType|[PassengerType](#schemapassengertype)|true|none||The type of passenger the baggage allowance applies to.<br />- 0: Adult<br />- 1: Child<br />- 2: Infant|
|»»»» baggagePiece|integer|true|none||Baggage pieces:<br />- `0`: No limitation<br />- `>0`: Maximum pieces|
|»»»» baggageWeight|integer|true|none||Baggage Weight, with the unit of KG.<br />- `0`: No Free baggage<br />- `-1`: No limitation on weight<br />- `>0`: Maximum weight|
|»»»» baggageSize|string|true|none||Baggage Size:<br />length＊width＊height and units. eg. `56＊36＊23cm`, `18＊14＊8inch`.<br />Or Total dimensions (length + width + height) of each piece. eg. `L+W+H<=158cm`.<br />Empty means no limitation.|
|»»»» isAllWeight|boolean¦null|false|none||Baggage is all weight: true or false|
|»»» refundRules|[object]|true|none||This node is used to fetch the refund rules of the fare. There is only one array element for one way, and two elements for round-trip. The first element is for the outbound, and the second element is for the inbound.|
|»»»» refundType|integer|true|none||Type of refund allowed.<br />- 0: Wholly unused ticket<br />- 1: Partially used ticket (For example, when the passenger has used an outbound flight and wants to refund an inbound flight.)|
|»»»» refundStatus|[RefundStatus](#schemarefundstatus)|false|none||Refund rule types (for the most restrictive condition).<br />- T: Non refundable<br />- H: Refundable with restrictions<br />- F: Full refundable|
|»»»» refundFee|integer¦null|false|none||Refund penalty amount (for the most restrictive condition)|
|»»»» currency|string¦null|false|none||The currency of refund penalty|
|»»»» refNoshow|string|true|none||Indicates if a no-show affects refunds (for the most restrictive condition).<br />- T: Non refundable<br />- H: Refundable with restrictions<br />- F: Free for refund|
|»»»» refNoShowCondition|integer|true|none||Time before scheduled flight departure|
|»»»» refNoshowFee|number|true|none||Total refund fee (for the most restrictive condition): If refNoshow = H, it should not be "null". This value includes the refund fee and no-show penalty|
|»»»» refundMethod|string¦null|false|none||Refund method: CashBackToOriginalPayment or Voucher.<br />- CashBackToOriginalPayment: Refund cash back to the original form of payment.<br />- Voucher: Refund in the form of a voucher.|
|»»»» ruleDetailList|[[AirlineRuleRes](#schemaairlineruleres)]|false|none||none|
|»»»»» status|[RefundStatus](#schemarefundstatus)|true|none||Level of refund/change.<br />- T: Non refundable<br />- H: Refundable with restrictions<br />- F: Full refundable|
|»»»»» startMinute|string|true|none||Starting time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|»»»»» endMinute|string|true|none||Ending time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|»»»»» amount|string¦null|false|none||Penalty amount for refund/change. If the`status`indicates free refund/change, then this field will be either`0`or`null`.|
|»»»»» currency|string¦null|false|none||The currency of penalty|
|»»»»» refundMethod|string¦null|false|none||Refund method: CashBackToOriginalPayment or Voucher.<br />- CashBackToOriginalPayment: Refund cash back to the original form of payment.<br />- Voucher: Refund in the form of a voucher.|
|»»» changesRules|[object]|true|none||This node is used to fetch the change rules of the fare. There is only one array element for one way, and two elements for round-trip. The first element is for the outbound, and the second element is for the inbound.|
|»»»» changesType|integer|true|none||Change flight type.<br />- `0`: Wholly unused ticket<br />- `1`: Partially used ticket (For example. When the passenger has used an outbound flight and wants to change an inbound flight)|
|»»»» changesStatus|[ChangeStatus](#schemachangestatus)|false|none||Change flight rule type (for the most restrictive condition):<br />- T: Non changeable<br />- H: Changeable with restrictions<br />- F: Free rescheduling|
|»»»» changesFee|number¦null|false|none||Change flight fee (for the most restrictive condition):<br />- If`changesStatus`=`H`, it should not be`null`<br />- If`changesStatus`=`T/F`, it can be`null`|
|»»»» currency|string¦null|false|none||The currency of change flight fee|
|»»»» revNoshow|string|true|none||Indicates if a no-show affects changes (for the most restrictive condition).<br />Valid values:<br />- T: Non changeable<br />- H: Changeable with restrictions<br />- F: Free flight change|
|»»»» revNoShowCondition|integer|true|none||Time before scheduled flight departure.|
|»»»» revNoshowFee|number|true|none||The total fee charged to change flight in case of no show. If revNoshow = H, it should not be "null." This value includes the change flight fee and no-show penalty.|
|»»»» ruleDetailList|[object]|false|none||Change conditions|
|»»»»» status|[RefundStatus](#schemarefundstatus)|true|none||Level of refund/change.<br />- T: Non refundable<br />- H: Refundable with restrictions<br />- F: Full refundable|
|»»»»» startMinute|string|true|none||Starting time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|»»»»» endMinute|string|true|none||Ending time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|»»»»» amount|string¦null|false|none||Penalty amount for refund/change. If the`status`indicates free refund/change, then this field will be either`0`or`null`.|
|»»»»» currency|string¦null|false|none||The currency of penalty|
|»»» serviceElements|[object]¦null|false|none||This function is used to fetch the other service rules of the fare. There is only one array for one way, and two arrays for round-trip. The first array is for the outbound, and the second array is for the inbound.|
|»»»» hasFreeSeat|integer|false|none||A marker used to indicate whether free seat selection is included.<br />- `0`: Not included<br />- `1`: Included<br />- `2`: Partially free|
|»»»» hasFreeMeal|integer|false|none||A marker used to indicate whether free meals are included.<br />- `0`: Not included<br />- `1`: Included|
|»» ancillaryProductElements|[[AncillaryProduct](#schemaancillaryproduct)]¦null|false|none||none|
|»»» ancillaryCode|string|true|none||A code that is relatively readable by humans and contains information about auxiliary business specifications (such as weight and quantity limitations of luggage). <br />**Note:** <br />This content is only for display purposes and should not be used for programming purposes. That is to say, do not attempt to parse the information about auxiliary business specifications from this code. If you want to access the auxiliary business specifications, please use structured fields. For example, for luggage, please use`auxBaggageElement`.|
|»»» auxBaggageElement|object¦null|false|none||Baggage specification limitations. This node is valid only when the ancillary type (`categoryCode`) is baggage.|
|»»»» isAllWeight|boolean|true|none||Mark whether the`weight`field restricts the total weight or the weight of a single piece.<br />- `true`: The weight is for all the pieces<br />- `false`: The weight is for each piece|
|»»»» piece|integer|true|none||The maximum number of pieces that can be purchased per person.<br />- `0`: No Limitation about piece<br />- `>0`: Maximum pieces|
|»»»» size|string¦null|false|none||Maximum size for the baggage|
|»»»» weight|integer|true|none||The maximum weight that can be purchased per person.<br />- `0`: No limitation for weight<br />- `>0`: Weight limit (KG)|
|»»» canPurchasePostTicket|integer|true|none||A flag used to mark if this ancillary product can be purchased in the post-ticketing flow.<br />- `0`: No<br />- `1`: Yes|
|»»» canPurchaseWithTicket|integer|true|none||A flag used to mark if this ancillary product can be purchased during the booking flow.<br />- `0`: No<br />- `1`: Yes|
|»»» categoryCode|[AncillaryCategory](#schemaancillarycategory)|true|none||Type of the ancillary.<br /><br />- StandardCheckInBaggage: Standard Check-in Baggage.<br />- CabinBaggage: Usually refers to the Cabin Baggage Overhead Locker. Transition value. It will gradually transition to `CabinBaggageOverheadLocker`.<br />- CabinBaggageOverheadLocker: Cabin Baggage Overhead Locker.<br />- CabinBaggageUnderSeat: Cabin Baggage Under Seat. Usually refers to the personal item.|
|»»» clientTechnicalServiceFee|number¦null|false|none||The service fee charged by Atlas for the purchase of the ancillary.|
|»»» currency|string|true|none||The currency in which Atlas settles transactions with you|
|»»» maxQty|integer|true|none||The maximum number of purchases allowed per person per flight segment|
|»»» minQty|integer|true|none||The minimum quantity allowed to be purchased per person per flight segment.|
|»»» price|number|true|none||Price for this ancillary.|
|»»» productCode|string|true|none||Unique identifier for the ancillary product. It would be used in the order request.|
|»»» segmentIndex|integer|true|none||The index of segment the ancillary applies to.|
|»»» vendorCurrency|string|true|none||The currency in which the vendor charges for the ancillary. If the fare does not allow for the VCC pass-through or BYOA payment, this information will be`null`.|
|»»» vendorPrice|integer|true|none||The price charged by the vendor for the ancillary. If the fare does not allow for the VCC pass-through or BYOA payment, this information will be`null`.|
|»» vendorFare|object|true|none||To identify the vendor’s fare with vendor’s currency. It is only available when`supportPaymentMethods`contains`3`or`4`.|
|»»» vendorAdultPrice|number|true|none||Adult fare per passenger in vendor’s currency|
|»»» vendorAdultTax|number|true|none||Adult tax per passenger in vendor’s currency|
|»»» vendorChildPrice|number|true|none||Child fare per passenger in vendor’s currency|
|»»» vendorChildTax|number|true|none||Child tax per passenger in vendor’s currency|
|»»» vendorInfantPrice|number|true|none||Infant fare per passenger in vendor’s currency|
|»»» vendorInfantTax|integer|true|none||Infant tax per passenger in vendor’s currency|
|»»» vendorCurrency|string|true|none||Vendor’s currency|
|»» links|[TAndCLink](#schematandclink)|true|none||The terms and conditions links of the airlines. Will only return in verify response.|
|»»» carrier|string|true|none||IATA code for the airline|
|»»» kind|string|true|none||always:`terms`|
|»»» link|string|true|none||URL to the carrier's terms and conditions|
|»»» description|string|true|none||Carrier terms and conditions|
|»» separateBookings|boolean|true|none||When the outbound and inbound of round trip need to be booked separately, it will be true.|
|»» refreshTime|string|true|none||If the fare is from the cache of Atlas, this field is used to indicate the refresh time of the cache. The time is a certain moment in the past (UTC), and the format is:`yyyy-MM-dd'T'HH:mm:ss'Z'`.|
|»» expireTime|string|true|none||If the current fare comes from the cache of Atlas, this field is used to indicate the estimated expiration time of the cache. This time is a certain moment in the future (UTC), and the format is:`yyyy-MM-dd'T'HH:mm:ss'Z'`.<br />**Note:** <br />This time is estimated, which means Atlas may refresh the cache before or after that time.|
|»» ancillarySupported|[string]|true|none||A list of ancillary service types that the fare allows for additional purchase. Possible value contains:<br />- `luggage`<br />- `seat`: You can carry out the subsequent seat selection process through our seat map interface.|
|»» cardChargeList|[[CardCharge](#schemacardcharge)]¦null|false|none||Payment handling fee for MoR/VCC|
|»»» cardType|[CardType](#schemacardtype)|true|none||Card types, such as Visa, MasterCard|
|»»» percentage|number¦null|false|none||Percentage of payment handling fee|
|»»» charge|number¦null|false|none||The amount of payment handling fee|
|»»» currency|string¦null|false|none||Currency of `charge`|
|» airlineBookings|[object]|true|none||Airline booking information. If the round-trip tickets are issued separately, the array will contain 2 elements, corresponding to the relevant information of the outgoing and return trips respectively.|
|»» airlineCode|string|true|none||2 character IATA airline code.|
|»» airlineName|string¦null|false|none||Name of the airline.|
|»» airlinePnr|string¦null|false|none||The record locator of the airline. If the airline PNR has not been generated, `null`will be displayed.|
|»» airlineWebSiteAddress|string¦null|false|none||The URL of the public airline website.|
|»» mmbEmail|string|true|none||The email id to be used in the airline's MMB (Manage my Booking) section.|
|»» tailDigitsOfPaymentCard|string¦null|false|none||The last four digits of the VCC card number paid by the airline.|
|» itineraryDownload|string|true|none||The link to download the itinerary of the trip.|
|» contact|object|true|none||Contact information of the order|
|»» name|string|true|none||Contact name, please follow this format: Family Name/Given Name. The contact name can only accept Latin letters, /, and spaces.|
|»» address|string¦null|false|none||Contact address.|
|»» postcode|string¦null|false|none||Contact post code.|
|»» email|string¦null|false|none||Contact email.|
|»» mobile|string¦null|false|none||Contact mobile, please follow this format : XXXX(digital country code)-XXXXXXXX(phone number), here're the examples: 0001-87291810, 0086-13928109091, 0971-19201998|
|» errorCode|[TicketErrorCodes](#schematicketerrorcodes)|true|none||An error code used to indicate the specific reason for ticket issuance failure. Note that this error code will only be displayed when the order is canceled due to ticket issuance failure.|
|» errorMessage|string|false|none||A brief message used to explain the`errorCode`.|
|» airlineMessage|string|false|none||A piece of error message on the airline side that is used to explain the`errorCode`.|
|» refundRules|[[RefundRule](#schemarefundrule)]¦null|false|none||Refund rules for the tickets|
|»» airline|string|true|none||IATA code of the airline|
|»» ruleType|[RefundRuleType](#schemarefundruletype)|true|none||Type of refund rule|
|»» passengerType|string¦null|false|none||The passenger types(separated by`/`) to which the rule applies, .`null`means that it is applicable to all passenger types.<br />-`ADT`<br />-`CHD`<br />-`INF`|
|»» penaltyAmount|number|false|none||The absolute amount of the penalty|
|»» penaltyPercent|number|false|none||The percentage of the penalty|
|»» penaltyPercentBase|string|false|none||The percentage base of the penalty|
|»» airlineFee|number|false|none||Airline ticket refund fee|
|»» taxRefundable|boolean|true|none||Whether tax can be refunded|
|»» fareRefundable|boolean|true|none||Whether fare can be refunded|
|»» refundableAncillaries|[string]¦null|false|none||Ancillary service types that can be refunded together with the ticket.|
|»» startMinute|integer|true|none||Starting time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|»» endMinute|integer|true|none||Ending time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|»» refundMethod|[RefundMethod](#schemarefundmethod)¦null|false|none||The method of fund refund|
|» ifSeatOccupied|[IfSeatOccupied](#schemaifseatoccupied)¦null|false|none||Configuration of ordering when the seat is occupied.|
|» paymentOptions|[[PaymentOption](#schemapaymentoption)]¦null|false|none||Available payment options for this order. If the order is paid, then it will be`null`.|
|»» paymentMethod|[PaymentMethod](#schemapaymentmethod)|true|none||Payment method.<br />- 1: balance<br />- 3: vcc passthrough<br />- 4: BYOA<br />- 5: MoR|
|»» ticketFare|[PaymentOptionDetail](#schemapaymentoptiondetail)|true|none||It is used to describe the total ticket price and how the deduction will be made.|
|»»» amount|number|true|none||Total amount will be deducted.|
|»»» currency|string|true|none||Currency of the`amount`|
|»»» deductFrom|string|true|none||Deduction method|
|»» serviceFee|[PaymentOptionDetail](#schemapaymentoptiondetail)¦null|false|none||It is used to describe the total service and how the deduction will be made.|
|»»» amount|number|true|none||Total amount will be deducted.|
|»»» currency|string|true|none||Currency of the`amount`|
|»»» deductFrom|string|true|none||Deduction method|
|»» paymentFee|[PaymentOptionDetail](#schemapaymentoptiondetail)¦null|false|none||It is used to describe the payment fee and how the deduction will be made.|
|»»» amount|number|true|none||Total amount will be deducted.|
|»»» currency|string|true|none||Currency of the`amount`|
|»»» deductFrom|string|true|none||Deduction method|
|»» cardType|string¦null|false|none||Only for MoR. Echo the card type you sent in order request.|
|» payment|[PaymentOption](#schemapaymentoption)¦null|false|none||The information about the actual payment method used for the order and the deduction method. Only will be displayed when order is paid.|
|»» paymentMethod|[PaymentMethod](#schemapaymentmethod)|true|none||Payment method.<br />- 1: balance<br />- 3: vcc passthrough<br />- 4: BYOA<br />- 5: MoR|
|»» ticketFare|[PaymentOptionDetail](#schemapaymentoptiondetail)|true|none||It is used to describe the total ticket price and how the deduction will be made.|
|»» serviceFee|[PaymentOptionDetail](#schemapaymentoptiondetail)¦null|false|none||It is used to describe the total service and how the deduction will be made.|
|»» paymentFee|[PaymentOptionDetail](#schemapaymentoptiondetail)¦null|false|none||It is used to describe the payment fee and how the deduction will be made.|
|»» cardType|string¦null|false|none||Only for MoR. Echo the card type you sent in order request.|
|» paymentAttempted|boolean¦null|false|none||Only used for VCC transparent transmission, indicating whether Atlas has initiated payment operations with the airline using your VCC. true/false/null (meaningless).<br />-`true`: Atlas has previously initiated a payment operation with the airline.<br />-`false`: Atlas has not initiated a payment operation with the airline.<br />-`null`: meaningless<br />**Note:**<br />`true` only indicates that Atlas has previously initiated a payment operation with the airline, and does not represent the payment result (successful or failed)|

#### 枚举值

|属性|值|
|---|---|
|status|800|
|status|701|
|status|702|
|status|703|
|status|704|
|status|705|
|passengerType|0|
|passengerType|1|
|passengerType|2|
|paymentMethod|1|
|paymentMethod|3|
|paymentMethod|4|
|paymentMethod|5|
|supportCreditTransPayment|0|
|supportCreditTransPayment|1|
|type|base|
|type|tax|
|type|fee|
|type|base|
|type|tax|
|type|fee|
|type|base|
|type|tax|
|type|fee|
|transactionFeeMode|PER_SEGMENT|
|transactionFeeMode|PER_TICKET|
|transactionFeeMode|PER_PAX|
|transactionFeeMode|PER_BOOKING|
|cabinClass|1|
|cabinClass|2|
|cabinClass|3|
|cabinClass|4|
|cabinClass|1|
|cabinClass|2|
|cabinClass|3|
|cabinClass|4|
|baggageType|StandardCheckInBaggage|
|baggageType|CabinBaggage|
|baggageType|CabinBaggageUnderSeat|
|baggageType|CabinBaggageOverheadLocker|
|passengerType|0|
|passengerType|1|
|passengerType|2|
|refundStatus|T|
|refundStatus|H|
|refundStatus|F|
|refundMethod|CashBackToOriginalPayment|
|refundMethod|Voucher|
|status|T|
|status|H|
|status|F|
|refundMethod|CashBackToOriginalPayment|
|refundMethod|Voucher|
|changesStatus|T|
|changesStatus|H|
|changesStatus|F|
|status|T|
|status|H|
|status|F|
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
|errorCode|601|
|errorCode|602|
|errorCode|603|
|errorCode|604|
|errorCode|605|
|errorCode|6051|
|errorCode|606|
|errorCode|607|
|errorCode|608|
|errorCode|609|
|errorCode|611|
|errorCode|613|
|errorCode|614|
|errorCode|615|
|errorCode|616|
|errorCode|617|
|errorCode|618|
|errorCode|619|
|errorCode|620|
|errorCode|621|
|errorCode|623|
|errorCode|624|
|errorCode|625|
|errorCode|626|
|errorCode|627|
|errorCode|628|
|errorCode|629|
|errorCode|630|
|errorCode|631|
|errorCode|632|
|errorCode|633|
|errorCode|634|
|errorCode|698|
|errorCode|699|
|ruleType|0|
|ruleType|1|
|ruleType|2|
|penaltyPercentBase|fare+tax|
|penaltyPercentBase|fare|
|refundMethod|CashBackToOriginalPayment|
|refundMethod|Voucher|
|ifSeatOccupied|SIMILAR_SEAT|
|ifSeatOccupied|STOP_SEAT|
|ifSeatOccupied|STOP_TICKET|
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

## POST Smart Search(Only For TMC)

POST /smartSearch.do

**Advantages of Smart Search:**

* Supports real-time search for booking windows and routes not covered in "Search API".
* Enhances search result rate and overall coverage.

**Points to note:**

* Smart Search will be activated "on demand". Please contact your account manager or sales director if you want this feature to be activated.
* The ist response will return the results from the cache. if the "smartEnd"=false, send the subsequent requests until if the "smartEnd"=true to get all the results from the LIVE search.
* <span style="color:rgb(255, 140, 0)">**Use production endpoint being used for APls other than search APl.**</span>

**Workflow:**

* Send the "Smart Search" request(called **First Request**) and receive the response, which includes an ID (`requestId`) used to identify the entire search process, and may also contain part of the flight data(`routings`).
* After receiving the response, if the`smartEnd`=`false`, then send another request (called **Subsequent Request**) only with the`requestId`.
* Follow this flow until`smartEnd`=`true`. This means that the smart search has been completed. 

**Endpoint:**
https://sandbox.atriptech.com/smartSearch.do

> Body 请求参数

```json
{
  "adultNum": 2,
  "childNum": 0,
  "currency": "GBP",
  "fromCity": "ACE",
  "fromDate": "20250920",
  "includeMultipleFareFamily": false,
  "infantNum": 0,
  "maxResponseTime": 15000,
  "requestSource": "Dynamic",
  "sync": true,
  "toCity": "LON",
  "tripType": "1"
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
|» requestId|body|string| 是 |Only required in **Subsequent Request**|
|» tripType|body|string| 是 |The trip type(1=one way or 2=round trip) you want to search|
|» adultNum|body|integer| 是 |Adult passenger count. Please note that the total number of adults(`adultNum`) and children(`childNum`) cannot exceed 9.|
|» childNum|body|integer| 是 |Child passenger count. Please note that the total number of adults(`adultNum`) and children(`childNum`) cannot exceed 9|
|» infantNum|body|integer| 是 |Infant passenger count, no more than the number of adult|
|» fromCity|body|string| 是 |IATA code of the departure city or airport (in capital letters).When the airport code you sent is different from the code of the city where the airport is located, we can recognize that it is an airport, otherwise we will treat it as a city code. We will filter flights based on your departure location type.|
|» toCity|body|string| 是 |IATA code of the arrival city or airport (in capital letters).When the airport code you sent is different from the code of the city where the airport is located, we can recognize that it is an airport, otherwise we will treat it as a city code. We will filter flights based on your departure location type.|
|» fromAirport|body|string¦null| 否 |IATA code of the departure airport|
|» toAirport|body|string¦null| 否 |IATA code of the arrival airport|
|» fromDate|body|string(date)| 是 |Departure date, the format is `YYYYMMDD`|
|» retDate|body|string(date)¦null| 否 |Return date, the format is `YYYYMMDD`. If you are searching for round-trip, the return date is mandatory.|
|» airlines|body|[string]¦null| 否 |An array of IATA Codes(in capital letters) of airlines. The result will only contain the airlines specified in the search request.|
|» fromFlightNumbers|body|[string]¦null| 否 |Search for specified departure flights. Each element represents one flight. Connecting flight numbers are separated by "`,`" (comma). |
|» retFlightNumbers|body|[string]¦null| 否 |Search for specified return flights. Each element represents one flight. Connecting flight numbers are separated by "`,`" (comma).|
|» includeMultipleFareFamily|body|boolean¦null| 否 |Search only for the lowest fare or for the Fare Families. By default, each flight only returns the lowest fare, and each array element in the response represents: flight - lowest fare. If this parameter is turned on, each element of the search results will be a combination of flight and one of the fares, that is, different elements will have the same flight but different ticket fare.|
|» currency|body|string¦null| 否 |This is the settlement currency. The 3-letter currency code should be entered. This field is optional, and when you want to settle with Atlas in different currencies (especially when you have opened multiple deposit accounts in different currencies in Atlas), you need to use this parameter.|
|» displayCurrency|body|string¦null| 否 |The currency for the display fares in response. If no display currency is specified, the display amount will be null.|
|» requestSource|body|string¦null| 否 |Identify the source of the search traffic, E.g. Google Flights, Oganic Search, SkyScanner.|
|» sync|body|boolean| 否 |Is smart search synchronized return, default is asynchronous|
|» residentCode|body|string¦null| 否 |Resident discount code|

#### 详细说明

**» fromFlightNumbers**: Search for specified departure flights. Each element represents one flight. Connecting flight numbers are separated by "`,`" (comma). 
**Example**:
- ["FR123"]: A direct flight
- ["FR456,FR789"]: A connecting flight
- ["FR123", "FR456,FR789"]: 2 flights, a direct flight and a connecting flight

#### 枚举值

|属性|值|
|---|---|
|» tripType|1|
|» tripType|2|

> 返回示例

> 200 Response

```json
{
  "status": 0,
  "requestId": "17553346623104JGpo",
  "smartEnd": true,
  "routings": [
    {
      "adultDetails": [
        {
          "amount": 12.09,
          "code": "farePrice",
          "description": "",
          "type": "base"
        },
        {
          "amount": 76.07,
          "code": "tax",
          "description": "",
          "type": "tax"
        }
      ],
      "adultPrice": 12.09,
      "adultTax": 76.07,
      "ancillaryProductElements": [
        {
          "ancillaryCode": "SCI_BAG_3PC_66KG",
          "auxBaggageElement": {
            "allWeight": true,
            "piece": 3,
            "size": "",
            "weight": 66
          },
          "canPurchasePostTicket": 0,
          "canPurchaseWithTicket": 1,
          "categoryCode": "StandardCheckInBaggage",
          "clientTechnicalServiceFee": 0,
          "currency": "GBP",
          "maxQty": 1,
          "minQty": 1,
          "price": 134.56,
          "productCode": "SCI_BAG_3PC_66KG",
          "segmentIndex": 1,
          "vendorCurrency": "GBP",
          "vendorPrice": 133.57
        },
        {
          "ancillaryCode": "SCI_BAG_1PC_22KG",
          "auxBaggageElement": {
            "allWeight": true,
            "piece": 1,
            "size": "",
            "weight": 22
          },
          "canPurchasePostTicket": 0,
          "canPurchaseWithTicket": 1,
          "categoryCode": "StandardCheckInBaggage",
          "clientTechnicalServiceFee": 0,
          "currency": "GBP",
          "maxQty": 1,
          "minQty": 1,
          "price": 44.86,
          "productCode": "SCI_BAG_1PC_22KG",
          "segmentIndex": 1,
          "vendorCurrency": "GBP",
          "vendorPrice": 44.53
        },
        {
          "ancillaryCode": "SCI_BAG_2PC_44KG",
          "auxBaggageElement": {
            "allWeight": true,
            "piece": 2,
            "size": "",
            "weight": 44
          },
          "canPurchasePostTicket": 0,
          "canPurchaseWithTicket": 1,
          "categoryCode": "StandardCheckInBaggage",
          "clientTechnicalServiceFee": 0,
          "currency": "GBP",
          "maxQty": 1,
          "minQty": 1,
          "price": 89.71,
          "productCode": "SCI_BAG_2PC_44KG",
          "segmentIndex": 1,
          "vendorCurrency": "GBP",
          "vendorPrice": 89.05
        }
      ],
      "ancillarySupported": [
        "seat",
        "luggage"
      ],
      "bundleOptions": [],
      "childDetails": [
        {
          "amount": 12.09,
          "code": "farePrice",
          "description": "",
          "type": "base"
        },
        {
          "amount": 76.07,
          "code": "tax",
          "description": "",
          "type": "tax"
        }
      ],
      "childPrice": 12.09,
      "childTax": 76.07,
      "combineIndexs": [],
      "currency": "GBP",
      "expireTime": "2025-08-16T12:19:38Z",
      "fid": "z8NUOiqt5NX05yUOdg0-RfZls9ockAhaJJ6w56FfZVEKQtULkxLefdhdb239v6gV",
      "fromSegments": [
        {
          "aircraftCode": "",
          "arrAirport": "STN",
          "arrTerminal": "",
          "arrTime": "202509210155",
          "cabin": "",
          "cabinClass": 1,
          "carrier": "LS",
          "codeShare": false,
          "depAirport": "ACE",
          "depTerminal": "",
          "depTime": "202509202150",
          "duration": 245,
          "fareFamily": "low",
          "flightNumber": "LS1422",
          "operatingCarrier": "",
          "operatingFlightnumber": "",
          "seatCount": 2,
          "segmentIndex": 1,
          "stopCities": ""
        }
      ],
      "infantAllowed": true,
      "infantDetails": [
        {
          "amount": 25.19,
          "code": "farePrice",
          "description": "",
          "type": "base"
        },
        {
          "amount": 0,
          "code": "tax",
          "description": "",
          "type": "tax"
        }
      ],
      "infantPrice": 25.19,
      "infantTax": 0,
      "nationality": "",
      "nationalityType": 0,
      "paxType": "ADT",
      "refreshTime": "2025-08-16T03:30:38Z",
      "retSegments": [],
      "riskSellout": false,
      "routingIdentifier": "QUNFX0xPTl8xXzIwMjUwOTIwX18yXzBfMHxYSEc3MjczMV9hcGlfMXwxfDg4LjE2Xzg4LjE2XzI1LjE5XzAuNjVfMjAyLjE2X0dCUHxBQ0VfTE9OXzFfMjAyNTA5MjBfXzJfMF8wXkFDRS1MUzE0MjItLVNUTi0yMDI1MDkyMDIxNTAtMjAyNTA5MjEwMTU1LWxvdy0xLV44OC4xNl84OC4xNl8yNS4xOV8wLjY1XzIwMi4xNl5BTFNBUElfQUxTXl5BTFMxQUNFTE9OMjAwMjAyNTA5MjBeR0JQXjg3LjUwXjg3LjUwXjI1LjAwXjF8MXwyMDI1MDgxNjE2NTc1NnwwfDE3NTUzMzQ2NjIzMTA0Skdwb3x8fHx8MS4zMHw0fDB8R0JQfG5vcm1hbHxmYWxzZQ==.Q86tmtSTKhG8cbOGw3SsCJVxdMAfHLwnafWbeP2Sjw4=",
      "rule": {
        "baggageElements": [
          {
            "baggagePiece": 0,
            "baggageSize": "",
            "baggageType": "StandardCheckInBaggage",
            "baggageWeight": 0,
            "passengerType": 0,
            "segmentNo": 1
          },
          {
            "baggagePiece": 0,
            "baggageSize": "",
            "baggageType": "StandardCheckInBaggage",
            "baggageWeight": 0,
            "passengerType": 1,
            "segmentNo": 1
          },
          {
            "baggagePiece": 0,
            "baggageSize": "",
            "baggageType": "StandardCheckInBaggage",
            "baggageWeight": 0,
            "passengerType": 2,
            "segmentNo": 1
          },
          {
            "baggagePiece": 1,
            "baggageSize": "56*45*25cm",
            "baggageType": "CabinBaggageOverheadLocker",
            "baggageWeight": 10,
            "passengerType": 0,
            "segmentNo": 1
          },
          {
            "baggagePiece": 1,
            "baggageSize": "56*45*25cm",
            "baggageType": "CabinBaggageOverheadLocker",
            "baggageWeight": 10,
            "passengerType": 1,
            "segmentNo": 1
          },
          {
            "baggagePiece": 0,
            "baggageSize": "56*45*25cm",
            "baggageType": "CabinBaggageOverheadLocker",
            "baggageWeight": 0,
            "passengerType": 2,
            "segmentNo": 1
          }
        ],
        "changesRules": [
          {
            "changesFee": 0,
            "changesStatus": "T",
            "changesType": 0,
            "currency": "GBP",
            "revNoShowCondition": 0,
            "revNoshow": "T",
            "revNoshowFee": 0,
            "ruleDetailList": [
              {
                "amount": 75.5,
                "currency": "GBP",
                "endMinute": 300,
                "ruleId": 38876,
                "startMinute": 525600,
                "status": "H"
              },
              {
                "amount": 0,
                "currency": "GBP",
                "endMinute": 0,
                "ruleId": 38877,
                "startMinute": 300,
                "status": "T"
              },
              {
                "amount": 0,
                "currency": "GBP",
                "endMinute": -525600,
                "ruleId": 38878,
                "startMinute": 0,
                "status": "T"
              }
            ]
          }
        ],
        "hasBaggage": 1,
        "refundRules": [
          {
            "currency": "GBP",
            "refNoShowCondition": 0,
            "refNoshow": "T",
            "refNoshowFee": 0,
            "refundFee": 0,
            "refundMethod": "CASH_BACK_TO_ORIGINAL_PAYMENT",
            "refundStatus": "T",
            "refundType": 0,
            "ruleDetailList": [
              {
                "amount": 0,
                "currency": "GBP",
                "endMinute": 0,
                "refundMethod": "CashBackToOriginalPayment",
                "ruleId": 31451,
                "startMinute": 525600,
                "status": "T"
              },
              {
                "amount": 0,
                "currency": "GBP",
                "endMinute": -525600,
                "refundMethod": "CashBackToOriginalPayment",
                "ruleId": 31452,
                "startMinute": 0,
                "status": "T"
              }
            ]
          }
        ],
        "serviceElements": [
          {
            "hasFreeMeal": 0,
            "hasFreeSeat": 0
          }
        ]
      },
      "separateBookings": false,
      "suitAge": "",
      "supportCreditTransPayment": "1",
      "supportPaymentMethods": [
        1,
        3
      ],
      "transactionFee": 1.3,
      "transactionFeeMode": "PER_BOOKING",
      "transactionFeePerPax": 0.65,
      "vendorFare": {
        "vendorAdultPrice": 12,
        "vendorAdultTax": 75.5,
        "vendorChildPrice": 12,
        "vendorChildTax": 75.5,
        "vendorCurrency": "GBP",
        "vendorInfantPrice": 25,
        "vendorInfantTax": 0
      }
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
|» status|[SearchResponseStatus](#schemasearchresponsestatus)|true|none||- 100: Missing required request data. Description: You should pass the necessary parameters in the HTTP request body.<br />- 101: Illegal request data. Description: Check the format of request<br />- 102: Illegal request param. Description: Some parameters do not meet the requirements. Please adjust them according to the error message.<br />- 105: OD is not in client's round-trip white list. Description: This city pair has not been whitelisted. Check with your account manager if there is a restriction to your account.<br />- 106: You are not allowed to search. Description: Check with your account manager if there is a restriction to your account.<br />- 107: Insufficient balance. Description: The account balance is below the agreed threshold. Top-up your account on a priority.<br />- 108: Route is restricted / System limitations. Description: The airline has flights and quotations, but Atlas has closed sales for some reasons. The reasons can be 1) The sales were manually closed 2) The system has detected a risk of sold out 3) Prohibitions on nearby flights.<br />- 109: The number of searches exceeded the limit. Description: The searches per day have exceeded the allowed limit. Check with your account manager if there is a restriction to your account.<br />- 110: Too many concurrent requests.. Description: The QPS (Queries Per Second) is higher than the allowed limit. If your business requires more resources, please contact your account manager.<br />- 111: Real time search is not allowed. Description: This feature is not activated for your account. Connect with your account manager if you require this service.<br />- 112: Timed out. Description: The search request has timed-out. For further details please refer to FAQs --> Atlas API General Information.<br />- 113: Airline is under maintenance. Description: Airline is in "Inactive" or "Maintenance" status with Atlas. This does not necessarily mean that there is an issue with the Airline website itself. Wait for the status to change to “active”.<br />- 114: No flights present. Description: This may happen when: - The airline does not fly on that date for the searched city pair. Check the airline website to see if the flight is operational for that date.<br />- 116: Search data not captured. Description: An error was reported during the search data stoprage at Atlas' end. If this error is not constantly reported, you can try trying again. If the error persists, then it is necessary to contact the account manager.<br />- 123: Too many requests but too few paid orders. Description: The service has been blocked as the search requests are too many and the paid orders are very less.<br />- 124: Unsupported settlement currency. Description: The settlement currency is different than what is accepted by Atlas. Change the currency to the currency accepted by Atlas for settlement.<br />- 126: `requestId` does not exist or request is already ended. Description: <br />- 900: Unauthorized access. Description: Incorrect credentials Or the account status is incorrect Or try to access other customer's data. Check credentials. If the error still persists, contact your account manager.<br />- 9999: Inner error. Description: There is a problem or a bug in the system. Contact your account manager.|
|» msg|[ResponseMessage](#schemaresponsemessage)¦null|false|none||It serves as an additional description of the response result. Especially when the interface reports an error (`status` !=`0`), it is usually a human-readable error message. Note: Do not use this field in any programming scenarios. For example, do not judge whether the interface responds successfully based on this field. Instead, you should only determine it by checking whether the status is equal to`0`at any time.|
|» requestId|string|true|none||Unique identifier for the search process.|
|» smartEnd|boolean|true|none||Informing whether the request has been completed.<br />-`true`: Indicates that the search has ended<br />-`false`: Indicates that the search is still in progress|
|» routings|[[Routing](#schemarouting)]¦null|false|none||The array of the routings include suitable flights and fares.|
|»» routingIdentifier|string|true|none||This unique string identifier is used to verify requests for a particular route.<br />**Note:**<br />Has a certain validity period (generally not exceeding 6 hours).|
|»» supportCreditTransPayment|string|true|none||This tag is used to identify if the fare is support to be paid using the client's credit card(known as vcc passthrough). This field has been deprecated, please use `supportPaymentMethods` instead.|
|»» supportPaymentMethods|[[PaymentMethod](#schemapaymentmethod)]|true|none||Support payment methods for this fare. If payment is not supported in any way, this will be `null`or`[]`. Each item in this array is one of the following:<br />- 1: deposit<br />- 3: vcc passthrough<br />- 4: BYOA(Bring Your Own Account)<br />- 5: MoR|
|»» currency|string|true|none||The currency in which Atlas settles transactions with you.|
|»» adultPrice|number|true|none||Adult fare per passenger.|
|»» adultTax|number|true|none||Adult tax per passenger.|
|»» adultDetails|[[PriceItem](#schemapriceitem)]¦null|false|none||Details of the adult price composition.|
|»»» code|string|true|none||Machine readable code used to identify this price item.|
|»»» type|string|true|none||Type of this price item.|
|»»» amount|number|true|none||none|
|»»» description|string¦null|false|none||Human-readable description for this price item.|
|»» childPrice|number|true|none||Child fare per passenger.|
|»» childTax|number|true|none||Child tax per passenger.|
|»» childDetails|[[PriceItem](#schemapriceitem)]¦null|false|none||Details of the child price composition.|
|»»» code|string|true|none||Machine readable code used to identify this price item.|
|»»» type|string|true|none||Type of this price item.|
|»»» amount|number|true|none||none|
|»»» description|string¦null|false|none||Human-readable description for this price item.|
|»» infantPrice|number|true|none||Infant fare per passenger.|
|»» infantTax|integer|true|none||Infant tax per passenger.|
|»» infantDetails|[[PriceItem](#schemapriceitem)]¦null|false|none||Details of the child infant composition.|
|»»» code|string|true|none||Machine readable code used to identify this price item.|
|»»» type|string|true|none||Type of this price item.|
|»»» amount|number|true|none||none|
|»»» description|string¦null|false|none||Human-readable description for this price item.|
|»» infantAllowed|boolean¦null|false|none||Since `infantPrice` and `infantTax` will never be `null`, when the fare does not support infants or is free for infants, both `infantPrice` and `infantTax` display `0`. In this case, you need this field to distinguish which situation it is.<br />**Scenario description:**<br />- `true`: infants is supported by this fare, `infantPrice` and `infantTax` will >= `0`<br />- `false`: infants is not supported by this fare, `infantPrice` and `infantTax`will be displayed as `0`|
|»» childMandatorySeatingFee|number¦null|false|none||Only valid for FR integration.<br /><br />**FR Seat Selection Rules:**<br />- Children under 12 years old are provided with free seats.<br />- Children must be seated in the same row as an adult.<br />- Each adult may accompany up to 4 children.<br /><br />For fare families that do not include seat selection fees (e.g., Basic or Family Plus), FR offers discounted seat selection fees for adults traveling with children. The`childMandatorySeatingFee`field displays this discounted fee.<br />For fare families that already include seat selection fees, this field will be `null`.<br /><br />**Handling by Atlas for Fare Families Without Seat Selection Fees:**<br />- The number of children cannot exceed 4.<br />- Customers cannot select seats manually.<br />- Atlas will automatically assign seats randomly to one adult and all children according to FR's rules. The adult will be charged the `childMandatorySeatingFee` for their seat.<br /><br />**For Fare Families That Include Seat Selection Fees:**<br />- Seat selection is free.<br />- Users may call the seat map API to select seats; otherwise, Atlas will automatically assign seats.|
|»» transactionFeePerPax|number|true|none||Technical service fee per passenger. This field has been deprecated and final total transaction fee will calculated based on `transactionFee` and `transactionFeeMode`.|
|»» transactionFee|number|true|none||Technical service fee as per `transactionFeeMode`. The following lists the calculation methods for the final technical service fee in various situations.<br />- `transactionFeeMode`=`PER_SEGMENT`:`transactionFee` * number of passengers * number of segments.<br />- `transactionFeeMode`=`PER_TICKET`:`transactionFee` * number of passengers * number of orders on airline side.<br />- `transactionFeeMode`=`PER_PAX`:`transactionFee` * number of passengers.<br />- `transactionFeeMode`=`PER_BOOKING`:`transactionFee`.|
|»» transactionFeeMode|[TransactionFeeMode](#schematransactionfeemode)|true|none||Calculation method for technical service fee.<br />- PER_SEGMENT: Calculate based on the number of segments in the order (number of travel segments * number of passengers)<br />- PER_TICKET: Calculate based on the number of orders on the airline's side<br />- PER_PAX: Calculate based on the number of passengers<br />- PER_BOOKING: Calculate based on each order|
|»» fromSegments|[[RoutingSegment](#schemaroutingsegment)]|true|none||For outbound segments.|
|»»» aircraftCode|string¦null|false|none||IATA Code of aircraft type|
|»»» arrAirport|string|true|none||3-letter iata code for the arrival airport at which the segment is scheduled to arrive.|
|»»» arrTerminal|string¦null|false|none||The terminal at the destination airport where the segment is scheduled to arrive.|
|»»» arrTime|string|true|none||The datetime at which the segment is scheduled to arrive, in the arrival airport timezone. The format is `YYYYMMDD`.|
|»»» cabin|string¦null|false|none||RBD(known as Reservation Booking Designator) displayed by the airline.|
|»»» cabinClass|[CabinClass](#schemacabinclass)|true|none||Cabin class of the segment.<br />- 1: economy<br />- 2: business<br />- 3: first<br />- 4: premium economy|
|»»» carrier|string|true|none||IATA code of marketing carrier.|
|»»» codeShare|boolean|true|none||A flag used to identify whether it is a code share flight.|
|»»» depAirport|string|true|none||3-letter iata code for the airport at which the segment is scheduled to depart.|
|»»» depTerminal|string¦null|false|none||The terminal at the departure airport from which the segment is scheduled to depart.|
|»»» depTime|string|true|none||The datetime at which the segment is scheduled to depart, in the departure airport timezone. The format is`YYYYMMSS`.|
|»»» duration|integer|true|none||The duration of the segment in munites.|
|»»» fareFamily|string|true|none||Fare Family as per the information received from the airline|
|»»» flightNumber|string|true|none||Marketing flight number. The format is: CA123 or TR021 or FR1290, with the first two letters representing the carrier and the following number representing the flight number.|
|»»» operatingCarrier|string¦null|false|none||2-letter iata code for the operating carrier. The airline actually operating this segment. This may differ from the marketing carrier in the case of a "codeshare", where one airline sells flights operated by another airline.|
|»»» operatingFlightnumber|string¦null|false|none||Operating flight number.|
|»»» seatCount|integer|true|none||Max booking seats for the fare.|
|»»» segmentIndex|integer|true|none||Segment sequence. Starts from 1. If it is return trip, sequence for outbound trip and inbound trip would be together. The segment index also represents the flight sequence of the segment.|
|»»» stopCities|string¦null|false|none||IATA code/Name of cities from where the passengers will take stopover flights. Include IATA code of cities and use a comma in case of multiple cities to separate transfer airports count is higher than 1. For example: `CGK, SUB`. <br />`null` or blank means non-stop flight.|
|»» retSegments|[[RoutingSegment](#schemaroutingsegment)]¦null|false|none||For inbound segments. For one-way, this field will be `null` or `[]`.|
|»»» aircraftCode|string¦null|false|none||IATA Code of aircraft type|
|»»» arrAirport|string|true|none||3-letter iata code for the arrival airport at which the segment is scheduled to arrive.|
|»»» arrTerminal|string¦null|false|none||The terminal at the destination airport where the segment is scheduled to arrive.|
|»»» arrTime|string|true|none||The datetime at which the segment is scheduled to arrive, in the arrival airport timezone. The format is `YYYYMMDD`.|
|»»» cabin|string¦null|false|none||RBD(known as Reservation Booking Designator) displayed by the airline.|
|»»» cabinClass|[CabinClass](#schemacabinclass)|true|none||Cabin class of the segment.<br />- 1: economy<br />- 2: business<br />- 3: first<br />- 4: premium economy|
|»»» carrier|string|true|none||IATA code of marketing carrier.|
|»»» codeShare|boolean|true|none||A flag used to identify whether it is a code share flight.|
|»»» depAirport|string|true|none||3-letter iata code for the airport at which the segment is scheduled to depart.|
|»»» depTerminal|string¦null|false|none||The terminal at the departure airport from which the segment is scheduled to depart.|
|»»» depTime|string|true|none||The datetime at which the segment is scheduled to depart, in the departure airport timezone. The format is`YYYYMMSS`.|
|»»» duration|integer|true|none||The duration of the segment in munites.|
|»»» fareFamily|string|true|none||Fare Family as per the information received from the airline|
|»»» flightNumber|string|true|none||Marketing flight number. The format is: CA123 or TR021 or FR1290, with the first two letters representing the carrier and the following number representing the flight number.|
|»»» operatingCarrier|string¦null|false|none||2-letter iata code for the operating carrier. The airline actually operating this segment. This may differ from the marketing carrier in the case of a "codeshare", where one airline sells flights operated by another airline.|
|»»» operatingFlightnumber|string¦null|false|none||Operating flight number.|
|»»» seatCount|integer|true|none||Max booking seats for the fare.|
|»»» segmentIndex|integer|true|none||Segment sequence. Starts from 1. If it is return trip, sequence for outbound trip and inbound trip would be together. The segment index also represents the flight sequence of the segment.|
|»»» stopCities|string¦null|false|none||IATA code/Name of cities from where the passengers will take stopover flights. Include IATA code of cities and use a comma in case of multiple cities to separate transfer airports count is higher than 1. For example: `CGK, SUB`. <br />`null` or blank means non-stop flight.|
|»» rule|object|true|none||none|
|»»» hasBaggage|integer|true|none||This tag is used to identify if the fare includes free checked-in or cabin baggage.<br />- `0`: Not included<br />- `1`: Included|
|»»» baggageElements|[object]|true|none||The free baggage allowance|
|»»»» segmentNo|integer|true|none||The index of segment the baggage allowance applies to.|
|»»»» baggageType|[AncillaryCategory](#schemaancillarycategory)|true|none||Type of the baggage.|
|»»»» passengerType|[PassengerType](#schemapassengertype)|true|none||The type of passenger the baggage allowance applies to.<br />- 0: Adult<br />- 1: Child<br />- 2: Infant|
|»»»» baggagePiece|integer|true|none||Baggage pieces:<br />- `0`: No limitation<br />- `>0`: Maximum pieces|
|»»»» baggageWeight|integer|true|none||Baggage Weight, with the unit of KG.<br />- `0`: No Free baggage<br />- `-1`: No limitation on weight<br />- `>0`: Maximum weight|
|»»»» baggageSize|string|true|none||Baggage Size:<br />length＊width＊height and units. eg. `56＊36＊23cm`, `18＊14＊8inch`.<br />Or Total dimensions (length + width + height) of each piece. eg. `L+W+H<=158cm`.<br />Empty means no limitation.|
|»»»» isAllWeight|boolean¦null|false|none||Baggage is all weight: true or false|
|»»» refundRules|[object]|true|none||This node is used to fetch the refund rules of the fare. There is only one array element for one way, and two elements for round-trip. The first element is for the outbound, and the second element is for the inbound.|
|»»»» refundType|integer|true|none||Type of refund allowed.<br />- 0: Wholly unused ticket<br />- 1: Partially used ticket (For example, when the passenger has used an outbound flight and wants to refund an inbound flight.)|
|»»»» refundStatus|[RefundStatus](#schemarefundstatus)|false|none||Refund rule types (for the most restrictive condition).<br />- T: Non refundable<br />- H: Refundable with restrictions<br />- F: Full refundable|
|»»»» refundFee|integer¦null|false|none||Refund penalty amount (for the most restrictive condition)|
|»»»» currency|string¦null|false|none||The currency of refund penalty|
|»»»» refNoshow|string|true|none||Indicates if a no-show affects refunds (for the most restrictive condition).<br />- T: Non refundable<br />- H: Refundable with restrictions<br />- F: Free for refund|
|»»»» refNoShowCondition|integer|true|none||Time before scheduled flight departure|
|»»»» refNoshowFee|number|true|none||Total refund fee (for the most restrictive condition): If refNoshow = H, it should not be "null". This value includes the refund fee and no-show penalty|
|»»»» refundMethod|string¦null|false|none||Refund method: CashBackToOriginalPayment or Voucher.<br />- CashBackToOriginalPayment: Refund cash back to the original form of payment.<br />- Voucher: Refund in the form of a voucher.|
|»»»» ruleDetailList|[[AirlineRuleRes](#schemaairlineruleres)]|false|none||none|
|»»»»» status|[RefundStatus](#schemarefundstatus)|true|none||Level of refund/change.<br />- T: Non refundable<br />- H: Refundable with restrictions<br />- F: Full refundable|
|»»»»» startMinute|string|true|none||Starting time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|»»»»» endMinute|string|true|none||Ending time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|»»»»» amount|string¦null|false|none||Penalty amount for refund/change. If the`status`indicates free refund/change, then this field will be either`0`or`null`.|
|»»»»» currency|string¦null|false|none||The currency of penalty|
|»»»»» refundMethod|string¦null|false|none||Refund method: CashBackToOriginalPayment or Voucher.<br />- CashBackToOriginalPayment: Refund cash back to the original form of payment.<br />- Voucher: Refund in the form of a voucher.|
|»»» changesRules|[object]|true|none||This node is used to fetch the change rules of the fare. There is only one array element for one way, and two elements for round-trip. The first element is for the outbound, and the second element is for the inbound.|
|»»»» changesType|integer|true|none||Change flight type.<br />- `0`: Wholly unused ticket<br />- `1`: Partially used ticket (For example. When the passenger has used an outbound flight and wants to change an inbound flight)|
|»»»» changesStatus|[ChangeStatus](#schemachangestatus)|false|none||Change flight rule type (for the most restrictive condition):<br />- T: Non changeable<br />- H: Changeable with restrictions<br />- F: Free rescheduling|
|»»»» changesFee|number¦null|false|none||Change flight fee (for the most restrictive condition):<br />- If`changesStatus`=`H`, it should not be`null`<br />- If`changesStatus`=`T/F`, it can be`null`|
|»»»» currency|string¦null|false|none||The currency of change flight fee|
|»»»» revNoshow|string|true|none||Indicates if a no-show affects changes (for the most restrictive condition).<br />Valid values:<br />- T: Non changeable<br />- H: Changeable with restrictions<br />- F: Free flight change|
|»»»» revNoShowCondition|integer|true|none||Time before scheduled flight departure.|
|»»»» revNoshowFee|number|true|none||The total fee charged to change flight in case of no show. If revNoshow = H, it should not be "null." This value includes the change flight fee and no-show penalty.|
|»»»» ruleDetailList|[object]|false|none||Change conditions|
|»»»»» status|[RefundStatus](#schemarefundstatus)|true|none||Level of refund/change.<br />- T: Non refundable<br />- H: Refundable with restrictions<br />- F: Full refundable|
|»»»»» startMinute|string|true|none||Starting time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|»»»»» endMinute|string|true|none||Ending time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|»»»»» amount|string¦null|false|none||Penalty amount for refund/change. If the`status`indicates free refund/change, then this field will be either`0`or`null`.|
|»»»»» currency|string¦null|false|none||The currency of penalty|
|»»» serviceElements|[object]¦null|false|none||This function is used to fetch the other service rules of the fare. There is only one array for one way, and two arrays for round-trip. The first array is for the outbound, and the second array is for the inbound.|
|»»»» hasFreeSeat|integer|false|none||A marker used to indicate whether free seat selection is included.<br />- `0`: Not included<br />- `1`: Included<br />- `2`: Partially free|
|»»»» hasFreeMeal|integer|false|none||A marker used to indicate whether free meals are included.<br />- `0`: Not included<br />- `1`: Included|
|»» ancillaryProductElements|[[AncillaryProduct](#schemaancillaryproduct)]¦null|false|none||none|
|»»» ancillaryCode|string|true|none||A code that is relatively readable by humans and contains information about auxiliary business specifications (such as weight and quantity limitations of luggage). <br />**Note:** <br />This content is only for display purposes and should not be used for programming purposes. That is to say, do not attempt to parse the information about auxiliary business specifications from this code. If you want to access the auxiliary business specifications, please use structured fields. For example, for luggage, please use`auxBaggageElement`.|
|»»» auxBaggageElement|object¦null|false|none||Baggage specification limitations. This node is valid only when the ancillary type (`categoryCode`) is baggage.|
|»»»» isAllWeight|boolean|true|none||Mark whether the`weight`field restricts the total weight or the weight of a single piece.<br />- `true`: The weight is for all the pieces<br />- `false`: The weight is for each piece|
|»»»» piece|integer|true|none||The maximum number of pieces that can be purchased per person.<br />- `0`: No Limitation about piece<br />- `>0`: Maximum pieces|
|»»»» size|string¦null|false|none||Maximum size for the baggage|
|»»»» weight|integer|true|none||The maximum weight that can be purchased per person.<br />- `0`: No limitation for weight<br />- `>0`: Weight limit (KG)|
|»»» canPurchasePostTicket|integer|true|none||A flag used to mark if this ancillary product can be purchased in the post-ticketing flow.<br />- `0`: No<br />- `1`: Yes|
|»»» canPurchaseWithTicket|integer|true|none||A flag used to mark if this ancillary product can be purchased during the booking flow.<br />- `0`: No<br />- `1`: Yes|
|»»» categoryCode|[AncillaryCategory](#schemaancillarycategory)|true|none||Type of the ancillary.<br /><br />- StandardCheckInBaggage: Standard Check-in Baggage.<br />- CabinBaggage: Usually refers to the Cabin Baggage Overhead Locker. Transition value. It will gradually transition to `CabinBaggageOverheadLocker`.<br />- CabinBaggageOverheadLocker: Cabin Baggage Overhead Locker.<br />- CabinBaggageUnderSeat: Cabin Baggage Under Seat. Usually refers to the personal item.|
|»»» clientTechnicalServiceFee|number¦null|false|none||The service fee charged by Atlas for the purchase of the ancillary.|
|»»» currency|string|true|none||The currency in which Atlas settles transactions with you|
|»»» maxQty|integer|true|none||The maximum number of purchases allowed per person per flight segment|
|»»» minQty|integer|true|none||The minimum quantity allowed to be purchased per person per flight segment.|
|»»» price|number|true|none||Price for this ancillary.|
|»»» productCode|string|true|none||Unique identifier for the ancillary product. It would be used in the order request.|
|»»» segmentIndex|integer|true|none||The index of segment the ancillary applies to.|
|»»» vendorCurrency|string|true|none||The currency in which the vendor charges for the ancillary. If the fare does not allow for the VCC pass-through or BYOA payment, this information will be`null`.|
|»»» vendorPrice|integer|true|none||The price charged by the vendor for the ancillary. If the fare does not allow for the VCC pass-through or BYOA payment, this information will be`null`.|
|»» vendorFare|object|true|none||To identify the vendor’s fare with vendor’s currency. It is only available when`supportPaymentMethods`contains`3`or`4`.|
|»»» vendorAdultPrice|number|true|none||Adult fare per passenger in vendor’s currency|
|»»» vendorAdultTax|number|true|none||Adult tax per passenger in vendor’s currency|
|»»» vendorChildPrice|number|true|none||Child fare per passenger in vendor’s currency|
|»»» vendorChildTax|number|true|none||Child tax per passenger in vendor’s currency|
|»»» vendorInfantPrice|number|true|none||Infant fare per passenger in vendor’s currency|
|»»» vendorInfantTax|integer|true|none||Infant tax per passenger in vendor’s currency|
|»»» vendorCurrency|string|true|none||Vendor’s currency|
|»» links|[TAndCLink](#schematandclink)|true|none||The terms and conditions links of the airlines. Will only return in verify response.|
|»»» carrier|string|true|none||IATA code for the airline|
|»»» kind|string|true|none||always:`terms`|
|»»» link|string|true|none||URL to the carrier's terms and conditions|
|»»» description|string|true|none||Carrier terms and conditions|
|»» separateBookings|boolean|true|none||When the outbound and inbound of round trip need to be booked separately, it will be true.|
|»» refreshTime|string|true|none||If the fare is from the cache of Atlas, this field is used to indicate the refresh time of the cache. The time is a certain moment in the past (UTC), and the format is:`yyyy-MM-dd'T'HH:mm:ss'Z'`.|
|»» expireTime|string|true|none||If the current fare comes from the cache of Atlas, this field is used to indicate the estimated expiration time of the cache. This time is a certain moment in the future (UTC), and the format is:`yyyy-MM-dd'T'HH:mm:ss'Z'`.<br />**Note:** <br />This time is estimated, which means Atlas may refresh the cache before or after that time.|
|»» ancillarySupported|[string]|true|none||A list of ancillary service types that the fare allows for additional purchase. Possible value contains:<br />- `luggage`<br />- `seat`: You can carry out the subsequent seat selection process through our seat map interface.|
|»» cardChargeList|[[CardCharge](#schemacardcharge)]¦null|false|none||Payment handling fee for MoR/VCC|
|»»» cardType|[CardType](#schemacardtype)|true|none||Card types, such as Visa, MasterCard|
|»»» percentage|number¦null|false|none||Percentage of payment handling fee|
|»»» charge|number¦null|false|none||The amount of payment handling fee|
|»»» currency|string¦null|false|none||Currency of `charge`|

#### 枚举值

|属性|值|
|---|---|
|status|100|
|status|101|
|status|102|
|status|105|
|status|106|
|status|107|
|status|108|
|status|109|
|status|110|
|status|111|
|status|112|
|status|113|
|status|114|
|status|116|
|status|123|
|status|124|
|status|126|
|status|900|
|status|9999|
|supportCreditTransPayment|0|
|supportCreditTransPayment|1|
|type|base|
|type|tax|
|type|fee|
|type|base|
|type|tax|
|type|fee|
|type|base|
|type|tax|
|type|fee|
|transactionFeeMode|PER_SEGMENT|
|transactionFeeMode|PER_TICKET|
|transactionFeeMode|PER_PAX|
|transactionFeeMode|PER_BOOKING|
|cabinClass|1|
|cabinClass|2|
|cabinClass|3|
|cabinClass|4|
|cabinClass|1|
|cabinClass|2|
|cabinClass|3|
|cabinClass|4|
|baggageType|StandardCheckInBaggage|
|baggageType|CabinBaggage|
|baggageType|CabinBaggageUnderSeat|
|baggageType|CabinBaggageOverheadLocker|
|passengerType|0|
|passengerType|1|
|passengerType|2|
|refundStatus|T|
|refundStatus|H|
|refundStatus|F|
|refundMethod|CashBackToOriginalPayment|
|refundMethod|Voucher|
|status|T|
|status|H|
|status|F|
|refundMethod|CashBackToOriginalPayment|
|refundMethod|Voucher|
|changesStatus|T|
|changesStatus|H|
|changesStatus|F|
|status|T|
|status|H|
|status|F|
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

## POST Get Offer

POST /getOffers.do

**Dependency:**
No preceding function needs to be called before Get Offer.

> - Compared to the Verify API, the GetOffer API does not rely on Search results and improves the success rate of price verify. Since using our GetOffer real-time search increases the L2B Ratio of our requesting carrier API, not all carriers support price verification via the GetOffer.
> - Please contact your Key Account Manager if you want to use the GetOffer API. Atlas will review your workflow and if deemed aplicable, Atlas will provide further information and support you with the implementation of this API.

**Endpoint:**
https://sandbox.atriptech.com/getOffers.do

> Body 请求参数

```json
{
  "adults": 1,
  "children": 0,
  "infants": 0,
  "inboundSegments": [
    {
      "arrivalAirport": "NRT",
      "carrier": "IJ",
      "departureAirport": "PVG",
      "departureDate": "20250908",
      "flightNumber": "004"
    }
  ],
  "outboundSegments": [
    {
      "arrivalAirport": "PVG",
      "carrier": "IJ",
      "departureAirport": "NRT",
      "departureDate": "20250904",
      "flightNumber": "001"
    }
  ]
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
|» adults|body|integer| 是 |Number of adults|
|» children|body|integer¦null| 否 |Number of children|
|» infants|body|integer¦null| 否 |Number of infants|
|» outboundSegments|body|[[UniqueSellingSegment](#schemauniquesellingsegment)]| 是 |Arrange the outbound flight segments in the order of flight.|
|»» carrier|body|string| 是 |IATA two letter code of marketing carrier, case sensitive|
|»» departureAirport|body|string| 是 |IATA three letter code of departure airport which is case sensitive. If the value is illegal, the system will prompt that the airport does not exist.|
|»» arrivalAirport|body|string| 是 |IATA three letter code of arrival airport which is case sensitive. If the value is illegal, the system will prompt that the airport does not exist.|
|»» flightNumber|body|string| 是 |Marketing flight number. Attention: Without airline code prefix. It should be noted that some users may enter flight numbers with or without zero padding, for example, you may enter 06 (or 6), but the airline may be 6 (or 06). Anyway, we will return to the user based on the actual flight number provided by the airline, and the user may need to handle the differences between request and response.|
|»» departureDate|body|string(date)| 是 |Departure date. Format: yyyyMMdd. We do not require users to specify departure times, nor do we want to return segments based on specific departure time. Considering that the externally transmitted time may not match the actual flight segment time on the supplier's (airline's) side, this can lead to search results being lost. Therefore, we will return the results of all flight segments that took off within the specified date, and it will be up to the user to decide how to use them.|
|» inboundSegments|body|[[UniqueSellingSegment](#schemauniquesellingsegment)]¦null| 否 |Return flight segments are arranged in the order of flight. Optional, null or [] indicates one-way.|
|»» departureAirport|body|string| 是 |出发机场的IATA三字码|
|»» arrivalAirport|body|string| 是 |达到机场的IATA三字码|
|»» carrier|body|string| 是 |marketing carrier的IATA二字码|
|»» flightNumber|body|string| 是 |marketing flight number，不带航司代码前缀|
|»» departureDate|body|string(date)| 是 |出发日期|
|» currency|body|string¦null| 否 |Quotation currency, optional, default will be determined based on a certain strategy, such as the currency of the customer's pre deposit account|
|» residentCode|body|string¦null| 否 |Resident discount code|

> 返回示例

> 200 Response

```json
{
  "data": [
    {
      "bookingRequirement": {
        "passenger": {
          "cardIssuePlace": {
            "required": true,
            "type": "string"
          },
          "birthday": {
            "required": true,
            "type": "string"
          },
          "cardNum": {
            "required": true,
            "type": "string"
          },
          "passengerType": {
            "required": true,
            "type": "int"
          },
          "nationality": {
            "required": true,
            "type": "string"
          },
          "gender": {
            "required": true,
            "type": "string"
          },
          "cardExpired": {
            "required": true,
            "type": "string"
          },
          "cardType": {
            "required": true,
            "type": "string"
          },
          "name": {
            "required": true,
            "type": "string"
          }
        }
      },
      "offer": {
        "inboundJourney": {
          "journeyID": "ij",
          "segments": [
            {
              "cabinClass": "Economy",
              "carrier": "IJ",
              "duration": 180,
              "fareFamily": "Lucky Spring",
              "flightNumber": "4",
              "legs": [
                {
                  "aircraftType": "",
                  "arrivalAirport": "NRT",
                  "arrivalTerminal": "",
                  "arrivalTime": "202509082135",
                  "departureAirport": "PVG",
                  "departureTerminal": "",
                  "departureTime": "202509081735"
                }
              ],
              "rBD": "R1",
              "seatsLeft": 9,
              "segmentID": "is-2"
            }
          ]
        },
        "offerID": "o_e11c74d10d85485a8732b3800aa55f1d_1",
        "offerToken": "VFlPX1NIQV8yXzIwMjUwOTA0XzIwMjUwOTA4XzFfMF8wfFJDUzc3NDc4X2FwaV8xfDF8MTg0LjcyXzE2Ny41OV81NS43M18wLjUwXzQwOC41NF9VU0R8VFlPX1NIQV8xXzIwMjUwOTA0XzIwMjUwOTA4XzFfMF8wXk5SVC1JSjAwMS1SMS1QVkctMjAyNTA5MDQyMjQ1LTIwMjUwOTA1MDEyNS1MdWNreSBTcHJpbmctMS0jUFZHLUlKMDA0LVIxLU5SVC0yMDI1MDkwODE3MzUtMjAyNTA5MDgyMTM1LUx1Y2t5IFNwcmluZy0yLV4xODQuNzJfMTY3LjU5XzU1LjczXzAuNTBfNDA4LjU0XkFJSl9BSUpeXl5DTlleMTMyNi4wMF4xMjAzLjAwXjQwMC4wMF4wfDB8MjAyNTA4MTYxNzA4MTl8MHxvX2UxMWM3NGQxMGQ4NTQ4NWE4NzMyYjM4MDBhYTU1ZjFkfHx8R2V0T2ZmZXJ8fDAuNTB8M3wwfHxub3JtYWx8ZmFsc2U=.PaLlOsP6tMoDuhw9U/VyFOL5mcAdLP2PeAGRBzPunwg=",
        "outboundJourney": {
          "journeyID": "oj",
          "segments": [
            {
              "cabinClass": "Economy",
              "carrier": "IJ",
              "duration": 220,
              "fareFamily": "Lucky Spring",
              "flightNumber": "1",
              "legs": [
                {
                  "aircraftType": "",
                  "arrivalAirport": "PVG",
                  "arrivalTerminal": "",
                  "arrivalTime": "202509050125",
                  "departureAirport": "NRT",
                  "departureTerminal": "",
                  "departureTime": "202509042245"
                }
              ],
              "rBD": "R1",
              "seatsLeft": 9,
              "segmentID": "os-1"
            }
          ]
        },
        "paxFares": [
          {
            "paxType": "ADT",
            "price": {
              "baseAmount": 94.73,
              "currency": "USD",
              "taxes": 89.99
            }
          },
          {
            "paxType": "CHD",
            "price": {
              "baseAmount": 94.73,
              "currency": "USD",
              "taxes": 72.86
            }
          },
          {
            "paxType": "INF",
            "price": {
              "baseAmount": 55.73,
              "currency": "USD",
              "taxes": 0
            }
          }
        ],
        "penalties": [
          {
            "amount": 576,
            "currency": "CNY",
            "journeyRefIDs": [
              "oj"
            ],
            "rule": {
              "airlineFee": 0,
              "currency": "CNY",
              "effectiveMinutes": 525600,
              "expirationMinutes": 43200,
              "fixedAmount": 576,
              "levelType": "Partial",
              "paxTypes": [
                "ADT",
                "CHD"
              ],
              "percent": 0,
              "percentBase": "fare+tax",
              "type": "Refund"
            }
          },
          {
            "amount": 615,
            "currency": "CNY",
            "journeyRefIDs": [
              "oj"
            ],
            "rule": {
              "airlineFee": 0,
              "currency": "CNY",
              "effectiveMinutes": 43200,
              "expirationMinutes": 21600,
              "fixedAmount": 615,
              "levelType": "Partial",
              "paxTypes": [
                "ADT",
                "CHD"
              ],
              "percent": 0,
              "percentBase": "fare+tax",
              "type": "Refund"
            }
          },
          {
            "amount": 654,
            "currency": "CNY",
            "journeyRefIDs": [
              "oj"
            ],
            "rule": {
              "airlineFee": 0,
              "currency": "CNY",
              "effectiveMinutes": 21600,
              "expirationMinutes": 10080,
              "fixedAmount": 654,
              "levelType": "Partial",
              "paxTypes": [
                "ADT",
                "CHD"
              ],
              "percent": 0,
              "percentBase": "fare+tax",
              "type": "Refund"
            }
          },
          {
            "amount": 693,
            "currency": "CNY",
            "journeyRefIDs": [
              "oj"
            ],
            "rule": {
              "airlineFee": 0,
              "currency": "CNY",
              "effectiveMinutes": 10080,
              "expirationMinutes": 1440,
              "fixedAmount": 693,
              "levelType": "Partial",
              "paxTypes": [
                "ADT",
                "CHD"
              ],
              "percent": 0,
              "percentBase": "fare+tax",
              "type": "Refund"
            }
          },
          {
            "amount": 771,
            "currency": "CNY",
            "journeyRefIDs": [
              "oj"
            ],
            "rule": {
              "airlineFee": 0,
              "currency": "CNY",
              "effectiveMinutes": 1440,
              "expirationMinutes": 0,
              "fixedAmount": 771,
              "levelType": "Partial",
              "paxTypes": [
                "ADT",
                "CHD"
              ],
              "percent": 0,
              "percentBase": "fare+tax",
              "type": "Refund"
            }
          },
          {
            "amount": 771,
            "currency": "CNY",
            "journeyRefIDs": [
              "oj"
            ],
            "rule": {
              "airlineFee": 0,
              "currency": "CNY",
              "effectiveMinutes": 0,
              "expirationMinutes": -43200,
              "fixedAmount": 771,
              "levelType": "Partial",
              "paxTypes": [
                "ADT",
                "CHD"
              ],
              "percent": 0,
              "percentBase": "fare+tax",
              "type": "Refund"
            }
          },
          {
            "amount": 410,
            "currency": "CNY",
            "journeyRefIDs": [
              "ij"
            ],
            "rule": {
              "airlineFee": 0,
              "currency": "CNY",
              "effectiveMinutes": 525600,
              "expirationMinutes": 43200,
              "fixedAmount": 410,
              "levelType": "Partial",
              "paxTypes": [
                "ADT",
                "CHD"
              ],
              "percent": 0,
              "percentBase": "fare+tax",
              "type": "Refund"
            }
          },
          {
            "amount": 439,
            "currency": "CNY",
            "journeyRefIDs": [
              "ij"
            ],
            "rule": {
              "airlineFee": 0,
              "currency": "CNY",
              "effectiveMinutes": 43200,
              "expirationMinutes": 21600,
              "fixedAmount": 439,
              "levelType": "Partial",
              "paxTypes": [
                "ADT",
                "CHD"
              ],
              "percent": 0,
              "percentBase": "fare+tax",
              "type": "Refund"
            }
          },
          {
            "amount": 468,
            "currency": "CNY",
            "journeyRefIDs": [
              "ij"
            ],
            "rule": {
              "airlineFee": 0,
              "currency": "CNY",
              "effectiveMinutes": 21600,
              "expirationMinutes": 10080,
              "fixedAmount": 468,
              "levelType": "Partial",
              "paxTypes": [
                "ADT",
                "CHD"
              ],
              "percent": 0,
              "percentBase": "fare+tax",
              "type": "Refund"
            }
          },
          {
            "amount": 497,
            "currency": "CNY",
            "journeyRefIDs": [
              "ij"
            ],
            "rule": {
              "airlineFee": 0,
              "currency": "CNY",
              "effectiveMinutes": 10080,
              "expirationMinutes": 1440,
              "fixedAmount": 497,
              "levelType": "Partial",
              "paxTypes": [
                "ADT",
                "CHD"
              ],
              "percent": 0,
              "percentBase": "fare+tax",
              "type": "Refund"
            }
          },
          {
            "amount": 555,
            "currency": "CNY",
            "journeyRefIDs": [
              "ij"
            ],
            "rule": {
              "airlineFee": 0,
              "currency": "CNY",
              "effectiveMinutes": 1440,
              "expirationMinutes": 0,
              "fixedAmount": 555,
              "levelType": "Partial",
              "paxTypes": [
                "ADT",
                "CHD"
              ],
              "percent": 0,
              "percentBase": "fare+tax",
              "type": "Refund"
            }
          },
          {
            "amount": 555,
            "currency": "CNY",
            "journeyRefIDs": [
              "ij"
            ],
            "rule": {
              "airlineFee": 0,
              "currency": "CNY",
              "effectiveMinutes": 0,
              "expirationMinutes": -43200,
              "fixedAmount": 555,
              "levelType": "Partial",
              "paxTypes": [
                "ADT",
                "CHD"
              ],
              "percent": 0,
              "percentBase": "fare+tax",
              "type": "Refund"
            }
          }
        ],
        "services": [
          {
            "level": "Free",
            "metadata": {
              "maximumDimension": "",
              "maximumPiece": 0,
              "maximumWeight": 0,
              "type": "StandardCheckInBaggage"
            },
            "paxTypes": [
              "CHD"
            ],
            "segmentRefIDs": [
              "os-1",
              "is-2"
            ],
            "serviceID": "fbs-1",
            "type": "Baggage"
          },
          {
            "level": "Free",
            "metadata": {
              "maximumDimension": "",
              "maximumPiece": 0,
              "maximumWeight": 0,
              "type": "StandardCheckInBaggage"
            },
            "paxTypes": [
              "INF"
            ],
            "segmentRefIDs": [
              "os-1",
              "is-2"
            ],
            "serviceID": "fbs-2",
            "type": "Baggage"
          },
          {
            "level": "Free",
            "metadata": {
              "maximumDimension": "",
              "maximumPiece": 0,
              "maximumWeight": 0,
              "type": "StandardCheckInBaggage"
            },
            "paxTypes": [
              "ADT"
            ],
            "segmentRefIDs": [
              "os-1",
              "is-2"
            ],
            "serviceID": "fbs-3",
            "type": "Baggage"
          },
          {
            "level": "Free",
            "metadata": {
              "maximumDimension": "56*36*23cm",
              "maximumPiece": 0,
              "maximumWeight": 0,
              "type": "CabinBaggageUnderSeat"
            },
            "paxTypes": [
              "INF"
            ],
            "segmentRefIDs": [
              "os-1",
              "is-2"
            ],
            "serviceID": "fbs-4",
            "type": "Baggage"
          },
          {
            "level": "Free",
            "metadata": {
              "maximumDimension": "56*36*23cm",
              "maximumPiece": 1,
              "maximumWeight": 7,
              "type": "CabinBaggageUnderSeat"
            },
            "paxTypes": [
              "CHD"
            ],
            "segmentRefIDs": [
              "os-1",
              "is-2"
            ],
            "serviceID": "fbs-5",
            "type": "Baggage"
          },
          {
            "level": "Free",
            "metadata": {
              "maximumDimension": "56*36*23cm",
              "maximumPiece": 1,
              "maximumWeight": 7,
              "type": "CabinBaggageUnderSeat"
            },
            "paxTypes": [
              "ADT"
            ],
            "segmentRefIDs": [
              "os-1",
              "is-2"
            ],
            "serviceID": "fbs-6",
            "type": "Baggage"
          },
          {
            "level": "Chargeable",
            "paxTypes": [
              "ADT",
              "CHD"
            ],
            "segmentRefIDs": [
              "os-1"
            ],
            "serviceID": "fss-1",
            "type": "Seat"
          },
          {
            "level": "Chargeable",
            "paxTypes": [
              "ADT",
              "CHD"
            ],
            "segmentRefIDs": [
              "is-2"
            ],
            "serviceID": "fss-2",
            "type": "Seat"
          },
          {
            "level": "Chargeable",
            "paxTypes": [
              "ADT",
              "CHD"
            ],
            "segmentRefIDs": [
              "os-1"
            ],
            "serviceID": "fms-1",
            "type": "Meal"
          },
          {
            "level": "Chargeable",
            "paxTypes": [
              "ADT",
              "CHD"
            ],
            "segmentRefIDs": [
              "is-2"
            ],
            "serviceID": "fms-2",
            "type": "Meal"
          }
        ],
        "terms": []
      },
      "serviceFee": {
        "amountPerUnit": 0.5,
        "currency": "USD",
        "unit": "PER_PAX"
      },
      "supportedPaymentMethods": [
        "Deposit"
      ]
    }
  ],
  "status": 0
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
|» status|integer|true|none||- 0: success<br />- 116: airline error<br />- 112: timed out<br />- 9999: system error|
|» msg|string¦null|false|none||As an additional description of the response result. Especially when the interface reports an error (status ≠ 0), it is usually a human-readable error message.<br /><br><br />**Note:** Do not use this field in any programming scenarios, such as judging whether the interface response is successful based on this field. You should always judge solely based on whether the status is equal to 0.|
|» data|[object]¦null|false|none||none|
|»» offer|object|true|none||none|
|»»» offerID|string|true|none||The unique ID for this offer, globally unique.|
|»»» offerToken|[OfferToken](#schemaoffertoken)¦null|false|none||A encrypted string containing complete flight information and related quotation information, which can be used to uniquely identify a complete itinerary. This content can be freely distributed and stored by users, but modification is not allowed. At the same time, this content has a certain validity period (generally not exceeding 6 hours). One use case of Offer Token is when users search for flight tickets and quotes through Atlas' caching system, and then use this information to perform real-time price verification in subsequent steps to confirm if there are any price changes. At this point, Atlas will directly query real-time quotes from the airline, rather than through caching.|
|»»» paxFares|[[PaxFare](#schemapaxfare)]|true|none||Contains ticket prices and taxes corresponding to each passenger type. If there are no elements for certain passenger types in the list, it means that the ticket is not currently being sold for that passenger type.|
|»»»» paxType|[PaxTypeEnums](#schemapaxtypeenums)|true|none||Passenger type.<br />- ADT: Representing adults<br />- CHD: Representing children<br />- INF: Representing a baby|
|»»»» price|[Price](#schemaprice)|true|none||none|
|»»»»» baseAmount|number|true|none||Basic price, excluding taxes. Unit: Yuan, with a maximum of 2 decimal places retained|
|»»»»» taxes|number|true|none||Total taxes. Unit: Yuan, with a maximum of 2 decimal places retained|
|»»»»» currency|string|true|none||Currency code, capitalized|
|»»» penalties|[object]|true|none||none|
|»»»» journeyRefIDs|[string]|true|none||The reference to the journey ID indicates the journey to which the rule applies, which may include references to multiple journey IDs (such as round trips), indicating that multiple journeys are applicable to the rule.|
|»»»» amount|number|true|none||Pennalty amount. Unit: Yuan. Keep up to 2 decimal places.|
|»»»» currency|string|true|none||Currency code corresponding to the pennalty amount, in capital letters. This currency may be different from the fare currency, depending on the airline.|
|»»»» rule|object|true|none||Calculation rules for the penalty|
|»»»»» type|string|true|none||Rule type: Refund or Change rule|
|»»»»» paxTypes|[[PaxTypeEnums](#schemapaxtypeenums)]|true|none||There may be multiple types of passengers to which this rule applies|
|»»»»» levelType|[FareRuleLevelEnums](#schemafarerulelevelenums)|true|none||- Full: If it is a refund, it means a full refund; If it is a rescheduling, it means free rescheduling<br />- Partial: If it is a refund, it means a partial refund; If it is a rescheduling, it means that there will be a fee for reschedulin<br />- None: If it is a refund, it means it cannot be refunded; If it is a rescheduling, it means that rescheduling is not possible|
|»»»»» effectiveMinutes|integer|true|none||Form a time interval together with expiratorMinutes to indicate the time range within which the rule applies. This value serves as the starting point of the interval, measured in minutes. >= 0 represents the number of minutes before takeoff, <0 represents the number of minutes after takeoff.|
|»»»»» expirationMinutes|integer|true|none||Form a time interval together with expirationMinutes to indicate the time range within which the rule applies. This value serves as the end point of the interval, measured in minutes. >=0 represents the number of minutes before takeoff, <0 represents the number of minutes after takeoff.|
|»»»»» fixedAmount|number|true|none||Fixed deduction penalty. Unit: Yuan, with a maximum of 2 decimal places retained.|
|»»»»» airlineFee|number|true|none||Fixed deduction of airline handling fees. Unit: Yuan, with a maximum of 2 decimal places retained.|
|»»»»» currency|string|true|none||Currency of penalty and airline handling fees. This currency may be different from the fare currency, depending on the airline.|
|»»»»» percent|number|true|none||Penalty percentage|
|»»»»» percentBase|string|true|none||Penalty percentage base.<br />- fare+tax: The base for calculating the percentage is the total price including tax<br />- fare: It indicates that the penalty percentage is based on the base price, excluding tax|
|»»» services|[[Service](#schemaservice)]¦null|false|none||Includes various free and chargeable services, including but not limited to: baggages, seat selection, meals, etc|
|»»»» serviceID|string|true|none||The unique ID of this service. Note: this ID is unique within the context of the current offer.|
|»»»» segmentRefIDs|[string]|true|none||The flight segment ID reference applicable to this service|
|»»»» type|[ServiceTypeEnums](#schemaservicetypeenums)|true|none||Service Type.<br />- Baggage: represent a package<br />- Seat: represent seat selection<br />- Meal: represent meals|
|»»»» level|[ServiceLevelEnums](#schemaservicelevelenums)|true|none||Service fee level.<br />- Free: Free service<br />- Partial: Partially Free<br />- Chargeable: Chargeable|
|»»»» paxTypes|[[PaxTypeEnums](#schemapaxtypeenums)]|true|none||There may be multiple types of passengers for which this service is applicable. The items are one of:<br />- ADT: Representing adults<br />- CHD: Representing children<br />- INF: Representing a baby|
|»»»» metadata|[BaggageAllowance](#schemabaggageallowance)|false|none||Metadata representing different services, such as package weight, quantity, size, and other restrictions. Note: The content of this node may vary depending on the type of service. Users should read the content of the node according to different service types.|
|»»»»» type|[BaggageTypeEnums](#schemabaggagetypeenums)|true|none||Type of baggage|
|»»»»» maximumWeight|integer|true|none||Maximum weight limit.<br />- `0`: No Free baggage<br />- `-1`: No limitation on weight<br />- `>0`: Maximum weight|
|»»»»» maximumPiece|integer|true|none||Maximum quantity limit.<br />- `0`: No limitation<br />- `>0`: Maximum pieces|
|»»»»» maximumDimension|string¦null|false|none||Maximum size limit. Note: This content is currently not guaranteed to be structured (parsed)|
|»»» outboundJourney|[Journey](#schemajourney)|true|none||none|
|»»»» journeyID|string|true|none||行程唯一ID，在当前Offer的上下文内唯一。|
|»»»» segments|[[Segment](#schemasegment)]|true|none||航段按照飞行顺序展示|
|»»»»» segmentID|string|true|none||Unique ID for the flight segment. Note: This ID is unique within the context of the current offer.|
|»»»»» carrier|string|true|none||Marketing carrier IATA two letter code, capitalized.|
|»»»»» flightNumber|string|true|none||Marketing flight number. Attention: Do not include airline code prefix.|
|»»»»» operatingCarrier|string¦null|false|none||Operating carrier IATA two letter code, capitalized.|
|»»»»» operatingFlightNumber|string¦null|false|none||Operating flight number. Attention: Do not include airline code prefix.|
|»»»»» duration|integer¦null|false|none||Representing the flight duration of the entire flight segment, in minutes|
|»»»»» legs|[[Leg](#schemaleg)]|true|none||The physical flight information that constitutes the flight segment and the stopover information can be obtained from this. The number of elements=1 indicates that there is no stopping point. Display in flight order.|
|»»»»»» departureAirport|string|true|none||IATA two letter code for the departure airport, in capital letters|
|»»»»»» departureTime|string(date-time)¦null|false|none||Takeoff time, format: yyyyMMddHHmm. For those taking off from transit points, the departure time may not be available; For those taking off from the starting point, this time will definitely be available.|
|»»»»»» departureTerminal|string¦null|false|none||Departure terminal.|
|»»»»»» arrivalAirport|string|true|none||IATA two letter code upon arrival at the airport, in capital letters|
|»»»»»» arrivalTime|string¦null|false|none||Arrival time, format: yyyyMMddHHmm. For those arriving as transit points, the arrival time may not be available; For those who arrive as the endpoint, there will definitely be an arrival time.|
|»»»»»» arrivalTerminal|string¦null|false|none||Arriving terminal.|
|»»»»»» aircraftType|string¦null|false|none||Aircraft type code. According to the actual display of the airline.|
|»»»»» fareFamily|string¦null|false|none||none|
|»»»»» RBD|string¦null|false|none||none|
|»»»»» cabinClass|[CabinClassEnums](#schemacabinclassenums)¦null|false|none||仓等|
|»»»»» seatsLeft|integer|false|none||the number of remaining seats|
|»»» inboundJourney|[Journey](#schemajourney)¦null|false|none||Inbound journey, null means one-way.|
|»»»» journeyID|string|true|none||Unique ID for the itinerary. Note: the ID is unique within the context of the current offer.|
|»»»» segments|[[Segment](#schemasegment)]|true|none||Display flight segments in flight order|
|»»»»» segmentID|string|true|none||Unique ID for the flight segment. Note: This ID is unique within the context of the current offer.|
|»»»»» carrier|string|true|none||Marketing carrier IATA two letter code, capitalized.|
|»»»»» flightNumber|string|true|none||Marketing flight number. Attention: Do not include airline code prefix.|
|»»»»» operatingCarrier|string¦null|false|none||Operating carrier IATA two letter code, capitalized.|
|»»»»» operatingFlightNumber|string¦null|false|none||Operating flight number. Attention: Do not include airline code prefix.|
|»»»»» duration|integer¦null|false|none||Representing the flight duration of the entire flight segment, in minutes|
|»»»»» legs|[[Leg](#schemaleg)]|true|none||The physical flight information that constitutes the flight segment and the stopover information can be obtained from this. The number of elements=1 indicates that there is no stopping point. Display in flight order.|
|»»»»» fareFamily|string¦null|false|none||none|
|»»»»» RBD|string¦null|false|none||none|
|»»»»» cabinClass|[CabinClassEnums](#schemacabinclassenums)¦null|false|none||仓等|
|»»»»» seatsLeft|integer|false|none||the number of remaining seats|
|»»» terms|[[Term](#schematerm)]¦null|false|none||none|
|»»»» carrier|string|true|none||Marketing carrier IATA two letter code, capitalize|
|»»»» URL|string|true|none||terms and condition link|
|»» serviceFee|[ServiceFee](#schemaservicefee)|true|none||none|
|»»» amountPerUnit|number|true|none||Unit amount, unit: yuan, with a maximum of 2 decimal places retained|
|»»» unit|[ServiceFeeModeEnums](#schemaservicefeemodeenums)|true|none||Amount unit.<br />- PER_SEGMENT: Calculated per flight segment<br />- PER_PAX: Calculated per passenger<br />- PER_BOOKING: Calculated per order|
|»»» currency|string|true|none||Currency code for the amount, in capital letters|
|»» bookingRequirement|[BookingRequirementSchema](#schemabookingrequirementschema)|true|none||none|
|»»» passenger|[PaxConstraint](#schemapaxconstraint)|true|none||Specific requirements for passenger information|
|»»»» name|[Constraint](#schemaconstraint)|true|none||none|
|»»»»» type|string|true|none||Data type|
|»»»»» required|boolean|true|none||Required or not|
|»»»»» description|string|false|none||none|
|»»»»» maxLength|string|false|none||none|
|»»»» passengerType|[Constraint](#schemaconstraint)|true|none||none|
|»»»»» type|string|true|none||Data type|
|»»»»» required|boolean|true|none||Required or not|
|»»»»» description|string|false|none||none|
|»»»»» maxLength|string|false|none||none|
|»»»» birthday|[Constraint](#schemaconstraint)|true|none||none|
|»»»»» type|string|true|none||Data type|
|»»»»» required|boolean|true|none||Required or not|
|»»»»» description|string|false|none||none|
|»»»»» maxLength|string|false|none||none|
|»»»» gender|[Constraint](#schemaconstraint)|true|none||none|
|»»»»» type|string|true|none||Data type|
|»»»»» required|boolean|true|none||Required or not|
|»»»»» description|string|false|none||none|
|»»»»» maxLength|string|false|none||none|
|»»»» nationality|[Constraint](#schemaconstraint)|true|none||none|
|»»»»» type|string|true|none||Data type|
|»»»»» required|boolean|true|none||Required or not|
|»»»»» description|string|false|none||none|
|»»»»» maxLength|string|false|none||none|
|»»»» cardType|[Constraint](#schemaconstraint)|true|none||none|
|»»»»» type|string|true|none||Data type|
|»»»»» required|boolean|true|none||Required or not|
|»»»»» description|string|false|none||none|
|»»»»» maxLength|string|false|none||none|
|»»»» cardNum|[Constraint](#schemaconstraint)|true|none||none|
|»»»»» type|string|true|none||Data type|
|»»»»» required|boolean|true|none||Required or not|
|»»»»» description|string|false|none||none|
|»»»»» maxLength|string|false|none||none|
|»»»» cardIssuePlace|[Constraint](#schemaconstraint)|true|none||none|
|»»»»» type|string|true|none||Data type|
|»»»»» required|boolean|true|none||Required or not|
|»»»»» description|string|false|none||none|
|»»»»» maxLength|string|false|none||none|
|»»»» cardExpired|[Constraint](#schemaconstraint)|true|none||none|
|»»»»» type|string|true|none||Data type|
|»»»»» required|boolean|true|none||Required or not|
|»»»»» description|string|false|none||none|
|»»»»» maxLength|string|false|none||none|
|»» supportedPaymentMethods|[[PaymentMethodEnums](#schemapaymentmethodenums)]|false|none||Supported payment methods. `null`or`[]`indicates that no payment methods are available.|

#### 枚举值

|属性|值|
|---|---|
|status|0|
|status|116|
|status|112|
|status|9999|
|paxType|ADT|
|paxType|CHD|
|paxType|INF|
|type|Refund|
|type|Change|
|levelType|Full|
|levelType|Partial|
|levelType|None|
|percentBase|fare+tax|
|percentBase|fare|
|type|Baggage|
|type|Seat|
|type|Meal|
|level|Free|
|level|Partial|
|level|Chargeable|
|type|StandardCheckInBaggage|
|type|CabinBaggage|
|type|CabinBaggageOverheadLocker|
|type|CabinBaggageUnderSeat|
|cabinClass|Economy|
|cabinClass|Business|
|cabinClass|First|
|cabinClass|PremiumEconomy|
|cabinClass|Economy|
|cabinClass|Business|
|cabinClass|First|
|cabinClass|PremiumEconomy|
|unit|PER_SEGMENT|
|unit|PER_PAX|
|unit|PER_BOOKING|
|type|string|
|type|int|
|type|string|
|type|int|
|type|string|
|type|int|
|type|string|
|type|int|
|type|string|
|type|int|
|type|string|
|type|int|
|type|string|
|type|int|
|type|string|
|type|int|
|type|string|
|type|int|

## POST Seat Availability

POST /seatAvailability.do

**Dependency:**
Verify or getOffer function should be called in prior to this call.

The seat map API is divided into **independent mode** and **non-independent mode**.
- **Independent mode** means it can be used standalone without relying on other APIs.
- **Non-independent mode** depends on the price verification API or the get offer API.

> In a booking process, please call the 'seatAvailability' API to get seat availability information after price verification via 'verify' or 'getOffer'.
> Steps:
> 1. API sequence
>    * Search - Verify- seatAvailability - Order - Pay
>    * getOffer - seatAvailability - Order - Pay
> 2. Pass 'offerId' in 'seatAvailability' requests:
>    * From 'verify': Use sessionId directly.
>    From 'getOffer': Use its offerId.
> 3. In the Order step, use the productCode to add specific seat to the ticket order.

**Endpoint:**
https://sandbox.atriptech.com/seatAvailability.do

> Body 请求参数

```json
{
  "carrier": "W6",
  "outboundSegments": [
    {
      "flightNumber": "W62340",
      "segmentIndex": 1,
      "depAirport": "FCO",
      "arrAirport": "BUD",
      "cabinClass": "1",
      "depTime": "202501250825"
    }
  ],
  "inboundSegments": [
    {
      "flightNumber": "W62341",
      "segmentIndex": 2,
      "depAirport": "BUD",
      "arrAirport": "FCO",
      "cabinClass": "1",
      "depTime": "202501301915"
    }
  ]
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
|» sessionId|body|string| 是 |The`sessionId`returned by price verification api(`verify.do`). Only required in **Non-independent mode**.|
|» offerId|body|string| 是 |The`offerID`returned by get offer api(`getOffers.do`). Only required in **Non-independent mode**.|
|» carrier|body|string| 是 |The IATA code of MSC(known as Most Significant Carrier) of the itinerary.|
|» outboundSegments|body|[[SeatMapFlight](#schemaseatmapflight)]| 是 |Outbound segments. All segments of the itinerary must be specified. Segments should be arranged in the order of takeoff.|
|»» flightNumber|body|string| 是 |none|
|»» segmentIndex|body|integer| 是 |none|
|»» depAirport|body|string| 是 |none|
|»» arrAirport|body|string| 是 |none|
|»» cabinClass|body|string| 是 |none|
|»» depTime|body|string| 是 |none|
|» inboundSegments|body|[[SeatMapFlight](#schemaseatmapflight)]¦null| 否 |Inbound segments. All segments of the itinerary must be specified. Segments should be arranged in the order of takeoff.|
|»» segmentIndex|body|integer| 是 |This is the segment number, which starts from 1 and increments in the order of takeoff of each segment.|
|»» flightNumber|body|string| 是 |Marketing flight number(with airline code prefix).|
|»» depAirport|body|string| 是 |3-letter iata code for the airport at which the segment is scheduled to depart.|
|»» arrAirport|body|string| 是 |3-letter iata code for the arrival airport at which the segment is scheduled to arrive.|
|»» depTime|body|string| 是 |The datetime at which the segment is scheduled to depart, in the departure airport timezone. The format is`YYYYMMDD`.|
|»» cabinClass|body|[CabinClass](#schemacabinclass)| 是 |Cabin class.|

#### 详细说明

**»» cabinClass**: Cabin class.
- 1: economy
- 2: business
- 3: first
- 4: premium economy

#### 枚举值

|属性|值|
|---|---|
|»» cabinClass|1|
|»» cabinClass|2|
|»» cabinClass|3|
|»» cabinClass|4|

> 返回示例

> 200 Response

```json
{
  "cabins": [
    {
      "segmentIndex": 1,
      "cabin": {
        "deck": "main",
        "cabinClass": 1,
        "cabinLayout": {
          "columns": [
            {
              "designator": "A",
              "characteristics": "W"
            },
            {
              "designator": "B",
              "characteristics": "M"
            },
            {
              "designator": "C",
              "characteristics": "A"
            },
            {
              "designator": "D",
              "characteristics": "W"
            },
            {
              "designator": "E",
              "characteristics": "M"
            },
            {
              "designator": "F",
              "characteristics": "A"
            }
          ],
          "rows": {
            "first": 4,
            "last": 20
          },
          "exitRowPositions": [
            {
              "first": 4,
              "last": 5
            },
            {
              "first": 10,
              "last": 11
            },
            {
              "first": 20,
              "last": 20
            }
          ]
        },
        "rows": [
          {
            "number": 4,
            "seats": [
              {
                "column": "A",
                "seatStatus": "F",
                "seatCharacteristics": [
                  "W",
                  "L",
                  "E"
                ],
                "price": 26.29,
                "currency": "USD",
                "vendorPrice": 26.29,
                "vendorCurrency": "USD",
                "productCode": "SCI_SEAT_4A_W6_FCO_BUD"
              },
              {
                "column": "B",
                "seatStatus": "F",
                "seatCharacteristics": [
                  "M",
                  "L",
                  "E"
                ],
                "price": 10.79,
                "currency": "USD",
                "vendorPrice": 10.79,
                "vendorCurrency": "USD",
                "productCode": "SCI_SEAT_4B_W6_FCO_BUD"
              },
              {
                "column": "C",
                "seatStatus": "F",
                "seatCharacteristics": [
                  "A",
                  "L",
                  "E"
                ],
                "price": 30.13,
                "currency": "USD",
                "vendorPrice": 30.13,
                "vendorCurrency": "USD",
                "productCode": "SCI_SEAT_4C_W6_FCO_BUD"
              },
              {
                "column": "D",
                "seatStatus": "F",
                "seatCharacteristics": [
                  "W",
                  "L",
                  "E"
                ],
                "price": 88.43,
                "currency": "USD",
                "vendorPrice": 88.43,
                "vendorCurrency": "USD",
                "productCode": "SCI_SEAT_4D_W6_FCO_BUD"
              },
              {
                "column": "E",
                "seatStatus": "F",
                "seatCharacteristics": [
                  "M",
                  "L",
                  "E"
                ],
                "price": 56.78,
                "currency": "USD",
                "vendorPrice": 56.78,
                "vendorCurrency": "USD",
                "productCode": "SCI_SEAT_4E_W6_FCO_BUD"
              },
              {
                "column": "F",
                "seatStatus": "F",
                "seatCharacteristics": [
                  "A",
                  "L",
                  "E"
                ],
                "price": 29.47,
                "currency": "USD",
                "vendorPrice": 29.47,
                "vendorCurrency": "USD",
                "productCode": "SCI_SEAT_4F_W6_FCO_BUD"
              }
            ]
          }
        ]
      }
    },
    {
      "segmentIndex": 2,
      "cabin": {
        "deck": "main",
        "cabinClass": 1,
        "cabinLayout": {
          "columns": [
            {
              "designator": "A",
              "characteristics": "W"
            },
            {
              "designator": "B",
              "characteristics": "M"
            },
            {
              "designator": "C",
              "characteristics": "A"
            },
            {
              "designator": "D",
              "characteristics": "W"
            },
            {
              "designator": "E",
              "characteristics": "M"
            },
            {
              "designator": "F",
              "characteristics": "A"
            }
          ],
          "rows": {
            "first": 4,
            "last": 20
          },
          "exitRowPositions": [
            {
              "first": 4,
              "last": 5
            },
            {
              "first": 10,
              "last": 11
            },
            {
              "first": 20,
              "last": 20
            }
          ]
        },
        "rows": [
          {
            "number": 5,
            "seats": [
              {
                "column": "A",
                "seatStatus": "F",
                "seatCharacteristics": [
                  "W",
                  "L",
                  "E"
                ],
                "price": 34.25,
                "currency": "USD",
                "vendorPrice": 34.25,
                "vendorCurrency": "USD",
                "productCode": "SCI_SEAT_5A_W6_BUD_FCO"
              },
              {
                "column": "B",
                "seatStatus": "F",
                "seatCharacteristics": [
                  "M",
                  "L",
                  "E"
                ],
                "price": 26.42,
                "currency": "USD",
                "vendorPrice": 26.42,
                "vendorCurrency": "USD",
                "productCode": "SCI_SEAT_5B_W6_BUD_FCO"
              },
              {
                "column": "C",
                "seatStatus": "F",
                "seatCharacteristics": [
                  "A",
                  "L",
                  "E"
                ],
                "price": 25.53,
                "currency": "USD",
                "vendorPrice": 25.53,
                "vendorCurrency": "USD",
                "productCode": "SCI_SEAT_5C_W6_BUD_FCO"
              },
              {
                "column": "D",
                "seatStatus": "F",
                "seatCharacteristics": [
                  "W",
                  "L",
                  "E"
                ],
                "price": 22.75,
                "currency": "USD",
                "vendorPrice": 22.75,
                "vendorCurrency": "USD",
                "productCode": "SCI_SEAT_5D_W6_BUD_FCO"
              },
              {
                "column": "E",
                "seatStatus": "F",
                "seatCharacteristics": [
                  "M",
                  "L",
                  "E"
                ],
                "price": 68.06,
                "currency": "USD",
                "vendorPrice": 68.06,
                "vendorCurrency": "USD",
                "productCode": "SCI_SEAT_5E_W6_BUD_FCO"
              },
              {
                "column": "F",
                "seatStatus": "F",
                "seatCharacteristics": [
                  "A",
                  "L",
                  "E"
                ],
                "price": 29.83,
                "currency": "USD",
                "vendorPrice": 29.83,
                "vendorCurrency": "USD",
                "productCode": "SCI_SEAT_5F_W6_BUD_FCO"
              }
            ]
          }
        ]
      }
    }
  ],
  "status": 0,
  "msg": "success"
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
|» status|[SeatAvailabilityResponseStatus](#schemaseatavailabilityresponsestatus)|true|none||- 214: Session ID invalid or expired.<br />- 215: Segment index missing.<br />- 216: Seat selection failed.<br />- 217: Unknown error.<br />- 218: The airline don’t support seat selection currently.<br />- 219: The route don’t support seat selection currently.<br />- 220: illegal request parameter.<br />- 221: Fare family is empty and not configured with lowest price fare family.<br />- 223: The ratio of seat quotation requests to payment orders has exceeded the allowed threshold.|
|» msg|[ResponseMessage](#schemaresponsemessage)¦null|false|none||It serves as an additional description of the response result. Especially when the interface reports an error (`status` !=`0`), it is usually a human-readable error message. Note: Do not use this field in any programming scenarios. For example, do not judge whether the interface responds successfully based on this field. Instead, you should only determine it by checking whether the status is equal to`0`at any time.|
|» cabins|[object]¦null|false|none||An array containing all cabins and the seat layouts within them.|
|»» segmentIndex|integer|true|none||The segment index to which the cabin belongs|
|»» cabin|object|true|none||An object used to describe the seat layout within a cabin.|
|»»» deck|string¦null|false|none||Main deck or upper deck above that, which is found on some large aircraft.|
|»»» cabinClass|[CabinClass](#schemacabinclass)¦null|false|none||Service grade of the fare|
|»»» cabinLayout|object|true|none||Used to describe the seat layout of the cabin.|
|»»»» columns|[object]|true|none||Contains columns and seat information for seat display purposes. Returns the characteristics for each column. Provided in the order from left to right.|
|»»»»» designator|string|true|none||A letter used to uniquely identify the seat position in the column.<br />**Typical values:** A,B,C,D,E,F|
|»»»»» characteristics|string¦null|false|none||characteristics of column:<br />-`A`: column by the aisle<br />-`M`: middle column<br />-`W`: column by the window|
|»»»» rows|object|true|none||Contains rows and seat information for seat display purposes Returns the starting end row position for each column|
|»»»»» first|integer|true|none||First-row number Row starting row position for columns A,B,C,D,E,F|
|»»»»» last|integer|true|none||Last row number Row ending row position for columns A,B,C,D,E,F|
|»»»» exitRowPositions|[object]¦null|false|none||Return the position of exit rows, if applicable. The row number generally starts from 1 and increases from the front to the tail of the aircraft, that is, the seats close to the cockpit (nose) have the smallest row numbers, and the closer to the tail, the larger the row numbers.|
|»»»»» first|integer|true|none||Exit seat starting row position|
|»»»»» last|integer|true|none||Exit seat ending row position|
|»»» rows|[object]|true|none||A list of rows in this cabin. A cabin row has one or more seats.|
|»»»» number|integer|true|none||Seat row number|
|»»»» seats|[object]|true|none||A list of seats that make up this row|
|»»»»» column|string|true|none||The column where the seat is located|
|»»»»» seatStatus|string|true|none||A flag used to indicate whether a seat is free or occupied.<br />- F: Free<br />- O: Occupied|
|»»»»» seatCharacteristics|[string]¦null|false|none||A list contains seat characteristics, typical values(but not limited to):<br />-`A`: Aisle seat<br />-`E`: Exit and emergency exit<br />-`I`: Seat suitable for adult with an infant<br />-`IE`: Seat not suitable for child<br />-`L`: Leg space seat<br />-`U`: Seat suitable for unaccompanied minors<br />-`V`: Seat to be left vacant or offered last<br />-`W`: Window seat<br /><br />For more information, please refer to: [EDIFACT Standards for Seat Characteristics (9825)](https://support.travelport.com/webhelp/GWS/Content/XML_Select_Web_Service/Codes/edifact_standards_for_seating.htm).|
|»»»»» price|number|true|none||The total price of the seat, including taxes|
|»»»»» currency|string|true|none||Currency of the price.|
|»»»»» vendorPrice|number¦null|false|none||The total price in vendor's currency of the seat, including taxes|
|»»»»» vendorCurrency|string¦null|false|none||Vendor's currency|
|»»»»» productCode|string|true|none||A code used to uniquely identify this seat, which needs to be used when submitting a seat selection request.|
|»»»»» displayCurrency|number¦null|false|none||Display currency|
|»»»»» displayPrice|number¦null|false|none||The total price in display currency of the seat, including taxes|

#### 枚举值

|属性|值|
|---|---|
|status|214|
|status|215|
|status|216|
|status|217|
|status|218|
|status|219|
|status|220|
|status|221|
|status|223|
|deck|Main|
|deck|Upper deck|
|cabinClass|1|
|cabinClass|2|
|cabinClass|3|
|cabinClass|4|
|seatStatus|F|
|seatStatus|O|

## POST Get Luggage

POST /getLuggage.do

> In a booking process, please call the 'getLuggage' API to get precise baggage quotes after price verification via 'verify' or 'getOffer'.
> Steps:
> 1. API sequence
>    * Search - Verify- getLuggage - Order - Pay
>    * getOffer - getLuggage - Order - Pay
> 2. For exact baggage prices, request 'getLuggage'.
> 3. Pass 'offerId' in 'getLuggage' requests:
>    * From 'verify': Use sessionId as offerId
>    * From 'getOffer': Use its offerId directly.
> 4. 'getLuggage' returns all flight segments' baggage data, each identified by a unique productCode.
> 5. In the Order step, use the productCode to add specific baggage products to the ticket order.

**Endpoint:**
https://sandbox.atriptech.com/getLuggage.do

> Body 请求参数

```json
{
  "offerId": "o_d2c7d44baf2643ebac8b7926a8b0be60_1"
}
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|x-atlas-client-id|header|string| 是 |api access id|
|x-atlas-client-secret|header|string| 是 |api access secret|
|Accept-Encoding|header|string| 否 |建议设置该请求头，能很大程度地减小网络传输报文的大小|
|Accept|header|string| 是 |none|
|Content-Type|header|string| 是 |none|
|body|body|object| 否 |none|
|» offerId|body|string| 是 |The`sessionId`returned by verify api(`verify.do`)|
|» maxResponseTime|body|integer¦null| 否 |Query timeout, unit: milliseconds, default 5000ms.|

#### 详细说明

**» maxResponseTime**: Query timeout, unit: milliseconds, default 5000ms.
<br>
**Note:** Due to network transmission and computational performance impacts, the client may still receive a normal result (rather than a timeout) even if this duration is exceeded. This time is used to control the overall response time of the interface within a certain range, with an error generally not exceeding a few hundred milliseconds.<br>
If you have strict requirements for the timeout, it is recommended to set the timeout of your HTTP toolkit. If the HTTP toolkit you are using does not support this capability, you may need to leverage other tools—related capabilities are generally provided in most programming languages.

> 返回示例

> 200 Response

```json
{
  "status": 0,
  "msg": null,
  "data": {
    "offerId": "o_d2c7d44baf2643ebac8b7926a8b0be60_1",
    "ancillaryProductElements": [
      {
        "ancillaryCode": "SCI_BAG_5KG",
        "auxBaggageElement": {
          "allWeight": true,
          "piece": 0,
          "size": "",
          "weight": 5
        },
        "canPurchasePostTicket": 1,
        "canPurchaseWithTicket": 1,
        "categoryCode": "StandardCheckInBaggage",
        "clientTechnicalServiceFee": 0,
        "currency": "USD",
        "maxQty": 1,
        "minQty": 1,
        "price": 10.17,
        "productCode": "SCI_BAG_5KG",
        "segmentIndex": 1,
        "vendorCurrency": "IDR",
        "vendorPrice": 165000
      },
      {
        "ancillaryCode": "SCI_BAG_10KG",
        "auxBaggageElement": {
          "allWeight": true,
          "piece": 0,
          "size": "",
          "weight": 10
        },
        "canPurchasePostTicket": 1,
        "canPurchaseWithTicket": 1,
        "categoryCode": "StandardCheckInBaggage",
        "clientTechnicalServiceFee": 0,
        "currency": "USD",
        "maxQty": 1,
        "minQty": 1,
        "price": 16.34,
        "productCode": "SCI_BAG_10KG",
        "segmentIndex": 1,
        "vendorCurrency": "IDR",
        "vendorPrice": 265000
      },
      {
        "ancillaryCode": "SCI_BAG_30KG",
        "auxBaggageElement": {
          "allWeight": true,
          "piece": 0,
          "size": "",
          "weight": 30
        },
        "canPurchasePostTicket": 1,
        "canPurchaseWithTicket": 1,
        "categoryCode": "StandardCheckInBaggage",
        "clientTechnicalServiceFee": 0,
        "currency": "USD",
        "maxQty": 1,
        "minQty": 1,
        "price": 36.06,
        "productCode": "SCI_BAG_30KG",
        "segmentIndex": 1,
        "vendorCurrency": "IDR",
        "vendorPrice": 585000
      },
      {
        "ancillaryCode": "SCI_BAG_20KG",
        "auxBaggageElement": {
          "allWeight": true,
          "piece": 0,
          "size": "",
          "weight": 20
        },
        "canPurchasePostTicket": 1,
        "canPurchaseWithTicket": 1,
        "categoryCode": "StandardCheckInBaggage",
        "clientTechnicalServiceFee": 0,
        "currency": "USD",
        "maxQty": 1,
        "minQty": 1,
        "price": 24.35,
        "productCode": "SCI_BAG_20KG",
        "segmentIndex": 1,
        "vendorCurrency": "IDR",
        "vendorPrice": 395000
      },
      {
        "ancillaryCode": "SCI_BAG_40KG",
        "auxBaggageElement": {
          "allWeight": true,
          "piece": 0,
          "size": "",
          "weight": 40
        },
        "canPurchasePostTicket": 1,
        "canPurchaseWithTicket": 1,
        "categoryCode": "StandardCheckInBaggage",
        "clientTechnicalServiceFee": 0,
        "currency": "USD",
        "maxQty": 1,
        "minQty": 1,
        "price": 48.38,
        "productCode": "SCI_BAG_40KG",
        "segmentIndex": 1,
        "vendorCurrency": "IDR",
        "vendorPrice": 785000
      }
    ],
    "inboundSegments": [],
    "outboundSegments": [
      {
        "aircraftCode": "320",
        "arrAirport": "CGK",
        "arrTerminal": "",
        "arrTime": "202508231100",
        "cabin": "",
        "cabinClass": 1,
        "carrier": "QG",
        "codeShare": false,
        "depAirport": "SIN",
        "depTerminal": "",
        "depTime": "202508231010",
        "duration": 110,
        "fareFamily": "ECO",
        "flightNumber": "QG523",
        "operatingCarrier": "",
        "operatingFlightnumber": "",
        "seatCount": 9,
        "segmentIndex": 1,
        "stopCities": ""
      }
    ]
  }
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
|» status|integer|true|none||- 212: illegal parameter.<br />- 214: offer not exists.<br />- 205: timed out.<br />- 299: airline error.<br />- 9999: system error.|
|» msg|string¦null|false|none||As an additional description of the response result. Especially when the interface reports an error (status ≠ 0), it is usually a human-readable error message.<br /><br><br />**Note:** Do not use this field in any programming scenarios, such as judging whether the interface response is successful based on this field. You should always judge solely based on whether the status is equal to 0.|
|» data|object|true|none||none|
|»» offerId|string|true|none||none|
|»» outboundSegments|[[RoutingSegment](#schemaroutingsegment)]|true|none||none|
|»»» aircraftCode|string¦null|false|none||IATA Code of aircraft type|
|»»» arrAirport|string|true|none||3-letter iata code for the arrival airport at which the segment is scheduled to arrive.|
|»»» arrTerminal|string¦null|false|none||The terminal at the destination airport where the segment is scheduled to arrive.|
|»»» arrTime|string|true|none||The datetime at which the segment is scheduled to arrive, in the arrival airport timezone. The format is `YYYYMMDD`.|
|»»» cabin|string¦null|false|none||RBD(known as Reservation Booking Designator) displayed by the airline.|
|»»» cabinClass|[CabinClass](#schemacabinclass)|true|none||Cabin class of the segment.<br />- 1: economy<br />- 2: business<br />- 3: first<br />- 4: premium economy|
|»»» carrier|string|true|none||IATA code of marketing carrier.|
|»»» codeShare|boolean|true|none||A flag used to identify whether it is a code share flight.|
|»»» depAirport|string|true|none||3-letter iata code for the airport at which the segment is scheduled to depart.|
|»»» depTerminal|string¦null|false|none||The terminal at the departure airport from which the segment is scheduled to depart.|
|»»» depTime|string|true|none||The datetime at which the segment is scheduled to depart, in the departure airport timezone. The format is`YYYYMMSS`.|
|»»» duration|integer|true|none||The duration of the segment in munites.|
|»»» fareFamily|string|true|none||Fare Family as per the information received from the airline|
|»»» flightNumber|string|true|none||Marketing flight number. The format is: CA123 or TR021 or FR1290, with the first two letters representing the carrier and the following number representing the flight number.|
|»»» operatingCarrier|string¦null|false|none||2-letter iata code for the operating carrier. The airline actually operating this segment. This may differ from the marketing carrier in the case of a "codeshare", where one airline sells flights operated by another airline.|
|»»» operatingFlightnumber|string¦null|false|none||Operating flight number.|
|»»» seatCount|integer|true|none||Max booking seats for the fare.|
|»»» segmentIndex|integer|true|none||Segment sequence. Starts from 1. If it is return trip, sequence for outbound trip and inbound trip would be together. The segment index also represents the flight sequence of the segment.|
|»»» stopCities|string¦null|false|none||IATA code/Name of cities from where the passengers will take stopover flights. Include IATA code of cities and use a comma in case of multiple cities to separate transfer airports count is higher than 1. For example: `CGK, SUB`. <br />`null` or blank means non-stop flight.|
|»» inboundSegments|[[RoutingSegment](#schemaroutingsegment)]¦null|false|none||none|
|»»» aircraftCode|string¦null|false|none||IATA Code of aircraft type|
|»»» arrAirport|string|true|none||3-letter iata code for the arrival airport at which the segment is scheduled to arrive.|
|»»» arrTerminal|string¦null|false|none||The terminal at the destination airport where the segment is scheduled to arrive.|
|»»» arrTime|string|true|none||The datetime at which the segment is scheduled to arrive, in the arrival airport timezone. The format is `YYYYMMDD`.|
|»»» cabin|string¦null|false|none||RBD(known as Reservation Booking Designator) displayed by the airline.|
|»»» cabinClass|[CabinClass](#schemacabinclass)|true|none||Cabin class of the segment.<br />- 1: economy<br />- 2: business<br />- 3: first<br />- 4: premium economy|
|»»» carrier|string|true|none||IATA code of marketing carrier.|
|»»» codeShare|boolean|true|none||A flag used to identify whether it is a code share flight.|
|»»» depAirport|string|true|none||3-letter iata code for the airport at which the segment is scheduled to depart.|
|»»» depTerminal|string¦null|false|none||The terminal at the departure airport from which the segment is scheduled to depart.|
|»»» depTime|string|true|none||The datetime at which the segment is scheduled to depart, in the departure airport timezone. The format is`YYYYMMSS`.|
|»»» duration|integer|true|none||The duration of the segment in munites.|
|»»» fareFamily|string|true|none||Fare Family as per the information received from the airline|
|»»» flightNumber|string|true|none||Marketing flight number. The format is: CA123 or TR021 or FR1290, with the first two letters representing the carrier and the following number representing the flight number.|
|»»» operatingCarrier|string¦null|false|none||2-letter iata code for the operating carrier. The airline actually operating this segment. This may differ from the marketing carrier in the case of a "codeshare", where one airline sells flights operated by another airline.|
|»»» operatingFlightnumber|string¦null|false|none||Operating flight number.|
|»»» seatCount|integer|true|none||Max booking seats for the fare.|
|»»» segmentIndex|integer|true|none||Segment sequence. Starts from 1. If it is return trip, sequence for outbound trip and inbound trip would be together. The segment index also represents the flight sequence of the segment.|
|»»» stopCities|string¦null|false|none||IATA code/Name of cities from where the passengers will take stopover flights. Include IATA code of cities and use a comma in case of multiple cities to separate transfer airports count is higher than 1. For example: `CGK, SUB`. <br />`null` or blank means non-stop flight.|
|»» ancillaryProductElements|[[AncillaryProduct](#schemaancillaryproduct)]|true|none||none|
|»»» ancillaryCode|string|true|none||A code that is relatively readable by humans and contains information about auxiliary business specifications (such as weight and quantity limitations of luggage). <br />**Note:** <br />This content is only for display purposes and should not be used for programming purposes. That is to say, do not attempt to parse the information about auxiliary business specifications from this code. If you want to access the auxiliary business specifications, please use structured fields. For example, for luggage, please use`auxBaggageElement`.|
|»»» auxBaggageElement|object¦null|false|none||Baggage specification limitations. This node is valid only when the ancillary type (`categoryCode`) is baggage.|
|»»»» isAllWeight|boolean|true|none||Mark whether the`weight`field restricts the total weight or the weight of a single piece.<br />- `true`: The weight is for all the pieces<br />- `false`: The weight is for each piece|
|»»»» piece|integer|true|none||The maximum number of pieces that can be purchased per person.<br />- `0`: No Limitation about piece<br />- `>0`: Maximum pieces|
|»»»» size|string¦null|false|none||Maximum size for the baggage|
|»»»» weight|integer|true|none||The maximum weight that can be purchased per person.<br />- `0`: No limitation for weight<br />- `>0`: Weight limit (KG)|
|»»» canPurchasePostTicket|integer|true|none||A flag used to mark if this ancillary product can be purchased in the post-ticketing flow.<br />- `0`: No<br />- `1`: Yes|
|»»» canPurchaseWithTicket|integer|true|none||A flag used to mark if this ancillary product can be purchased during the booking flow.<br />- `0`: No<br />- `1`: Yes|
|»»» categoryCode|[AncillaryCategory](#schemaancillarycategory)|true|none||Type of the ancillary.<br /><br />- StandardCheckInBaggage: Standard Check-in Baggage.<br />- CabinBaggage: Usually refers to the Cabin Baggage Overhead Locker. Transition value. It will gradually transition to `CabinBaggageOverheadLocker`.<br />- CabinBaggageOverheadLocker: Cabin Baggage Overhead Locker.<br />- CabinBaggageUnderSeat: Cabin Baggage Under Seat. Usually refers to the personal item.|
|»»» clientTechnicalServiceFee|number¦null|false|none||The service fee charged by Atlas for the purchase of the ancillary.|
|»»» currency|string|true|none||The currency in which Atlas settles transactions with you|
|»»» maxQty|integer|true|none||The maximum number of purchases allowed per person per flight segment|
|»»» minQty|integer|true|none||The minimum quantity allowed to be purchased per person per flight segment.|
|»»» price|number|true|none||Price for this ancillary.|
|»»» productCode|string|true|none||Unique identifier for the ancillary product. It would be used in the order request.|
|»»» segmentIndex|integer|true|none||The index of segment the ancillary applies to.|
|»»» vendorCurrency|string|true|none||The currency in which the vendor charges for the ancillary. If the fare does not allow for the VCC pass-through or BYOA payment, this information will be`null`.|
|»»» vendorPrice|integer|true|none||The price charged by the vendor for the ancillary. If the fare does not allow for the VCC pass-through or BYOA payment, this information will be`null`.|

#### 枚举值

|属性|值|
|---|---|
|status|212|
|status|214|
|status|205|
|status|299|
|status|9999|
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

<h2 id="tocS_IfSeatOccupied">IfSeatOccupied</h2>

<a id="schemaifseatoccupied"></a>
<a id="schema_IfSeatOccupied"></a>
<a id="tocSifseatoccupied"></a>
<a id="tocsifseatoccupied"></a>

```json
"SIMILAR_SEAT"

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|string|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|SIMILAR_SEAT|
|*anonymous*|STOP_SEAT|
|*anonymous*|STOP_TICKET|

<h2 id="tocS_RefundRuleType">RefundRuleType</h2>

<a id="schemarefundruletype"></a>
<a id="schema_RefundRuleType"></a>
<a id="tocSrefundruletype"></a>
<a id="tocsrefundruletype"></a>

```json
"0"

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|string|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|0|
|*anonymous*|1|
|*anonymous*|2|

<h2 id="tocS_RefundMethod">RefundMethod</h2>

<a id="schemarefundmethod"></a>
<a id="schema_RefundMethod"></a>
<a id="tocSrefundmethod"></a>
<a id="tocsrefundmethod"></a>

```json
"CashBackToOriginalPayment"

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|string|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|CashBackToOriginalPayment|
|*anonymous*|Voucher|

<h2 id="tocS_OrderCommitResponseStatus">OrderCommitResponseStatus</h2>

<a id="schemaordercommitresponsestatus"></a>
<a id="schema_OrderCommitResponseStatus"></a>
<a id="tocSordercommitresponsestatus"></a>
<a id="tocsordercommitresponsestatus"></a>

```json
307

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|integer|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|307|
|*anonymous*|800|
|*anonymous*|316|
|*anonymous*|317|

<h2 id="tocS_SearchResponseStatus">SearchResponseStatus</h2>

<a id="schemasearchresponsestatus"></a>
<a id="schema_SearchResponseStatus"></a>
<a id="tocSsearchresponsestatus"></a>
<a id="tocssearchresponsestatus"></a>

```json
100

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|integer|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|100|
|*anonymous*|101|
|*anonymous*|102|
|*anonymous*|105|
|*anonymous*|106|
|*anonymous*|107|
|*anonymous*|108|
|*anonymous*|109|
|*anonymous*|110|
|*anonymous*|111|
|*anonymous*|112|
|*anonymous*|113|
|*anonymous*|114|
|*anonymous*|116|
|*anonymous*|123|
|*anonymous*|124|
|*anonymous*|126|
|*anonymous*|900|
|*anonymous*|9999|

<h2 id="tocS_VerifyResponseStatus">VerifyResponseStatus</h2>

<a id="schemaverifyresponsestatus"></a>
<a id="schema_VerifyResponseStatus"></a>
<a id="tocSverifyresponsestatus"></a>
<a id="tocsverifyresponsestatus"></a>

```json
200

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|integer|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|200|
|*anonymous*|201|
|*anonymous*|202|
|*anonymous*|203|
|*anonymous*|205|
|*anonymous*|207|
|*anonymous*|210|
|*anonymous*|212|
|*anonymous*|213|
|*anonymous*|222|
|*anonymous*|299|

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

<h2 id="tocS_PaymentResponseStatus">PaymentResponseStatus</h2>

<a id="schemapaymentresponsestatus"></a>
<a id="schema_PaymentResponseStatus"></a>
<a id="tocSpaymentresponsestatus"></a>
<a id="tocspaymentresponsestatus"></a>

```json
400

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|integer|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|400|
|*anonymous*|401|
|*anonymous*|402|
|*anonymous*|403|
|*anonymous*|404|
|*anonymous*|406|
|*anonymous*|407|
|*anonymous*|408|
|*anonymous*|409|
|*anonymous*|410|
|*anonymous*|411|
|*anonymous*|412|
|*anonymous*|413|
|*anonymous*|414|
|*anonymous*|415|

<h2 id="tocS_RetrieveBookingResponseStatus">RetrieveBookingResponseStatus</h2>

<a id="schemaretrievebookingresponsestatus"></a>
<a id="schema_RetrieveBookingResponseStatus"></a>
<a id="tocSretrievebookingresponsestatus"></a>
<a id="tocsretrievebookingresponsestatus"></a>

```json
800

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|integer|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|800|
|*anonymous*|701|
|*anonymous*|702|
|*anonymous*|703|
|*anonymous*|704|
|*anonymous*|705|

<h2 id="tocS_SeatAvailabilityResponseStatus">SeatAvailabilityResponseStatus</h2>

<a id="schemaseatavailabilityresponsestatus"></a>
<a id="schema_SeatAvailabilityResponseStatus"></a>
<a id="tocSseatavailabilityresponsestatus"></a>
<a id="tocsseatavailabilityresponsestatus"></a>

```json
214

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|integer|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|214|
|*anonymous*|215|
|*anonymous*|216|
|*anonymous*|217|
|*anonymous*|218|
|*anonymous*|219|
|*anonymous*|220|
|*anonymous*|221|
|*anonymous*|223|

<h2 id="tocS_SeatMapFlight">SeatMapFlight</h2>

<a id="schemaseatmapflight"></a>
<a id="schema_SeatMapFlight"></a>
<a id="tocSseatmapflight"></a>
<a id="tocsseatmapflight"></a>

```json
{
  "segmentIndex": 1,
  "flightNumber": "W62340",
  "depAirport": "LON",
  "arrAirport": "PAR",
  "depTime": "202510101630",
  "cabinClass": 1
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|segmentIndex|integer|true|none||This is the segment number, which starts from 1 and increments in the order of takeoff of each segment.|
|flightNumber|string|true|none||Marketing flight number(with airline code prefix).|
|depAirport|string|true|none||3-letter iata code for the airport at which the segment is scheduled to depart.|
|arrAirport|string|true|none||3-letter iata code for the arrival airport at which the segment is scheduled to arrive.|
|depTime|string|true|none||The datetime at which the segment is scheduled to depart, in the departure airport timezone. The format is`YYYYMMDD`.|
|cabinClass|[CabinClass](#schemacabinclass)|true|none||Cabin class.<br />- 1: economy<br />- 2: business<br />- 3: first<br />- 4: premium economy|

<h2 id="tocS_UniqueSellingSegment">UniqueSellingSegment</h2>

<a id="schemauniquesellingsegment"></a>
<a id="schema_UniqueSellingSegment"></a>
<a id="tocSuniquesellingsegment"></a>
<a id="tocsuniquesellingsegment"></a>

```json
{
  "carrier": "U2",
  "departureAirport": "LON",
  "arrivalAirport": "PAR",
  "flightNumber": "673",
  "departureDate": "20250301"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|carrier|string|true|none||IATA two letter code of marketing carrier, case sensitive|
|departureAirport|string|true|none||IATA three letter code of departure airport which is case sensitive. If the value is illegal, the system will prompt that the airport does not exist.|
|arrivalAirport|string|true|none||IATA three letter code of arrival airport which is case sensitive. If the value is illegal, the system will prompt that the airport does not exist.|
|flightNumber|string|true|none||Marketing flight number. Attention: Without airline code prefix. It should be noted that some users may enter flight numbers with or without zero padding, for example, you may enter 06 (or 6), but the airline may be 6 (or 06). Anyway, we will return to the user based on the actual flight number provided by the airline, and the user may need to handle the differences between request and response.|
|departureDate|string(date)|true|none||Departure date. Format: yyyyMMdd. We do not require users to specify departure times, nor do we want to return segments based on specific departure time. Considering that the externally transmitted time may not match the actual flight segment time on the supplier's (airline's) side, this can lead to search results being lost. Therefore, we will return the results of all flight segments that took off within the specified date, and it will be up to the user to decide how to use them.|

<h2 id="tocS_Offer">Offer</h2>

<a id="schemaoffer"></a>
<a id="schema_Offer"></a>
<a id="tocSoffer"></a>
<a id="tocsoffer"></a>

```json
{
  "offerID": "string",
  "offerToken": "string",
  "paxFares": [
    {
      "paxType": "ADT",
      "price": {
        "baseAmount": 100,
        "taxes": 0,
        "currency": "USD"
      }
    }
  ],
  "penalties": [
    {
      "journeyRefIDs": [
        "string"
      ],
      "amount": 0,
      "currency": "USD",
      "rule": {
        "type": "Refund",
        "paxTypes": [
          "ADT"
        ],
        "levelType": "Partial",
        "effectiveMinutes": 0,
        "expirationMinutes": 0,
        "fixedAmount": 0,
        "airlineFee": 0,
        "currency": "USD",
        "percent": 0.2,
        "percentBase": "fare"
      }
    }
  ],
  "services": [
    {
      "serviceID": "string",
      "segmentRefIDs": [
        "string"
      ],
      "type": "Baggage",
      "level": "Chargeable",
      "paxTypes": [
        "ADT"
      ],
      "metadata": {
        "type": "[",
        "maximumWeight": 20,
        "maximumPiece": 1,
        "maximumDimension": "L+W+H<=158cm"
      }
    }
  ],
  "outboundJourney": {
    "journeyID": "string",
    "segments": [
      {
        "segmentID": "string",
        "carrier": "string",
        "flightNumber": "string",
        "operatingCarrier": "string",
        "operatingFlightNumber": "string",
        "duration": 0,
        "legs": [
          {
            "departureAirport": null,
            "departureTime": null,
            "departureTerminal": null,
            "arrivalAirport": null,
            "arrivalTime": null,
            "arrivalTerminal": null,
            "aircraftType": null
          }
        ],
        "fareFamily": "string",
        "RBD": "string",
        "cabinClass": "Economy",
        "seatsLeft": 0
      }
    ]
  },
  "inboundJourney": {
    "journeyID": "string",
    "segments": [
      {
        "segmentID": "string",
        "carrier": "string",
        "flightNumber": "string",
        "operatingCarrier": "string",
        "operatingFlightNumber": "string",
        "duration": 0,
        "legs": [
          {
            "departureAirport": null,
            "departureTime": null,
            "departureTerminal": null,
            "arrivalAirport": null,
            "arrivalTime": null,
            "arrivalTerminal": null,
            "aircraftType": null
          }
        ],
        "fareFamily": "string",
        "RBD": "string",
        "cabinClass": "Economy",
        "seatsLeft": 0
      }
    ]
  },
  "terms": [
    {
      "carrier": "string",
      "URL": "string"
    }
  ]
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|offerID|string¦null|false|none||The unique ID for this offer, globally unique.|
|offerToken|[OfferToken](#schemaoffertoken)|false|none||A encrypted string containing complete flight information and related quotation information, which can be used to uniquely identify a complete itinerary. This content can be freely distributed and stored by users, but modification is not allowed. At the same time, this content has a certain validity period (generally not exceeding 6 hours). One use case of Offer Token is when users search for flight tickets and quotes through Atlas' caching system, and then use this information to perform real-time price verification in subsequent steps to confirm if there are any price changes. At this point, Atlas will directly query real-time quotes from the airline, rather than through caching.|
|paxFares|[[PaxFare](#schemapaxfare)]|true|none||Contains ticket prices and taxes corresponding to each passenger type. If there are no elements for certain passenger types in the list, it means that the ticket is not currently being sold for that passenger type.|
|penalties|[object]|true|none||none|
|» journeyRefIDs|[string]|true|none||The reference to the journey ID indicates the journey to which the rule applies, which may include references to multiple journey IDs (such as round trips), indicating that multiple journeys are applicable to the rule.|
|» amount|number|true|none||Pennalty amount. Unit: Yuan. Keep up to 2 decimal places.|
|» currency|string|true|none||Currency code corresponding to the pennalty amount, in capital letters. This currency may be different from the fare currency, depending on the airline.|
|» rule|object|true|none||Calculation rules for the penalty|
|»» type|string|true|none||Rule type: Refund or Change rule|
|»» paxTypes|[[PaxTypeEnums](#schemapaxtypeenums)]|true|none||There may be multiple types of passengers to which this rule applies|
|»» levelType|[FareRuleLevelEnums](#schemafarerulelevelenums)|true|none||- Full: If it is a refund, it means a full refund; If it is a rescheduling, it means free rescheduling<br />- Partial: If it is a refund, it means a partial refund; If it is a rescheduling, it means that there will be a fee for reschedulin<br />- None: If it is a refund, it means it cannot be refunded; If it is a rescheduling, it means that rescheduling is not possible|
|»» effectiveMinutes|integer|true|none||Form a time interval together with expiratorMinutes to indicate the time range within which the rule applies. This value serves as the starting point of the interval, measured in minutes. >= 0 represents the number of minutes before takeoff, <0 represents the number of minutes after takeoff.|
|»» expirationMinutes|integer|true|none||Form a time interval together with expirationMinutes to indicate the time range within which the rule applies. This value serves as the end point of the interval, measured in minutes. >=0 represents the number of minutes before takeoff, <0 represents the number of minutes after takeoff.|
|»» fixedAmount|number|true|none||Fixed deduction penalty. Unit: Yuan, with a maximum of 2 decimal places retained.|
|»» airlineFee|number|true|none||Fixed deduction of airline handling fees. Unit: Yuan, with a maximum of 2 decimal places retained.|
|»» currency|string|true|none||Currency of penalty and airline handling fees. This currency may be different from the fare currency, depending on the airline.|
|»» percent|number|true|none||Penalty percentage|
|»» percentBase|string|true|none||Penalty percentage base.<br />- fare+tax: The base for calculating the percentage is the total price including tax<br />- fare: It indicates that the penalty percentage is based on the base price, excluding tax|
|services|[[Service](#schemaservice)]¦null|false|none||Includes various free and chargeable services, including but not limited to: baggages, seat selection, meals, etc|
|outboundJourney|[Journey](#schemajourney)|true|none||none|
|inboundJourney|[Journey](#schemajourney)|false|none||Inbound journey, null means one-way.|
|terms|[[Term](#schematerm)]¦null|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|type|Refund|
|type|Change|
|percentBase|fare+tax|
|percentBase|fare|

<h2 id="tocS_PaxFare">PaxFare</h2>

<a id="schemapaxfare"></a>
<a id="schema_PaxFare"></a>
<a id="tocSpaxfare"></a>
<a id="tocspaxfare"></a>

```json
{
  "paxType": "ADT",
  "price": {
    "baseAmount": 100,
    "taxes": 0,
    "currency": "USD"
  }
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|paxType|[PaxTypeEnums](#schemapaxtypeenums)|true|none||Passenger type.<br />- ADT: Representing adults<br />- CHD: Representing children<br />- INF: Representing a baby|
|price|[Price](#schemaprice)|true|none||none|

<h2 id="tocS_OfferToken">OfferToken</h2>

<a id="schemaoffertoken"></a>
<a id="schema_OfferToken"></a>
<a id="tocSoffertoken"></a>
<a id="tocsoffertoken"></a>

```json
"string"

```

A encrypted string containing complete flight information and related quotation information, which can be used to uniquely identify a complete itinerary. This content can be freely distributed and stored by users, but modification is not allowed. At the same time, this content has a certain validity period (generally not exceeding 6 hours). One use case of Offer Token is when users search for flight tickets and quotes through Atlas' caching system, and then use this information to perform real-time price verification in subsequent steps to confirm if there are any price changes. At this point, Atlas will directly query real-time quotes from the airline, rather than through caching.

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|string¦null|false|none||A encrypted string containing complete flight information and related quotation information, which can be used to uniquely identify a complete itinerary. This content can be freely distributed and stored by users, but modification is not allowed. At the same time, this content has a certain validity period (generally not exceeding 6 hours). One use case of Offer Token is when users search for flight tickets and quotes through Atlas' caching system, and then use this information to perform real-time price verification in subsequent steps to confirm if there are any price changes. At this point, Atlas will directly query real-time quotes from the airline, rather than through caching.|

<h2 id="tocS_Price">Price</h2>

<a id="schemaprice"></a>
<a id="schema_Price"></a>
<a id="tocSprice"></a>
<a id="tocsprice"></a>

```json
{
  "baseAmount": 100,
  "taxes": 0,
  "currency": "USD"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|baseAmount|number|true|none||Basic price, excluding taxes. Unit: Yuan, with a maximum of 2 decimal places retained|
|taxes|number|true|none||Total taxes. Unit: Yuan, with a maximum of 2 decimal places retained|
|currency|string|true|none||Currency code, capitalized|

<h2 id="tocS_FareRule">FareRule</h2>

<a id="schemafarerule"></a>
<a id="schema_FareRule"></a>
<a id="tocSfarerule"></a>
<a id="tocsfarerule"></a>

```json
{
  "type": "Refund",
  "paxTypes": [
    "ADT"
  ],
  "levelType": "Partial",
  "effectiveMinutes": 0,
  "expirationMinutes": 0,
  "fixedAmount": 0,
  "airlineFee": 0,
  "currency": "USD",
  "percent": 0.2,
  "percentBase": "fare"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|type|string|true|none||Rule type: Refund or Change rule|
|paxTypes|[[PaxTypeEnums](#schemapaxtypeenums)]|true|none||There may be multiple types of passengers to which this rule applies|
|levelType|[FareRuleLevelEnums](#schemafarerulelevelenums)|true|none||- Full: If it is a refund, it means a full refund; If it is a rescheduling, it means free rescheduling<br />- Partial: If it is a refund, it means a partial refund; If it is a rescheduling, it means that there will be a fee for reschedulin<br />- None: If it is a refund, it means it cannot be refunded; If it is a rescheduling, it means that rescheduling is not possible|
|effectiveMinutes|integer|true|none||Form a time interval together with expiratorMinutes to indicate the time range within which the rule applies. This value serves as the starting point of the interval, measured in minutes. >= 0 represents the number of minutes before takeoff, <0 represents the number of minutes after takeoff.|
|expirationMinutes|integer|true|none||Form a time interval together with expirationMinutes to indicate the time range within which the rule applies. This value serves as the end point of the interval, measured in minutes. >=0 represents the number of minutes before takeoff, <0 represents the number of minutes after takeoff.|
|fixedAmount|number|true|none||Fixed deduction penalty. Unit: Yuan, with a maximum of 2 decimal places retained.|
|airlineFee|number|true|none||Fixed deduction of airline handling fees. Unit: Yuan, with a maximum of 2 decimal places retained.|
|currency|string|true|none||Currency of penalty and airline handling fees. This currency may be different from the fare currency, depending on the airline.|
|percent|number|true|none||Penalty percentage|
|percentBase|string|true|none||Penalty percentage base.<br />- fare+tax: The base for calculating the percentage is the total price including tax<br />- fare: It indicates that the penalty percentage is based on the base price, excluding tax|

#### 枚举值

|属性|值|
|---|---|
|type|Refund|
|type|Change|
|percentBase|fare+tax|
|percentBase|fare|

<h2 id="tocS_PaxTypeEnums">PaxTypeEnums</h2>

<a id="schemapaxtypeenums"></a>
<a id="schema_PaxTypeEnums"></a>
<a id="tocSpaxtypeenums"></a>
<a id="tocspaxtypeenums"></a>

```json
"ADT"

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|string|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|ADT|
|*anonymous*|CHD|
|*anonymous*|INF|

<h2 id="tocS_FareRuleLevelEnums">FareRuleLevelEnums</h2>

<a id="schemafarerulelevelenums"></a>
<a id="schema_FareRuleLevelEnums"></a>
<a id="tocSfarerulelevelenums"></a>
<a id="tocsfarerulelevelenums"></a>

```json
"Partial"

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|string|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|Full|
|*anonymous*|Partial|
|*anonymous*|None|

<h2 id="tocS_Service">Service</h2>

<a id="schemaservice"></a>
<a id="schema_Service"></a>
<a id="tocSservice"></a>
<a id="tocsservice"></a>

```json
{
  "serviceID": "string",
  "segmentRefIDs": [
    "string"
  ],
  "type": "Baggage",
  "level": "Chargeable",
  "paxTypes": [
    "ADT"
  ],
  "metadata": {
    "type": "StandardCheckInBaggage",
    "maximumWeight": 20,
    "maximumPiece": 1,
    "maximumDimension": "L+W+H<=158cm"
  }
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|serviceID|string|true|none||The unique ID of this service. Note: this ID is unique within the context of the current offer.|
|segmentRefIDs|[string]|true|none||The flight segment ID reference applicable to this service|
|type|[ServiceTypeEnums](#schemaservicetypeenums)|true|none||Service Type.<br />- Baggage: represent a package<br />- Seat: represent seat selection<br />- Meal: represent meals|
|level|[ServiceLevelEnums](#schemaservicelevelenums)|true|none||Service fee level.<br />- Free: Free service<br />- Partial: Partially Free<br />- Chargeable: Chargeable|
|paxTypes|[[PaxTypeEnums](#schemapaxtypeenums)]|true|none||There may be multiple types of passengers for which this service is applicable. The items are one of:<br />- ADT: Representing adults<br />- CHD: Representing children<br />- INF: Representing a baby|
|metadata|[BaggageAllowance](#schemabaggageallowance)|false|none||Metadata representing different services, such as package weight, quantity, size, and other restrictions. Note: The content of this node may vary depending on the type of service. Users should read the content of the node according to different service types.|

<h2 id="tocS_ServiceTypeEnums">ServiceTypeEnums</h2>

<a id="schemaservicetypeenums"></a>
<a id="schema_ServiceTypeEnums"></a>
<a id="tocSservicetypeenums"></a>
<a id="tocsservicetypeenums"></a>

```json
"Baggage"

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|string|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|Baggage|
|*anonymous*|Seat|
|*anonymous*|Meal|

<h2 id="tocS_ServiceLevelEnums">ServiceLevelEnums</h2>

<a id="schemaservicelevelenums"></a>
<a id="schema_ServiceLevelEnums"></a>
<a id="tocSservicelevelenums"></a>
<a id="tocsservicelevelenums"></a>

```json
"Chargeable"

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|string|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|Free|
|*anonymous*|Partial|
|*anonymous*|Chargeable|

<h2 id="tocS_Segment">Segment</h2>

<a id="schemasegment"></a>
<a id="schema_Segment"></a>
<a id="tocSsegment"></a>
<a id="tocssegment"></a>

```json
{
  "segmentID": "string",
  "carrier": "string",
  "flightNumber": "string",
  "operatingCarrier": "string",
  "operatingFlightNumber": "string",
  "duration": 0,
  "legs": [
    {
      "departureAirport": "string",
      "departureTime": "202503011100",
      "departureTerminal": "string",
      "arrivalAirport": "string",
      "arrivalTime": "string",
      "arrivalTerminal": "string",
      "aircraftType": "string"
    }
  ],
  "fareFamily": "string",
  "RBD": "string",
  "cabinClass": "Economy",
  "seatsLeft": 0
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|segmentID|string|true|none||Unique ID for the flight segment. Note: This ID is unique within the context of the current offer.|
|carrier|string|true|none||Marketing carrier IATA two letter code, capitalized.|
|flightNumber|string|true|none||Marketing flight number. Attention: Do not include airline code prefix.|
|operatingCarrier|string¦null|false|none||Operating carrier IATA two letter code, capitalized.|
|operatingFlightNumber|string¦null|false|none||Operating flight number. Attention: Do not include airline code prefix.|
|duration|integer¦null|false|none||Representing the flight duration of the entire flight segment, in minutes|
|legs|[[Leg](#schemaleg)]|true|none||The physical flight information that constitutes the flight segment and the stopover information can be obtained from this. The number of elements=1 indicates that there is no stopping point. Display in flight order.|
|fareFamily|string¦null|false|none||none|
|RBD|string¦null|false|none||none|
|cabinClass|[CabinClassEnums](#schemacabinclassenums)|false|none||仓等|
|seatsLeft|integer|false|none||the number of remaining seats|

<h2 id="tocS_Leg">Leg</h2>

<a id="schemaleg"></a>
<a id="schema_Leg"></a>
<a id="tocSleg"></a>
<a id="tocsleg"></a>

```json
{
  "departureAirport": "string",
  "departureTime": "202503011100",
  "departureTerminal": "string",
  "arrivalAirport": "string",
  "arrivalTime": "string",
  "arrivalTerminal": "string",
  "aircraftType": "string"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|departureAirport|string|true|none||IATA two letter code for the departure airport, in capital letters|
|departureTime|string(date-time)¦null|false|none||Takeoff time, format: yyyyMMddHHmm. For those taking off from transit points, the departure time may not be available; For those taking off from the starting point, this time will definitely be available.|
|departureTerminal|string¦null|false|none||Departure terminal.|
|arrivalAirport|string|true|none||IATA two letter code upon arrival at the airport, in capital letters|
|arrivalTime|string¦null|false|none||Arrival time, format: yyyyMMddHHmm. For those arriving as transit points, the arrival time may not be available; For those who arrive as the endpoint, there will definitely be an arrival time.|
|arrivalTerminal|string¦null|false|none||Arriving terminal.|
|aircraftType|string¦null|false|none||Aircraft type code. According to the actual display of the airline.|

<h2 id="tocS_CabinClassEnums">CabinClassEnums</h2>

<a id="schemacabinclassenums"></a>
<a id="schema_CabinClassEnums"></a>
<a id="tocScabinclassenums"></a>
<a id="tocscabinclassenums"></a>

```json
"Economy"

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|string|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|Economy|
|*anonymous*|Business|
|*anonymous*|First|
|*anonymous*|PremiumEconomy|

<h2 id="tocS_Term">Term</h2>

<a id="schematerm"></a>
<a id="schema_Term"></a>
<a id="tocSterm"></a>
<a id="tocsterm"></a>

```json
{
  "carrier": "string",
  "URL": "string"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|carrier|string|true|none||Marketing carrier IATA two letter code, capitalize|
|URL|string|true|none||terms and condition link|

<h2 id="tocS_ServiceFee">ServiceFee</h2>

<a id="schemaservicefee"></a>
<a id="schema_ServiceFee"></a>
<a id="tocSservicefee"></a>
<a id="tocsservicefee"></a>

```json
{
  "amountPerUnit": 0,
  "unit": "PER_PAX",
  "currency": "USD"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|amountPerUnit|number|true|none||Unit amount, unit: yuan, with a maximum of 2 decimal places retained|
|unit|[ServiceFeeModeEnums](#schemaservicefeemodeenums)|true|none||Amount unit.<br />- PER_SEGMENT: Calculated per flight segment<br />- PER_PAX: Calculated per passenger<br />- PER_BOOKING: Calculated per order|
|currency|string|true|none||Currency code for the amount, in capital letters|

<h2 id="tocS_ServiceFeeModeEnums">ServiceFeeModeEnums</h2>

<a id="schemaservicefeemodeenums"></a>
<a id="schema_ServiceFeeModeEnums"></a>
<a id="tocSservicefeemodeenums"></a>
<a id="tocsservicefeemodeenums"></a>

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
|*anonymous*|PER_PAX|
|*anonymous*|PER_BOOKING|

<h2 id="tocS_BookingRequirementSchema">BookingRequirementSchema</h2>

<a id="schemabookingrequirementschema"></a>
<a id="schema_BookingRequirementSchema"></a>
<a id="tocSbookingrequirementschema"></a>
<a id="tocsbookingrequirementschema"></a>

```json
{
  "passenger": {
    "name": {
      "type": "string",
      "required": true,
      "description": "string",
      "maxLength": "string"
    },
    "passengerType": {
      "type": "string",
      "required": true,
      "description": "string",
      "maxLength": "string"
    },
    "birthday": {
      "type": "string",
      "required": true,
      "description": "string",
      "maxLength": "string"
    },
    "gender": {
      "type": "string",
      "required": true,
      "description": "string",
      "maxLength": "string"
    },
    "nationality": {
      "type": "string",
      "required": true,
      "description": "string",
      "maxLength": "string"
    },
    "cardType": {
      "type": "string",
      "required": true,
      "description": "string",
      "maxLength": "string"
    },
    "cardNum": {
      "type": "string",
      "required": true,
      "description": "string",
      "maxLength": "string"
    },
    "cardIssuePlace": {
      "type": "string",
      "required": true,
      "description": "string",
      "maxLength": "string"
    },
    "cardExpired": {
      "type": "string",
      "required": true,
      "description": "string",
      "maxLength": "string"
    }
  }
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|passenger|[PaxConstraint](#schemapaxconstraint)|true|none||Specific requirements for passenger information|

<h2 id="tocS_PaymentMethodEnums">PaymentMethodEnums</h2>

<a id="schemapaymentmethodenums"></a>
<a id="schema_PaymentMethodEnums"></a>
<a id="tocSpaymentmethodenums"></a>
<a id="tocspaymentmethodenums"></a>

```json
"Deposit"

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|string|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|Deposit|
|*anonymous*|VCC_Passthrough|
|*anonymous*|BYOA|
|*anonymous*|MoR|

<h2 id="tocS_ApiResponse">ApiResponse</h2>

<a id="schemaapiresponse"></a>
<a id="schema_ApiResponse"></a>
<a id="tocSapiresponse"></a>
<a id="tocsapiresponse"></a>

```json
{
  "status": 0,
  "msg": "string"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|status|integer|true|none||An identifier indicating whether the interface has responded successfully. It represents success if and only if the value is 0. Other values represent different error scenarios, with specific reference to the error codes listed in different APIs.|
|msg|string¦null|false|none||As an additional description of the response result. Especially when the interface reports an error (status ≠ 0), it is usually a human-readable error message.<br /><br><br />**Note:** Do not use this field in any programming scenarios, such as judging whether the interface response is successful based on this field. You should always judge solely based on whether the status is equal to 0.|

<h2 id="tocS_BaggageAllowance">BaggageAllowance</h2>

<a id="schemabaggageallowance"></a>
<a id="schema_BaggageAllowance"></a>
<a id="tocSbaggageallowance"></a>
<a id="tocsbaggageallowance"></a>

```json
{
  "type": "StandardCheckInBaggage",
  "maximumWeight": 20,
  "maximumPiece": 1,
  "maximumDimension": "L+W+H<=158cm"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|type|[BaggageTypeEnums](#schemabaggagetypeenums)|true|none||Type of baggage|
|maximumWeight|integer|true|none||Maximum weight limit.<br />- `0`: No Free baggage<br />- `-1`: No limitation on weight<br />- `>0`: Maximum weight|
|maximumPiece|integer|true|none||Maximum quantity limit.<br />- `0`: No limitation<br />- `>0`: Maximum pieces|
|maximumDimension|string¦null|false|none||Maximum size limit. Note: This content is currently not guaranteed to be structured (parsed)|

<h2 id="tocS_BaggageTypeEnums">BaggageTypeEnums</h2>

<a id="schemabaggagetypeenums"></a>
<a id="schema_BaggageTypeEnums"></a>
<a id="tocSbaggagetypeenums"></a>
<a id="tocsbaggagetypeenums"></a>

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
|*anonymous*|CabinBaggageOverheadLocker|
|*anonymous*|CabinBaggageUnderSeat|

<h2 id="tocS_Journey">Journey</h2>

<a id="schemajourney"></a>
<a id="schema_Journey"></a>
<a id="tocSjourney"></a>
<a id="tocsjourney"></a>

```json
{
  "journeyID": "string",
  "segments": [
    {
      "segmentID": "string",
      "carrier": "string",
      "flightNumber": "string",
      "operatingCarrier": "string",
      "operatingFlightNumber": "string",
      "duration": 0,
      "legs": [
        {
          "departureAirport": "string",
          "departureTime": "202503011100",
          "departureTerminal": "string",
          "arrivalAirport": "string",
          "arrivalTime": "string",
          "arrivalTerminal": "string",
          "aircraftType": "string"
        }
      ],
      "fareFamily": "string",
      "RBD": "string",
      "cabinClass": "Economy",
      "seatsLeft": 0
    }
  ]
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|journeyID|string|true|none||Unique ID for the itinerary. Note: the ID is unique within the context of the current offer.|
|segments|[[Segment](#schemasegment)]|true|none||Display flight segments in flight order|

<h2 id="tocS_Constraint">Constraint</h2>

<a id="schemaconstraint"></a>
<a id="schema_Constraint"></a>
<a id="tocSconstraint"></a>
<a id="tocsconstraint"></a>

```json
{
  "type": "string",
  "required": true,
  "description": "string",
  "maxLength": "string"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|type|string|true|none||Data type|
|required|boolean|true|none||Required or not|
|description|string|false|none||none|
|maxLength|string|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|type|string|
|type|int|

<h2 id="tocS_PaxConstraint">PaxConstraint</h2>

<a id="schemapaxconstraint"></a>
<a id="schema_PaxConstraint"></a>
<a id="tocSpaxconstraint"></a>
<a id="tocspaxconstraint"></a>

```json
{
  "name": {
    "type": "string",
    "required": true,
    "description": "string",
    "maxLength": "string"
  },
  "passengerType": {
    "type": "string",
    "required": true,
    "description": "string",
    "maxLength": "string"
  },
  "birthday": {
    "type": "string",
    "required": true,
    "description": "string",
    "maxLength": "string"
  },
  "gender": {
    "type": "string",
    "required": true,
    "description": "string",
    "maxLength": "string"
  },
  "nationality": {
    "type": "string",
    "required": true,
    "description": "string",
    "maxLength": "string"
  },
  "cardType": {
    "type": "string",
    "required": true,
    "description": "string",
    "maxLength": "string"
  },
  "cardNum": {
    "type": "string",
    "required": true,
    "description": "string",
    "maxLength": "string"
  },
  "cardIssuePlace": {
    "type": "string",
    "required": true,
    "description": "string",
    "maxLength": "string"
  },
  "cardExpired": {
    "type": "string",
    "required": true,
    "description": "string",
    "maxLength": "string"
  }
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|name|[Constraint](#schemaconstraint)|true|none||none|
|passengerType|[Constraint](#schemaconstraint)|true|none||none|
|birthday|[Constraint](#schemaconstraint)|true|none||none|
|gender|[Constraint](#schemaconstraint)|true|none||none|
|nationality|[Constraint](#schemaconstraint)|true|none||none|
|cardType|[Constraint](#schemaconstraint)|true|none||none|
|cardNum|[Constraint](#schemaconstraint)|true|none||none|
|cardIssuePlace|[Constraint](#schemaconstraint)|true|none||none|
|cardExpired|[Constraint](#schemaconstraint)|true|none||none|

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

<h2 id="tocS_BookingRequirement">BookingRequirement</h2>

<a id="schemabookingrequirement"></a>
<a id="schema_BookingRequirement"></a>
<a id="tocSbookingrequirement"></a>
<a id="tocsbookingrequirement"></a>

```json
{
  "passenger": {
    "birthday": {
      "required": true
    },
    "cardIssuePlace": {
      "required": true
    },
    "cardNum": {
      "required": true
    },
    "passengerType": {
      "required": true
    },
    "gender": {
      "required": true
    },
    "nationality": {
      "required": true
    },
    "cardExpired": {
      "required": true
    },
    "name": {
      "required": true
    },
    "cardType": {
      "required": true
    }
  }
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|passenger|object|true|none||Passenger information requirements|
|» birthday|[BookingRequirementConstraint](#schemabookingrequirementconstraint)|true|none||Requirements for birthday.|
|» cardIssuePlace|[BookingRequirementConstraint](#schemabookingrequirementconstraint)|true|none||Requirements for the country where the identity document is issued.|
|» cardNum|[BookingRequirementConstraint](#schemabookingrequirementconstraint)|true|none||Requirements for the number of identity document.|
|» passengerType|[BookingRequirementConstraint](#schemabookingrequirementconstraint)|true|none||Requirements for the type of passenger(Adult, Child, Infant).|
|» gender|[BookingRequirementConstraint](#schemabookingrequirementconstraint)|true|none||Requirements for passenger's gender|
|» nationality|[BookingRequirementConstraint](#schemabookingrequirementconstraint)|true|none||Requirements for passenger's nationality|
|» cardExpired|[BookingRequirementConstraint](#schemabookingrequirementconstraint)|true|none||Requirements for the expiration date of identity document|
|» name|[BookingRequirementConstraint](#schemabookingrequirementconstraint)|true|none||Requirements for passenger's name|
|» cardType|[BookingRequirementConstraint](#schemabookingrequirementconstraint)|true|none||Requirements for the type of identity document.|

<h2 id="tocS_BookingRequirementConstraint">BookingRequirementConstraint</h2>

<a id="schemabookingrequirementconstraint"></a>
<a id="schema_BookingRequirementConstraint"></a>
<a id="tocSbookingrequirementconstraint"></a>
<a id="tocsbookingrequirementconstraint"></a>

```json
{
  "required": true
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|required|boolean|true|none||Required or not|

<h2 id="tocS_RequestSource">RequestSource</h2>

<a id="schemarequestsource"></a>
<a id="schema_RequestSource"></a>
<a id="tocSrequestsource"></a>
<a id="tocsrequestsource"></a>

```json
"string"

```

The tag to identify which channel does this traffic come from. For example: SkyScanner,Google,Oganic search,etc…

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|string|false|none||The tag to identify which channel does this traffic come from. For example: SkyScanner,Google,Oganic search,etc…|

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

<h2 id="tocS_Contact">Contact</h2>

<a id="schemacontact"></a>
<a id="schema_Contact"></a>
<a id="tocScontact"></a>
<a id="tocscontact"></a>

```json
{
  "name": "string",
  "address": "string",
  "postcode": "string",
  "email": "string",
  "mobile": "string",
  "companyName": "string"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|name|string|true|none||Contact name, please follow this format: Family Name/Given Name. The contact name can only accept Latin letters, /, and spaces.|
|address|string¦null|false|none||Contact address.|
|postcode|string¦null|false|none||Contact post code.|
|email|string¦null|false|none||Contact email.|
|mobile|string¦null|false|none||Contact mobile, please follow this format : XXXX(digital country code)-XXXXXXXX(phone number), here're the examples: 0001-87291810, 0086-13928109091, 0971-19201998|
|companyName|string¦null|false|none||Company name.|

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

<h2 id="tocS_TicketErrorCodes">TicketErrorCodes</h2>

<a id="schematicketerrorcodes"></a>
<a id="schema_TicketErrorCodes"></a>
<a id="tocSticketerrorcodes"></a>
<a id="tocsticketerrorcodes"></a>

```json
"601"

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|*anonymous*|string|false|none||none|

#### 枚举值

|属性|值|
|---|---|
|*anonymous*|601|
|*anonymous*|602|
|*anonymous*|603|
|*anonymous*|604|
|*anonymous*|605|
|*anonymous*|6051|
|*anonymous*|606|
|*anonymous*|607|
|*anonymous*|608|
|*anonymous*|609|
|*anonymous*|611|
|*anonymous*|613|
|*anonymous*|614|
|*anonymous*|615|
|*anonymous*|616|
|*anonymous*|617|
|*anonymous*|618|
|*anonymous*|619|
|*anonymous*|620|
|*anonymous*|621|
|*anonymous*|623|
|*anonymous*|624|
|*anonymous*|625|
|*anonymous*|626|
|*anonymous*|627|
|*anonymous*|628|
|*anonymous*|629|
|*anonymous*|630|
|*anonymous*|631|
|*anonymous*|632|
|*anonymous*|633|
|*anonymous*|634|
|*anonymous*|698|
|*anonymous*|699|

<h2 id="tocS_RefundRule">RefundRule</h2>

<a id="schemarefundrule"></a>
<a id="schema_RefundRule"></a>
<a id="tocSrefundrule"></a>
<a id="tocsrefundrule"></a>

```json
{
  "airline": "string",
  "ruleType": "0",
  "passengerType": "string",
  "penaltyAmount": 0,
  "penaltyPercent": 0,
  "penaltyPercentBase": "fare+tax",
  "airlineFee": 0,
  "taxRefundable": true,
  "fareRefundable": true,
  "refundableAncillaries": [
    "string"
  ],
  "startMinute": 0,
  "endMinute": 0,
  "refundMethod": "CashBackToOriginalPayment"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|airline|string|true|none||IATA code of the airline|
|ruleType|[RefundRuleType](#schemarefundruletype)|true|none||Type of refund rule|
|passengerType|string¦null|false|none||The passenger types(separated by`/`) to which the rule applies, .`null`means that it is applicable to all passenger types.<br />-`ADT`<br />-`CHD`<br />-`INF`|
|penaltyAmount|number|false|none||The absolute amount of the penalty|
|penaltyPercent|number|false|none||The percentage of the penalty|
|penaltyPercentBase|string|false|none||The percentage base of the penalty|
|airlineFee|number|false|none||Airline ticket refund fee|
|taxRefundable|boolean|true|none||Whether tax can be refunded|
|fareRefundable|boolean|true|none||Whether fare can be refunded|
|refundableAncillaries|[string]¦null|false|none||Ancillary service types that can be refunded together with the ticket.|
|startMinute|integer|true|none||Starting time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|endMinute|integer|true|none||Ending time of rule application. Positive numbers represent XXX minutes before departure. Negative numbers represent XXX minutes after departure.|
|refundMethod|[RefundMethod](#schemarefundmethod)|false|none||The method of fund refund|

#### 枚举值

|属性|值|
|---|---|
|penaltyPercentBase|fare+tax|
|penaltyPercentBase|fare|

<h2 id="tocS_SearchRequest">SearchRequest</h2>

<a id="schemasearchrequest"></a>
<a id="schema_SearchRequest"></a>
<a id="tocSsearchrequest"></a>
<a id="tocssearchrequest"></a>

```json
{
  "tripType": "1",
  "adultNum": 1,
  "childNum": 0,
  "infantNum": 0,
  "fromCity": "LON",
  "toCity": "PAR",
  "fromAirport": "AAA",
  "toAirport": "AAA",
  "fromDate": "20251010",
  "retDate": "2019-08-24",
  "airlines": [
    "string"
  ],
  "fromFlightNumbers": [
    "string"
  ],
  "retFlightNumbers": [
    "string"
  ],
  "includeMultipleFareFamily": false,
  "currency": "string",
  "displayCurrency": "string",
  "requestSource": "string"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|tripType|string|true|none||The trip type(1=one way or 2=round trip) you want to search|
|adultNum|integer|true|none||Adult passenger count. Please note that the total number of adults(`adultNum`) and children(`childNum`) cannot exceed 9.|
|childNum|integer|true|none||Child passenger count. Please note that the total number of adults(`adultNum`) and children(`childNum`) cannot exceed 9|
|infantNum|integer|true|none||Infant passenger count, no more than the number of adult|
|fromCity|string|true|none||IATA code of the departure city or airport (in capital letters).When the airport code you sent is different from the code of the city where the airport is located, we can recognize that it is an airport, otherwise we will treat it as a city code. We will filter flights based on your departure location type.|
|toCity|string|true|none||IATA code of the arrival city or airport (in capital letters).When the airport code you sent is different from the code of the city where the airport is located, we can recognize that it is an airport, otherwise we will treat it as a city code. We will filter flights based on your departure location type.|
|fromAirport|string¦null|false|none||IATA code of the departure airport|
|toAirport|string¦null|false|none||IATA code of the arrival airport|
|fromDate|string(date)|true|none||Departure date, the format is `YYYYMMDD`|
|retDate|string(date)¦null|false|none||Return date, the format is `YYYYMMDD`. If you are searching for round-trip, the return date is mandatory.|
|airlines|[string]¦null|false|none||An array of IATA Codes(in capital letters) of airlines. The result will only contain the airlines specified in the search request.|
|fromFlightNumbers|[string]¦null|false|none||Search for specified departure flights. Each element represents one flight. Connecting flight numbers are separated by "`,`" (comma). <br />**Example**:<br />- ["FR123"]: A direct flight<br />- ["FR456,FR789"]: A connecting flight<br />- ["FR123", "FR456,FR789"]: 2 flights, a direct flight and a connecting flight|
|retFlightNumbers|[string]¦null|false|none||Search for specified return flights. Each element represents one flight. Connecting flight numbers are separated by "`,`" (comma).|
|includeMultipleFareFamily|boolean¦null|false|none||Search only for the lowest fare or for the Fare Families. By default, each flight only returns the lowest fare, and each array element in the response represents: flight - lowest fare. If this parameter is turned on, each element of the search results will be a combination of flight and one of the fares, that is, different elements will have the same flight but different ticket fare.|
|currency|string¦null|false|none||This is the settlement currency. The 3-letter currency code should be entered. This field is optional, and when you want to settle with Atlas in different currencies (especially when you have opened multiple deposit accounts in different currencies in Atlas), you need to use this parameter.|
|displayCurrency|string¦null|false|none||The currency for the display fares in response. If no display currency is specified, the display amount will be null.|
|requestSource|string¦null|false|none||Identify the source of the search traffic, E.g. Google Flights, Oganic Search, SkyScanner.|

#### 枚举值

|属性|值|
|---|---|
|tripType|1|
|tripType|2|

<h2 id="tocS_OrderResponse">OrderResponse</h2>

<a id="schemaorderresponse"></a>
<a id="schema_OrderResponse"></a>
<a id="tocSorderresponse"></a>
<a id="tocsorderresponse"></a>

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
  "duplicateOrders": [
    "string"
  ],
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
  ]
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
|duplicateOrders|[string]¦null|false|none||If the api returns error code`318`(duplicate booking), then the list will contain duplicate order numbers.|
|paymentOptions|[object]|true|none||none|
|» paymentMethod|integer|true|none||none|
|» serviceFee|[PaymentOption](#schemapaymentoption)|true|none||none|
|» ticketFare|[PaymentOption](#schemapaymentoption)|true|none||none|
|» paymentFee|[PaymentOption](#schemapaymentoption)|true|none||none|
|» cardType|string¦null|true|none||none|

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

