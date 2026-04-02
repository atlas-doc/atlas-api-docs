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

# Other Functions

## POST Regenerate Order

POST /regenerateOrder.do

**Dependency:**
Order function should be called in prior to this call.

**Endpoint:**
https://sandbox.atriptech.com/regenerateOrder.do

> Body 请求参数

```json
{
  "originalOrderNo": "AAYDY20250816162229555"
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
|» originalOrderNo|body|string| 是 |The order number of the original ticket order you want to regenerate|

> 返回示例

> 200 Response

```json
{
  "sessionId": "b4eabebb-c95f-4721-b3ac-65e7a553047a",
  "offerId": null,
  "orderNo": "AAWPQ20250816170913493",
  "originalOrderNo": "AAYDY20250816162229555",
  "ticketOrderNo": null,
  "totalPrice": 954.02,
  "totalTransactionFee": 7.18,
  "currency": "CNY",
  "vendorTotalPrice": 498.21,
  "vendorCurrency": "SAR",
  "tktLimitTime": "2025-08-16 17:39:13",
  "pnrCode": "FNCHLR",
  "includeExtraBaggage": 0,
  "paxTicketInfos": [
    {
      "serialVersionUID": 6508292362378021000,
      "name": "********",
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
      "ticketStatus": null,
      "ancillaries": []
    }
  ],
  "routing": {
    "fid": "gxI2eU5jg8ny09kiTvZIxSgoO6cfIMz-Yl3QHGlIDERl7pomn85KJb1Jt6TNGiwV",
    "routingIdentifier": "UlVIX0RYQl8xXzIwMjUwODE3X18xXzBfMHxCR1M5NDIzMV9hcGlfMnwxfDk1NC4wMl85NTQuMDJfMzE0LjU4XzcuMThfMjIyOS44MF9DTll8UlVIX0RYQl8xXzIwMjUwODE3X18xXzBfMF5SVUgtWFkyMDUtLURYQi0yMDI1MDgxNzEyMjAtMjAyNTA4MTcxNTI1LVZBTDEtMS1eOTU0LjAyXzk1NC4wMl8zMTQuNThfNy4xOF8yMjI5LjgwXkFYWUFQSV9BWFleXkFYWTFSVUhEWEIyMDAyMDI1MDgxN15TQVJeNDk4LjIxXjQ5OC4yMV4xNjQuMjheMHwxfDIwMjUwODE2MTcwOTEzfDB8MTc1NTMzNTM1Mzc4M05aOGkxfHx8fHw3LjE4fDN8MHx8bm9ybWFsfGZhbHNl.GoNoudYJMU+2AiNREqc0xu6TNa3oT+PMg48hY/iKa/g=",
    "supportCreditTransPayment": "1",
    "supportPaymentMethods": [
      1,
      3
    ],
    "currency": "CNY",
    "adultPrice": 534.65,
    "adultTax": 419.37,
    "adultDetails": [
      {
        "code": "apiChannelFee",
        "type": "fee",
        "amount": 17.64,
        "description": ""
      },
      {
        "code": "farePrice",
        "type": "base",
        "amount": 517.01,
        "description": ""
      },
      {
        "code": "tax",
        "type": "tax",
        "amount": 419.37,
        "description": ""
      }
    ],
    "childPrice": 534.65,
    "childTax": 419.37,
    "childDetails": [
      {
        "code": "apiChannelFee",
        "type": "fee",
        "amount": 17.64,
        "description": ""
      },
      {
        "code": "farePrice",
        "type": "base",
        "amount": 517.01,
        "description": ""
      },
      {
        "code": "tax",
        "type": "tax",
        "amount": 419.37,
        "description": ""
      }
    ],
    "infantPrice": 314.58,
    "infantTax": 0,
    "infantDetails": [
      {
        "code": "apiChannelFee",
        "type": "fee",
        "amount": 8.19,
        "description": ""
      },
      {
        "code": "farePrice",
        "type": "base",
        "amount": 306.39,
        "description": ""
      },
      {
        "code": "tax",
        "type": "tax",
        "amount": 0,
        "description": ""
      }
    ],
    "childMandatorySeatingFee": null,
    "infantAllowed": true,
    "transactionFeePerPax": 7.18,
    "transactionFee": 7.18,
    "transactionFeeMode": "PER_PAX",
    "nationalityType": 0,
    "nationality": "",
    "suitAge": "",
    "PaxType": "ADT",
    "fromSegments": [
      {
        "segmentIndex": 1,
        "carrier": "XY",
        "flightNumber": "XY205",
        "depAirport": "RUH",
        "depTime": "202508171220",
        "arrAirport": "DXB",
        "arrTime": "202508171525",
        "stopCities": "",
        "duration": 125,
        "codeShare": false,
        "cabin": "",
        "cabinClass": 1,
        "seatCount": 2,
        "aircraftCode": "",
        "depTerminal": "",
        "arrTerminal": "",
        "operatingCarrier": "",
        "operatingFlightnumber": "",
        "fareFamily": "VAL1"
      }
    ],
    "retSegments": [],
    "combineIndexs": [],
    "rule": {
      "hasBaggage": 1,
      "baggageElements": [
        {
          "segmentNo": 1,
          "baggageType": "StandardCheckInBaggage",
          "passengerType": 0,
          "baggagePiece": 1,
          "baggageWeight": 20,
          "baggageSize": "75*50*33cm"
        },
        {
          "segmentNo": 1,
          "baggageType": "StandardCheckInBaggage",
          "passengerType": 1,
          "baggagePiece": 1,
          "baggageWeight": 20,
          "baggageSize": "75*50*33cm"
        },
        {
          "segmentNo": 1,
          "baggageType": "StandardCheckInBaggage",
          "passengerType": 2,
          "baggagePiece": 0,
          "baggageWeight": 0,
          "baggageSize": "75*50*33cm"
        },
        {
          "segmentNo": 1,
          "baggageType": "CabinBaggageOverheadLocker",
          "passengerType": 0,
          "baggagePiece": 1,
          "baggageWeight": 7,
          "baggageSize": "56*36*23cm"
        },
        {
          "segmentNo": 1,
          "baggageType": "CabinBaggageOverheadLocker",
          "passengerType": 1,
          "baggagePiece": 1,
          "baggageWeight": 7,
          "baggageSize": "56*36*23cm"
        },
        {
          "segmentNo": 1,
          "baggageType": "CabinBaggageOverheadLocker",
          "passengerType": 2,
          "baggagePiece": 0,
          "baggageWeight": 0,
          "baggageSize": "56*36*23cm"
        }
      ],
      "refundRules": [
        {
          "refundType": 0,
          "refundStatus": "T",
          "refundMethod": "CASH_BACK_TO_ORIGINAL_PAYMENT",
          "refundFee": 0,
          "currency": "SAR",
          "refNoshow": "T",
          "refNoShowCondition": 0,
          "refNoshowFee": 0,
          "ruleDetailList": [
            {
              "ruleId": 56740,
              "status": "T",
              "refundMethod": "CashBackToOriginalPayment",
              "startMinute": 525600,
              "endMinute": 0,
              "amount": 0,
              "currency": "SAR"
            },
            {
              "ruleId": 56741,
              "status": "T",
              "refundMethod": "CashBackToOriginalPayment",
              "startMinute": 0,
              "endMinute": -525600,
              "amount": 0,
              "currency": "SAR"
            }
          ],
          "ruleList": [
            {
              "rowId": 56740,
              "gmtCreate": 1747638757000,
              "gmtModified": 1747638757000,
              "creator": null,
              "modifier": null,
              "isDeleted": "N",
              "airline": "XY",
              "ruleType": "self_refund",
              "ruleName": "self_refund_XY_38_lp3bh5",
              "ruleKey": "self_refund_XY_2025051915123738",
              "priority": 20,
              "validBeginTime": 1570464000000,
              "validEndTime": 11468966399000,
              "depCity": null,
              "arrCity": null,
              "depCountry": null,
              "arrCountry": null,
              "bookingCode": null,
              "fareFamily": "VAL1",
              "cabinClass": null,
              "timingMode": "depTime",
              "timeLeft": null,
              "timeRight": 0,
              "travelBeginDate": null,
              "travelEndDate": null,
              "productType": null,
              "ruleExtend": {
                "ruleKey": "self_refund_XY_2025051915123738",
                "canRefund": "N",
                "canChange": null,
                "canRefundTax": "N",
                "canRefundPkg": null,
                "canRefundCoupon": null,
                "canMakeUpDiff": null,
                "canNoShowRefund": null,
                "amount": null,
                "amountCurrency": "SAR",
                "pricePercent": null,
                "priceItem": null,
                "taxItem": null,
                "charge": null,
                "chargeCurrency": null,
                "canExemptSameDay": null,
                "exemptDuration": null,
                "ticketBeginTime": null,
                "ticketEndTime": null,
                "applyBeginTime": null,
                "applyEndTime": null,
                "travelBeginTime": null,
                "travelEndTime": null
              }
            },
            {
              "rowId": 56741,
              "gmtCreate": 1747638757000,
              "gmtModified": 1747638757000,
              "creator": null,
              "modifier": null,
              "isDeleted": "N",
              "airline": "XY",
              "ruleType": "self_refund",
              "ruleName": "self_refund_XY_39_v7314B",
              "ruleKey": "self_refund_XY_2025051915123739",
              "priority": 20,
              "validBeginTime": 1570464000000,
              "validEndTime": 11468966399000,
              "depCity": null,
              "arrCity": null,
              "depCountry": null,
              "arrCountry": null,
              "bookingCode": null,
              "fareFamily": "VAL1",
              "cabinClass": null,
              "timingMode": "depTime",
              "timeLeft": 0,
              "timeRight": null,
              "travelBeginDate": null,
              "travelEndDate": null,
              "productType": null,
              "ruleExtend": {
                "ruleKey": "self_refund_XY_2025051915123739",
                "canRefund": "N",
                "canChange": null,
                "canRefundTax": "N",
                "canRefundPkg": null,
                "canRefundCoupon": null,
                "canMakeUpDiff": null,
                "canNoShowRefund": null,
                "amount": null,
                "amountCurrency": "SAR",
                "pricePercent": null,
                "priceItem": null,
                "taxItem": null,
                "charge": null,
                "chargeCurrency": null,
                "canExemptSameDay": null,
                "exemptDuration": null,
                "ticketBeginTime": null,
                "ticketEndTime": null,
                "applyBeginTime": null,
                "applyEndTime": null,
                "travelBeginTime": null,
                "travelEndTime": null
              }
            }
          ]
        }
      ],
      "changesRules": [
        {
          "changesType": 0,
          "changesStatus": "T",
          "changesFee": 0,
          "currency": "SAR",
          "revNoshow": "T",
          "revNoShowCondition": 0,
          "revNoshowFee": 0,
          "ruleList": [
            {
              "rowId": 35011,
              "gmtCreate": 1722605504000,
              "gmtModified": 1722605504000,
              "creator": null,
              "modifier": null,
              "isDeleted": "N",
              "airline": "XY",
              "ruleType": "self_change",
              "ruleName": "self_change_XY_28_8JxpOW",
              "ruleKey": "self_change_XY_2024080221314328",
              "priority": 10,
              "validBeginTime": 1570464000000,
              "validEndTime": 11468966399000,
              "depCity": null,
              "arrCity": null,
              "depCountry": null,
              "arrCountry": null,
              "bookingCode": null,
              "fareFamily": "VAL1",
              "cabinClass": null,
              "timingMode": "depTime",
              "timeLeft": null,
              "timeRight": -240,
              "travelBeginDate": null,
              "travelEndDate": null,
              "productType": null,
              "ruleExtend": {
                "ruleKey": "self_change_XY_2024080221314328",
                "canRefund": "Y",
                "canChange": null,
                "canRefundTax": "N",
                "canRefundPkg": null,
                "canRefundCoupon": null,
                "canMakeUpDiff": null,
                "canNoShowRefund": null,
                "amount": 150,
                "amountCurrency": "SAR",
                "pricePercent": null,
                "priceItem": null,
                "taxItem": null,
                "charge": null,
                "chargeCurrency": null,
                "canExemptSameDay": null,
                "exemptDuration": null,
                "ticketBeginTime": null,
                "ticketEndTime": null,
                "applyBeginTime": null,
                "applyEndTime": null,
                "travelBeginTime": null,
                "travelEndTime": null
              }
            },
            {
              "rowId": 35012,
              "gmtCreate": 1722605504000,
              "gmtModified": 1722605504000,
              "creator": null,
              "modifier": null,
              "isDeleted": "N",
              "airline": "XY",
              "ruleType": "self_change",
              "ruleName": "self_change_XY_29_OSEUU8",
              "ruleKey": "self_change_XY_2024080221314329",
              "priority": 10,
              "validBeginTime": 1570464000000,
              "validEndTime": 11468966399000,
              "depCity": null,
              "arrCity": null,
              "depCountry": null,
              "arrCountry": null,
              "bookingCode": null,
              "fareFamily": "VAL1",
              "cabinClass": null,
              "timingMode": "depTime",
              "timeLeft": -240,
              "timeRight": 0,
              "travelBeginDate": null,
              "travelEndDate": null,
              "productType": null,
              "ruleExtend": {
                "ruleKey": "self_change_XY_2024080221314329",
                "canRefund": "N",
                "canChange": null,
                "canRefundTax": "N",
                "canRefundPkg": null,
                "canRefundCoupon": null,
                "canMakeUpDiff": null,
                "canNoShowRefund": null,
                "amount": null,
                "amountCurrency": "SAR",
                "pricePercent": null,
                "priceItem": null,
                "taxItem": null,
                "charge": null,
                "chargeCurrency": null,
                "canExemptSameDay": null,
                "exemptDuration": null,
                "ticketBeginTime": null,
                "ticketEndTime": null,
                "applyBeginTime": null,
                "applyEndTime": null,
                "travelBeginTime": null,
                "travelEndTime": null
              }
            },
            {
              "rowId": 35013,
              "gmtCreate": 1722605504000,
              "gmtModified": 1722605504000,
              "creator": null,
              "modifier": null,
              "isDeleted": "N",
              "airline": "XY",
              "ruleType": "self_change",
              "ruleName": "self_change_XY_30_dVZtPh",
              "ruleKey": "self_change_XY_2024080221314330",
              "priority": 10,
              "validBeginTime": 1570464000000,
              "validEndTime": 11468966399000,
              "depCity": null,
              "arrCity": null,
              "depCountry": null,
              "arrCountry": null,
              "bookingCode": null,
              "fareFamily": "VAL1",
              "cabinClass": null,
              "timingMode": "depTime",
              "timeLeft": 0,
              "timeRight": null,
              "travelBeginDate": null,
              "travelEndDate": null,
              "productType": null,
              "ruleExtend": {
                "ruleKey": "self_change_XY_2024080221314330",
                "canRefund": "N",
                "canChange": null,
                "canRefundTax": "N",
                "canRefundPkg": null,
                "canRefundCoupon": null,
                "canMakeUpDiff": null,
                "canNoShowRefund": null,
                "amount": null,
                "amountCurrency": "SAR",
                "pricePercent": null,
                "priceItem": null,
                "taxItem": null,
                "charge": null,
                "chargeCurrency": null,
                "canExemptSameDay": null,
                "exemptDuration": null,
                "ticketBeginTime": null,
                "ticketEndTime": null,
                "applyBeginTime": null,
                "applyEndTime": null,
                "travelBeginTime": null,
                "travelEndTime": null
              }
            }
          ],
          "ruleDetailList": [
            {
              "ruleId": 35011,
              "status": "H",
              "refundMethod": null,
              "startMinute": 525600,
              "endMinute": 240,
              "amount": 219,
              "currency": "SAR"
            },
            {
              "ruleId": 35012,
              "status": "T",
              "refundMethod": null,
              "startMinute": 240,
              "endMinute": 0,
              "amount": 0,
              "currency": "SAR"
            },
            {
              "ruleId": 35013,
              "status": "T",
              "refundMethod": null,
              "startMinute": 0,
              "endMinute": -525600,
              "amount": 0,
              "currency": "SAR"
            }
          ]
        }
      ],
      "serviceElements": [
        {
          "hasFreeSeat": 2,
          "hasFreeMeal": 0
        }
      ]
    },
    "ancillaryProductElements": [
      {
        "segmentIndex": 1,
        "endSegmentIndex": null,
        "productCode": "SCI_BAG_1PC_25KG",
        "productName": "StandardCheckInBaggage",
        "productType": 1,
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 1,
        "price": 478.74,
        "currency": "CNY",
        "vendorPrice": 250,
        "vendorCurrency": "SAR",
        "clientTechnicalServiceFee": 0,
        "clientTechnicalServiceFeeMode": null,
        "auxBaggageElement": {
          "piece": 1,
          "weight": 25,
          "isAllWeight": true,
          "size": ""
        },
        "offerId": null,
        "maxQty": 1,
        "minQty": 1,
        "categoryCode": "StandardCheckInBaggage",
        "ancillaryCode": "SCI_BAG_1PC_25KG",
        "auxSeatElement": null,
        "displayPrice": null,
        "displayCurrency": null
      },
      {
        "segmentIndex": 1,
        "endSegmentIndex": null,
        "productCode": "SCI_BAG_1PC_15KG",
        "productName": "StandardCheckInBaggage",
        "productType": 1,
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 1,
        "price": 201.07,
        "currency": "CNY",
        "vendorPrice": 105,
        "vendorCurrency": "SAR",
        "clientTechnicalServiceFee": 0,
        "clientTechnicalServiceFeeMode": null,
        "auxBaggageElement": {
          "piece": 1,
          "weight": 15,
          "isAllWeight": true,
          "size": ""
        },
        "offerId": null,
        "maxQty": 1,
        "minQty": 1,
        "categoryCode": "StandardCheckInBaggage",
        "ancillaryCode": "SCI_BAG_1PC_15KG",
        "auxSeatElement": null,
        "displayPrice": null,
        "displayCurrency": null
      },
      {
        "segmentIndex": 1,
        "endSegmentIndex": null,
        "productCode": "SCI_BAG_1PC_20KG",
        "productName": "StandardCheckInBaggage",
        "productType": 1,
        "canPurchaseWithTicket": 1,
        "canPurchasePostTicket": 1,
        "price": 344.69,
        "currency": "CNY",
        "vendorPrice": 180,
        "vendorCurrency": "SAR",
        "clientTechnicalServiceFee": 0,
        "clientTechnicalServiceFeeMode": null,
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
        "auxSeatElement": null,
        "displayPrice": null,
        "displayCurrency": null
      }
    ],
    "vendorFare": {
      "vendorAdultPrice": 279.21,
      "vendorAdultTax": 219,
      "vendorChildPrice": 279.21,
      "vendorChildTax": 219,
      "vendorInfantPrice": 164.28,
      "vendorInfantTax": 0,
      "vendorCurrency": "SAR"
    },
    "bundleOptions": [],
    "links": [],
    "separateBookings": false,
    "refreshTime": null,
    "expireTime": null,
    "displayFare": null,
    "ancillarySupported": [
      "seat",
      "luggage"
    ],
    "cardChargeList": null,
    "tags": null,
    "riskSellout": false
  },
  "duplicateOrders": null,
  "paymentOptions": [
    {
      "paymentMethod": 1,
      "serviceFee": {
        "amount": 7.18,
        "currency": "CNY",
        "deductFrom": "DEPOSIT",
        "displayAmount": null,
        "displayCurrency": null
      },
      "ticketFare": {
        "amount": 954.02,
        "currency": "CNY",
        "deductFrom": "DEPOSIT",
        "displayAmount": null,
        "displayCurrency": null
      },
      "paymentFee": {
        "amount": 0,
        "currency": "CNY",
        "deductFrom": "CARD",
        "displayAmount": null,
        "displayCurrency": null
      },
      "cardType": null
    },
    {
      "paymentMethod": 3,
      "serviceFee": {
        "amount": 7.18,
        "currency": "CNY",
        "deductFrom": "DEPOSIT",
        "displayAmount": null,
        "displayCurrency": null
      },
      "ticketFare": {
        "amount": 498.21,
        "currency": "SAR",
        "deductFrom": "CARD",
        "displayAmount": null,
        "displayCurrency": null
      },
      "paymentFee": null,
      "cardType": null
    }
  ],
  "status": 0,
  "msg": null,
  "requestId": null,
  "clientRequestId": null
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
|» status|[OrderResponseStatus](#schemaorderresponsestatus)|true|none||- 301: Session does not exist or timed out. Description: The "sessionID" has a validity of 2 hrs. If the “sessionID” is used after this time period, then this error is displayed<br />- 302: The target flight is no longer available. Description: In the period between verify and book, the flight has been sold out. This can also be due to the number of passengers booked. The number of pax when booking and the number of pax when verifying may be different. When create a booking, the price is verified based on the actual number of pax booked<br />- 303: Airline closed. Description: Airline has either ceased to exist or not operational.<br />- 304: Verify failed. Description: In some uncontrollable situations, such as network issues, upgrades, and restarts, 304 error may occur, but not many. If there are many 304 errors, it is possible that the airline is not available or some technical issue at Atlas' end. Contact your account manager if this error keeps on repeating.<br />- 305: Invalid routing. Description: When generating an order, the system found that the flight was no longer sold for various reasons, such as 1) L2B 2) The system has identified that there may be a risk of the flight being sold out 3) The airline's sales have been closed<br />- 307: Illegal booking request parameters. Description: Some request parameters have problem. Please check the message.<br />- 308: Price changed. Description: The price has changed between the price verification and order. Please verify the price again and generate the order.<br />- 309: Ancillary not found. Description: Incorrect ancillary product code has been entered. Check and enter the correct ancillary product code.<br />- 310: Infant not allowed. Description: The offer does not support infant. Create a new booking without infant passenger type.<br />- 312: Too many seats booked. Description: The number of pax booked exceeds the remaining (or allowed) seats on the current flight.<br />- 313: Fare family sold out. Description: Selected offer is no longer available. Conduct the search again and rebook.<br />- 315: Not enough seats. Description: Seats have been sold out<br />- 316: Timed out. Description: There is a time-out error at the airline’s end<br />- 317: Booking unsuccessful with Airline. Description: An error has happened at the airline’s end.<br />- 318: Check if a booking with the same passenger details and flight numbers exists. After confirming, ignore this booking.<br />- 319: Flight information has changed. Description: Re-verify the price (query the latest flight information) and generate the order.<br />- 320: The requested seats were not found or they are already occupied. Description: Rebook seats and submit a new order.<br />- 321: <br />- 322: Seat price changed. Description: Seat price changed. Re-query the seat map and select seats<br />- 323: The format of the e-mail in the contact information is incorrect<br />- 324: Airline system issues. Description: Retry after some time. If the issue persists, please contact our operations team.<br />- 325: The airline has deemed the passenger unserviceable<br />- 326: Your account balance on the airline side is insufficient(BYOA scenario)<br />- 327: Passenger information does not meet the requirements. Description: Check and correct the passenger information according to the error message<br />- 328: Selected seat is no longer available. Description: The selected seat has been occupied.<br />- 329: No payment method is available. Description: No payment method is available. Please check whether the quotation currency or account configuration is correct.<br />- 330: operation is in progress. Description: operation is in progress|
|» msg|[ResponseMessage](#schemaresponsemessage)|true|none||It serves as an additional description of the response result. Especially when the interface reports an error (`status` !=`0`), it is usually a human-readable error message. Note: Do not use this field in any programming scenarios. For example, do not judge whether the interface responds successfully based on this field. Instead, you should only determine it by checking whether the status is equal to`0`at any time.|
|» sessionId|string|true|none||none|
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

## POST Stop Ticket Issuance

POST /stopTicket.do

**Dependency:**
`Payment` function should be called in prior to this call.

**Endpoint:**
https://sandbox.atriptech.com/stopTicket.do

> Body 请求参数

```json
{
  "orderNo": "ZNMKU20220119160129691"
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
|» orderNo|body|string| 是 |The order number of the ticket order you want to stop ticket issuance.|

> 返回示例

> 200 Response

```json
{
  "status": 0,
  "msg": "We are trying to intercept the ticket issuance. Please check the order status for result after 8 minutes"
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
|» status|integer|true|none||-`0`: success<br />-other: fail|
|» msg|[ResponseMessage](#schemaresponsemessage)¦null|false|none||It serves as an additional description of the response result. Especially when the interface reports an error (`status` !=`0`), it is usually a human-readable error message. Note: Do not use this field in any programming scenarios. For example, do not judge whether the interface responds successfully based on this field. Instead, you should only determine it by checking whether the status is equal to`0`at any time.|

## POST Order List

POST /orderList.do

**Dependency:**
No preceding function needs to be called before 'orderList' API.

**Endpoint:**
https://sandbox.atriptech.com/orderList.do

> Body 请求参数

```json
{
  "orderNo": "",
  "airlinePNRs": [
    "FT759J",
    "8HFT67"
  ],
  "paxName": "",
  "contactEmail": "",
  "fromCity": "",
  "toCity": "",
  "depDate": "20250101",
  "createTimeRangeFrom": "2024-10-31T19:57:46Z",
  "createTimeRangeTo": "2024-11-01T19:57:46Z",
  "orderStatus": [
    0,
    1,
    2,
    -3
  ],
  "airlines": [
    "SL",
    "TF"
  ],
  "page": 1,
  "pageSize": 20
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
|» orderNo|body|string¦null| 否 |Atlas order number. Accurate matching|
|» airlinePNRs|body|[string]¦null| 否 |The airline PNR(not Atlas's).  If the airline pnr of the order contains any of the given values, it will be returned.|
|» paxName|body|string¦null| 否 |The name of the passenger(last name/first name). If the passenger in the order includes the given value, it will be returned.|
|» contactEmail|body|string¦null| 否 |Accurate matching，match based on the contact email provided by the customer|
|» fromCity|body|string¦null| 否 |IATA code of the departure city|
|» toCity|body|string¦null| 否 |IATA code of the arrival city|
|» depDate|body|string¦null| 否 |Date of departure. The format is:`yyyyMMdd`|
|» createTimeRangeFrom|body|string¦null| 否 |The start time of order creation. This is in UTC. The format is:`yyyy-MM-dd'T'HH:mm:ss'Z'`.|
|» createTimeRangeTo|body|string¦null| 否 |The end time of order creation. This is in UTC. The format is`yyyy-MM-dd'T'HH:mm:ss'Z'`|
|» orderStatus|body|[[OrderStatus](#schemaorderstatus)]¦null| 否 |If the status of the order matches any of the given values, it will be returned|
|» airlines|body|[string]¦null| 否 |If the airlines of the order contains any of the given values, it will be returned|
|» page|body|string¦null| 否 |Start from: 1|
|» pageSize|body|string¦null| 否 |Number of records to be displayed on each page.|

#### 枚举值

|属性|值|
|---|---|
|» orderStatus|0|
|» orderStatus|1|
|» orderStatus|2|
|» orderStatus|-3|

> 返回示例

> 200 Response

```json
{
  "status": 0,
  "msg": null,
  "page": 1,
  "pageSize": 20,
  "totalRecords": 2,
  "orders": [
    {
      "orderNo": "TESTA20241122090710695",
      "pnrCode": "Z27T5B",
      "airlinePNRs": [
        "FT759J"
      ],
      "orderStatus": 2,
      "depDate": "20250101",
      "airlines": [
        "SL"
      ],
      "orderCreateTimestamp": "2024-11-22T01:07:10Z",
      "paymentTimestamp": "2024-11-22T01:07:11Z",
      "paxNames": [
        "YIJING/tFGo"
      ],
      "contactEmail": "test@test.com",
      "fromCity": "CNX",
      "toCity": "BKK",
      "errorCode": null,
      "errorMessage": null
    },
    {
      "orderNo": "TESTA20241122080618700",
      "pnrCode": "LLQNYJ",
      "airlinePNRs": [
        "8HFT67|8HFT67"
      ],
      "orderStatus": 2,
      "depDate": "20250101",
      "airlines": [
        "TF"
      ],
      "orderCreateTimestamp": "2024-11-22T00:06:18Z",
      "paymentTimestamp": "2024-11-22T00:06:19Z",
      "paxNames": [
        "YIJING/gAMM",
        "JIXING/gAMM"
      ],
      "contactEmail": "test@test.com",
      "fromCity": "VBY",
      "toCity": "STO",
      "errorCode": null,
      "errorMessage": null
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
|» status|integer|true|none||none|
|» msg|[ResponseMessage](#schemaresponsemessage)¦null|false|none||It serves as an additional description of the response result. Especially when the interface reports an error (`status` !=`0`), it is usually a human-readable error message. Note: Do not use this field in any programming scenarios. For example, do not judge whether the interface responds successfully based on this field. Instead, you should only determine it by checking whether the status is equal to`0`at any time.|
|» page|string|true|none||none|
|» pageSize|string|true|none||none|
|» totalRecords|string|true|none||none|
|» orders|[object]|true|none||none|
|»» orderNo|string|true|none||Atlas order number|
|»» pnrCode|string|true|none||Atlas internal reference code|
|»» airlinePNRs|[string]¦null|false|none||Airline PNRs in the order|
|»» orderStatus|[OrderStatus](#schemaorderstatus)|true|none||Order status|
|»» depDate|string|true|none||Date of departure. The format is:`YYYYMMDD`|
|»» airlines|[string]|true|none||The IATA codes of all airlines in the order|
|»» orderCreateTimestamp|string|true|none||The time of order creation. This is in UTC. Format:`yyyy-MM-dd'T'HH:mm:ss'Z'`|
|»» paymentTimestamp|string|true|none||The time payment was made. This is in UTC. Format:`yyyy-MM-dd'T'HH:mm:ss'Z'`|
|»» paxNames|[string]|true|none||The names of all passengers in the order|
|»» contactEmail|string|true|none||Contact email provided by the customer|
|»» fromCity|string|true|none||IATA code of departure city|
|»» toCity|string|true|none||IATA code of arrival city|
|»» errorCode|string¦null|false|none||The error code returned for a cancelled order. This will only be displayed for cancelled orders.|
|»» errorMessage|string¦null|false|none||The error description.|

#### 枚举值

|属性|值|
|---|---|
|orderStatus|0|
|orderStatus|1|
|orderStatus|2|
|orderStatus|-3|

## POST PNR Claim

POST /pnr/claim.do

**Dependency**
No preceding function needs to be carried out.

**Endpoint:**
https://sandbox.atriptech.com/pnr/claim.do

> Body 请求参数

```json
{
  "mmb": {
    "airlinePnr": "S1BE6Z",
    "email": "TESTABC22Oct@pnrclaim.com"
  },
  "passengers": [
    {
      "name": "test/abc",
      "passengerType": 0,
      "birthday": "20001010",
      "gender": "M",
      "cardNum": "",
      "cardType": "PP",
      "cardIssuePlace": "",
      "cardExpired": "20241010",
      "nationality": ""
    }
  ],
  "fromSegments": [
    {
      "carrier": "AK",
      "flightNumber": "AK128",
      "depAirport": "DEL",
      "arrAirport": "BOM",
      "depTime": "202411201600",
      "arrTime": "202411201820",
      "stopCities": "",
      "codeShare": 0,
      "operatingCarrier": "",
      "operatingFlightNumber": "",
      "depTerminal": "T2",
      "arrTerminal": "T1",
      "cabinClass": "1",
      "fareFamily": "Flexi",
      "flightIndex": null,
      "duration": 140
    }
  ],
  "retSegments": null
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
|» mmb|body|object¦null| 否 |The information used for loging into traveler’s MMB|
|»» airlinePnr|body|string| 是 |Passenger Name Record generated by the airline.|
|»» email|body|string¦null| 否 |Contact email.|
|» passengers|body|[object]| 是 |none|
|»» name|body|string| 是 |The passenger's name. Please send it in the following format: Family Name/Given Name|
|»» passengerType|body|[PassengerType](#schemapassengertype)¦null| 否 |Type of passenger.|
|»» gender|body|string¦null| 否 |The passenger's gender.|
|»» birthday|body|string¦null| 否 |The passenger's date of birth. Format:`YYYYMMDD`. Please fill in according to the passenger information requirements(`bookingRequirement`) returned by the Verification / Get Offer API.|
|»» cardType|body|string¦null| 否 |The type of the identity document.|
|»» cardNum|body|string¦null| 否 |The unique identifier of the identity document. e.g. the passport number. Please fill in according to the passenger information requirements(`bookingRequirement`) returned by the Verification / Get Offer API.|
|»» cardIssuePlace|body|string¦null| 否 |The ISO 3166-1 alpha-2 code for the country where the identity document is issued. Please fill in according to the passenger information requirements(`bookingRequirement`) returned by the Verification / Get Offer API.|
|»» cardExpired|body|string¦null| 否 |The date on which the identity document expires. Format:`YYYYMMDD`.Please fill in according to the passenger information requirements(`bookingRequirement`) returned by the Verification / Get Offer API.|
|»» nationality|body|string¦null| 否 |The ISO 3166-1 alpha-2 code for the nationality of passenger. Please fill in according to the passenger information requirements(`bookingRequirement`) returned by the Verification / Get Offer API.|
|» fromSegments|body|[object]| 是 |Outbound segments|
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
|» connectInfo|body|object¦null| 否 |none|
|»» contactName|body|string¦null| 否 |none|
|»» contactEmail|body|string¦null| 否 |none|
|»» contactPhone|body|string¦null| 否 |none|
|»» useAtlasMailForContact|body|string¦null| 否 |none|

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
|»» passengerType|0|
|»» passengerType|1|
|»» passengerType|2|
|»» cardType|PP|
|»» cardType|GA|
|»» cardType|TW|
|»» cardType|TB|
|»» cardType|HY|
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
  "orderNo": "TESTC20241022100111040",
  "pnrCode": "RCOFMU",
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
|» status|string|true|none||none|
|» msg|string¦null|false|none||none|
|» orderNo|string|true|none||Atlas order number|

## POST Get Balance

POST /balance.do

**Dependency**
No preceding function needs to be carried out.

**Endpoint:**
https://sandbox.atriptech.com/balance.do

> Body 请求参数

```json
{
  "currency": "string"
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
|» currency|body|string| 是 |The currency of your balance account|

> 返回示例

> 200 Response

```json
{
  "accountBalance": {
    "amount": 12308007.89,
    "currency": "USD"
  },
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
|» status|integer|true|none||none|
|» msg|string¦null|false|none||none|
|» accountBalance|object¦null|false|none||This element contavins the information regarding the amount and the currency of transaction of the customer.|
|»» amount|string|true|none||The amount of balance in your deposit account.|
|»» currency|string|true|none||The currency in which Atlas settles transactions with you.|

## POST City Pairs API

POST /route/export.do

The "City pairs API" can be used to download the city pairs supported by Atlas as well as by the airlines. 
The customer can use this structured data and transfer the city pair information into their mid-back office systems.

**This API is only available in the production environment.**

**Dependency**
There is no dependency for this call.

**Endpoint:**
https://sandbox.atriptech.com/route/export.do

> Body 请求参数

```json
{
  "routeType": 1,
  "fromCity": "LON",
  "fromCountry": "GB",
  "toCity": "AMS",
  "toCountry": "NL"
}
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|Accept|header|string| 是 |none|
|Content-Type|header|string| 是 |none|
|Accept-Encoding|header|string| 是 |none|
|x-atlas-client-id|header|string| 否 |none|
|x-atlas-client-secret|header|string| 否 |none|
|body|body|object| 否 |none|
|» routeType|body|integer| 是 |-`1`: Airline routes|
|» fromCity|body|string¦null| 否 |IATA Code of departure city.|
|» fromCountry|body|string¦null| 否 |IATA Code of departure country.|
|» toCity|body|string¦null| 否 |IATA Code of arrival city or airport|
|» toCountry|body|string¦null| 否 |IATA Code of arrival country.|
|» airlines|body|[string]¦null| 否 |An array of IATA Codes of airlines. The routes within the airlines will be returned.|
|» pageSize|body|integer¦null| 否 |none|
|» pageNumber|body|integer¦null| 否 |none|

#### 详细说明

**» routeType**: -`1`: Airline routes
-`2`: Atlas routes

> 返回示例

> 200 Response

```json
{
  "data": [
    {
      "airlines": [
        "U2"
      ],
      "fromCity": "LON",
      "fromCountry": "GB",
      "toCity": "AMS",
      "toCountry": "NL",
      "isDirect": null,
      "scheduleStart": null,
      "scheduleEnd": null,
      "updateDate": "20250408"
    },
    {
      "airlines": [
        "DS"
      ],
      "fromCity": "LON",
      "fromCountry": "GB",
      "toCity": "AMS",
      "toCountry": "NL",
      "isDirect": null,
      "scheduleStart": null,
      "scheduleEnd": null,
      "updateDate": "20250408"
    },
    {
      "airlines": [
        "EC"
      ],
      "fromCity": "LON",
      "fromCountry": "GB",
      "toCity": "AMS",
      "toCountry": "NL",
      "isDirect": null,
      "scheduleStart": null,
      "scheduleEnd": null,
      "updateDate": "20250408"
    },
    {
      "airlines": [
        "DH"
      ],
      "fromCity": "LON",
      "fromCountry": "GB",
      "toCity": "AMS",
      "toCountry": "NL",
      "isDirect": null,
      "scheduleStart": null,
      "scheduleEnd": null,
      "updateDate": "20250402"
    },
    {
      "airlines": [
        "D8"
      ],
      "fromCity": "LON",
      "fromCountry": "GB",
      "toCity": "AMS",
      "toCountry": "NL",
      "isDirect": null,
      "scheduleStart": null,
      "scheduleEnd": null,
      "updateDate": "20250402"
    },
    {
      "airlines": [
        "LE"
      ],
      "fromCity": "LON",
      "fromCountry": "GB",
      "toCity": "AMS",
      "toCountry": "NL",
      "isDirect": null,
      "scheduleStart": null,
      "scheduleEnd": null,
      "updateDate": "20250402"
    },
    {
      "airlines": [
        "DY"
      ],
      "fromCity": "LON",
      "fromCountry": "GB",
      "toCity": "AMS",
      "toCountry": "NL",
      "isDirect": null,
      "scheduleStart": null,
      "scheduleEnd": null,
      "updateDate": "20250402"
    },
    {
      "airlines": [
        "6E"
      ],
      "fromCity": "LON",
      "fromCountry": "GB",
      "toCity": "AMS",
      "toCountry": "NL",
      "isDirect": null,
      "scheduleStart": null,
      "scheduleEnd": null,
      "updateDate": "20241210"
    },
    {
      "airlines": [
        "GQ"
      ],
      "fromCity": "LON",
      "fromCountry": "GB",
      "toCity": "AMS",
      "toCountry": "NL",
      "isDirect": null,
      "scheduleStart": null,
      "scheduleEnd": null,
      "updateDate": "20250217"
    }
  ],
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
|» status|integer|true|none||none|
|» msg|string¦null|false|none||none|
|» data|[object]|true|none||none|
|»» airlines|string|true|none||An array of IATA Codes of airlines.|
|»» fromCity|string|true|none||IATA Code of departure city or airport|
|»» fromCountry|string|true|none||IATA Code of departure country.|
|»» toCity|string|true|none||IATA Code of arrival city or airport|
|»» toCountry|string|true|none||IATA Code of arrival country.|
|»» isDirect|string|true|none||-`true`: Direct Flight<br />-`false`: Connecting Flight<br />This data will only be available when the "routeType" = 2 (Atlas Routes)|
|»» scheduleStart|string|true|none||The start date of the booking window. The format is YYYYMMDD.|
|»» scheduleEnd|string|true|none||The end date of the booking window. The format is YYYYMMDD.|
|»» updateDate|string|true|none||The date when the routing data was updated. The format is YYYYMMDD.|

## POST Email List

POST /queryMail.do

**Dependency**
No preceding function needs to be carried out.

**Endpoint:**
https://sandbox.atriptech.com/queryMail.do

> Body 请求参数

```json
{
  "orderNo": "TESTD20230811113115020",
  "emailReceivingDateStart": "2022-12-11 18:33:33",
  "emailReceivingDateEnd": "2022-12-11 18:33:33",
  "createTimeStart": "2022-12-11 18:33:33",
  "createTimeEnd": "2022-12-11 18:33:45",
  "emailCategories": [
    "Payment Success",
    "Advertisement"
  ],
  "pageIndex": 1,
  "pageSize": 100
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
|» orderNo|body|string¦null| 否 |Order number.|
|» emailReceivingDateStart|body|string¦null| 否 |Start of the receiving time.|
|» emailReceivingDateEnd|body|string¦null| 否 |End of the receiving time.|
|» createTimeStart|body|string¦null| 否 |Start of creation time.|
|» createTimeEnd|body|string¦null| 否 |End of creation time.|
|» emailCategories|body|string¦null| 否 |Atlas email categories. Atlas categorizes emails but does not guarantee accuracy in classification.|
|» pageIndex|body|string¦null| 否 |none|
|» pageSize|body|string¦null| 否 |none|

#### 详细说明

**» orderNo**: Order number.
At least one of the order number, receiving time and/or creation time must be specified for querying.

**» emailReceivingDateStart**: Start of the receiving time.
The time Atlas received the airline's email.
Format: yyyy-MM-dd hh:mm:ss UTC+08:00

**» emailReceivingDateEnd**: End of the receiving time.
The time Atlas received the airline's email.
Format: yyyy-mm-dd hh:mm:ss UTC+08:00.
You can only query data for up to one month at a time

**» createTimeStart**: Start of creation time.
Create Time is the time when Atlas created this email record in the Email list. Generally, it will be later than the receiving time.
Format: yyyy-mm-dd hh:mm:ss UTC+08:00

**» createTimeEnd**: End of creation time.
Create Time is the time when Atlas created this email record in the Email list. Generally, it will be later than the receiving time.
Format: yyyy-MM-dd hh:mm:ss UTC+08:00
You can only query data for up to one month at a time.

**» emailCategories**: Atlas email categories. Atlas categorizes emails but does not guarantee accuracy in classification.
-`Travel Itinerary`
-`Schedule Change`
-`Payment Due`
-`Payment Success`
-`Receipt`
-`Trip Reminder`
-`PNR Cancellation Success`
-`Advertisement`
-`Duplicated Schedule Change`
-`Verification`
-`Unaccounted Cancellation`
-`Promo code`

> 返回示例

> 200 Response

```json
{
  "records": [
    {
      "orderNo": "TESTD20230811113115020",
      "emailReceivingDate": "2022-12-11 18:33:33",
      "uniqueCode": "2b5435c63102ac28d840b2a54f61e2db",
      "emailCategory": "Unidentified",
      "from": "xiaoyebiao@qq.com",
      "to": "connexpay@mx.theatlas.top",
      "emailSubject": "sda",
      "emailLink": "http://order-oss-sg.oss-ap-southeast-1.aliyuncs.com/2022/12/2b5435c63102ac28d840b2a54f61e2db.eml?Expires=1704364782&OSSAccessKeyId=LTAI5tDmTE9iwtNdsqxVXuom&Signature=Hl6vBTM8lv%2Fan%2FFnCVQmQnwaXnk%3D",
      "createTime": "2022-12-11 18:33:45"
    }
  ],
  "hasNext": false,
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
|» status|integer|true|none||none|
|» msg|string¦null|false|none||none|
|» hasNext|boolean|true|none||-`true`: There is also the next page<br />-`false`: There is not the next page|
|» records|[object]|true|none||none|
|»» orderNo|string|true|none||Order number|
|»» emailReceivingDate|string|true|none||The time Atlas received the airline's email.<br />Format: yyyy-MM-dd HH:mm:ss UTC+08:00|
|»» uniqueCode|string|true|none||Unique Code of the email|
|»» emailCategory|string|true|none||Atlas email categories. Atlas categorizes emails but does not guarantee accuracy in classification.|
|»» from|string|true|none||Email “from” address|
|»» to|string|true|none||Email “to” address|
|»» emailSubject|string|true|none||Email “Subject”|
|»» emailLink|string¦null|false|none||Email Link. Email Link is only valid for 10 mins.|
|»» createTime|string|true|none||Create Time is the time when Atlas created this email record in the Email list.<br />Generally, it will be later than the receiving time.<br />Format: yyyy-MM-dd HH:mm:ss UTC+08:00|

## POST Extract PNR

POST /extractPnr.do

This API is used to directly connect to airlines and extract PNR information. The content displayed by this API reflects the current PNR information on the airline side, such as flight schedule and ticket status. Atlas extracts airline information truthfully and will not do any modification.

**Endpoint:**
https://sandbox.atriptech.com/extractPnr.do

> Body 请求参数

```json
{
  "airlinePnr": "0419",
  "carrier": "BC",
  "passengers": [
    {
      "firstName": "***",
      "lastName": "*****",
      "passengerType": null
    }
  ],
  "contact": {
    "email": "*********************"
  },
  "routing": {
    "fromSegments": [
      {
        "dptAirport": "UKB",
        "arrAirport": "HND",
        "flightNumber": "BC108",
        "depTime": "2025-07-27 13:00",
        "arrTime": "2025-07-27 14:15"
      }
    ],
    "retSegments": null
  },
  "timeout": 15000,
  "requestSource": null,
  "channel": null,
  "mainChannel": null,
  "subChannelID": null,
  "requestOwner": null,
  "requestId": "50fbfd16ec2c4bfa8f604f8788565311",
  "clientRequestId": null
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
|» airlinePnr|body|string| 是 |The airline PNR|
|» carrier|body|string| 是 |2-letter IATA code for the airline|
|» passengers|body|[object]| 是 |none|
|»» firstName|body|string| 是 |none|
|»» lastName|body|string| 是 |none|
|» contact|body|object| 是 |none|
|»» email|body|string| 是 |Contact email.|
|» routing|body|object| 是 |The original flight segment information at the time of order generation|
|»» fromSegments|body|[object]| 是 |none|
|»»» arrAirport|body|string| 是 |3-letter iata code for the arrival airport at which the segment is scheduled to arrive.|
|»»» arrTime|body|string| 是 |The datetime at which the segment is scheduled to arrive, in the arrival airport timezone. The format is `yyyy-MM-dd HH:mm`.|
|»»» dptAirport|body|string| 是 |3-letter iata code for the airport at which the segment is scheduled to depart.|
|»»» depTime|body|string| 是 |The datetime at which the segment is scheduled to depart, in the departure airport timezone. The format is`yyyy-MM-dd HH:mm`.|
|»»» flightNumber|body|string| 是 |Marketing flight number. The format is: CA123 or TR021 or FR1290, with the first two letters representing the carrier and the following number representing the flight number.|
|»» retSegments|body|[object]¦null| 否 |none|
|»»» arrAirport|body|string| 是 |3-letter iata code for the arrival airport at which the segment is scheduled to arrive.|
|»»» arrTime|body|string| 是 |The datetime at which the segment is scheduled to arrive, in the arrival airport timezone. The format is `yyyy-MM-dd HH:mm`.|
|»»» dptAirport|body|string| 是 |3-letter iata code for the airport at which the segment is scheduled to depart.|
|»»» depTime|body|string| 是 |The datetime at which the segment is scheduled to depart, in the departure airport timezone. The format is`yyyy-MM-dd HH:mm`.|
|»»» flightNumber|body|string| 是 |Marketing flight number. The format is: CA123 or TR021 or FR1290, with the first two letters representing the carrier and the following number representing the flight number.|
|» timeout|body|integer¦null| 否 |The maximum response duration, in milliseconds. Note: This time is estimated due to the impact of network transmission.|

> 返回示例

> 200 Response

```json
{
  "status": 99005,
  "msg": "string",
  "airlinePnr": "BSG768",
  "pnrStatus": "Ticketed",
  "pnrUsed": "used",
  "currency": "USD",
  "totalPrice": "string",
  "routing": {
    "fromSegments": [
      {
        "aircraftCode": "string",
        "arrAirport": "string",
        "arrTerminal": "string",
        "arrTime": "string",
        "carrier": "string",
        "codeShare": true,
        "depAirport": "string",
        "depTerminal": "string",
        "depTime": "string",
        "duration": 0,
        "flightNumber": "string",
        "operatingCarrier": "string",
        "operatingFlightnumber": "string"
      }
    ],
    "retSegments": [
      {
        "aircraftCode": "string",
        "arrAirport": "string",
        "arrTerminal": "string",
        "arrTime": "string",
        "carrier": "string",
        "codeShare": true,
        "depAirport": "string",
        "depTerminal": "string",
        "depTime": "string",
        "duration": 0,
        "flightNumber": "string",
        "operatingCarrier": "string",
        "operatingFlightnumber": "string"
      }
    ]
  },
  "paxTicketInfos": [
    {
      "name": "string",
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
      ],
      "ticketStatus": "OPEN_FOR_USE"
    }
  ],
  "contact": {
    "email": "string",
    "companyName": "string"
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
|» status|integer|true|none||none|
|» msg|string¦null|false|none||none|
|» airlinePnr|string|true|none||Airline PNR(not Atlas)|
|» pnrStatus|string|true|none||none|
|» pnrUsed|string¦null|true|none||pnr usage status|
|» currency|string¦null|false|none||The currency of fare|
|» totalPrice|string¦null|false|none||none|
|» routing|object|true|none||The current flight schedule. It may be different from that at the time of booking (flight schedule change).|
|»» fromSegments|[object]|true|none||none|
|»»» aircraftCode|string¦null|false|none||IATA Code of aircraft type|
|»»» arrAirport|string|true|none||3-letter iata code for the arrival airport at which the segment is scheduled to arrive.|
|»»» arrTerminal|string¦null|false|none||The terminal at the destination airport where the segment is scheduled to arrive.|
|»»» arrTime|string|true|none||The datetime at which the segment is scheduled to arrive, in the arrival airport timezone. The format is `YYYYMMDD`.|
|»»» carrier|string|true|none||IATA code of marketing carrier.|
|»»» codeShare|boolean|true|none||A flag used to identify whether it is a code share flight.|
|»»» depAirport|string|true|none||3-letter iata code for the airport at which the segment is scheduled to depart.|
|»»» depTerminal|string¦null|false|none||The terminal at the departure airport from which the segment is scheduled to depart.|
|»»» depTime|string|true|none||The datetime at which the segment is scheduled to depart, in the departure airport timezone. The format is`YYYYMMSS`.|
|»»» duration|integer|true|none||The duration of the segment in munites.|
|»»» flightNumber|string|true|none||Marketing flight number. The format is: CA123 or TR021 or FR1290, with the first two letters representing the carrier and the following number representing the flight number.|
|»»» operatingCarrier|string¦null|false|none||2-letter iata code for the operating carrier. The airline actually operating this segment. This may differ from the marketing carrier in the case of a "codeshare", where one airline sells flights operated by another airline.|
|»»» operatingFlightnumber|string¦null|false|none||Operating flight number.|
|»» retSegments|[object]¦null|false|none||none|
|»»» aircraftCode|string¦null|false|none||IATA Code of aircraft type|
|»»» arrAirport|string|true|none||3-letter iata code for the arrival airport at which the segment is scheduled to arrive.|
|»»» arrTerminal|string¦null|false|none||The terminal at the destination airport where the segment is scheduled to arrive.|
|»»» arrTime|string|true|none||The datetime at which the segment is scheduled to arrive, in the arrival airport timezone. The format is `YYYYMMDD`.|
|»»» carrier|string|true|none||IATA code of marketing carrier.|
|»»» codeShare|boolean|true|none||A flag used to identify whether it is a code share flight.|
|»»» depAirport|string|true|none||3-letter iata code for the airport at which the segment is scheduled to depart.|
|»»» depTerminal|string¦null|false|none||The terminal at the departure airport from which the segment is scheduled to depart.|
|»»» depTime|string|true|none||The datetime at which the segment is scheduled to depart, in the departure airport timezone. The format is`YYYYMMSS`.|
|»»» duration|integer|true|none||The duration of the segment in munites.|
|»»» flightNumber|string|true|none||Marketing flight number. The format is: CA123 or TR021 or FR1290, with the first two letters representing the carrier and the following number representing the flight number.|
|»»» operatingCarrier|string¦null|false|none||2-letter iata code for the operating carrier. The airline actually operating this segment. This may differ from the marketing carrier in the case of a "codeshare", where one airline sells flights operated by another airline.|
|»»» operatingFlightnumber|string¦null|false|none||Operating flight number.|
|» paxTicketInfos|[object]|true|none||Ticket information for each passenger.|
|»» name|string|true|none||Echo the passenger's name, in the format of last name/first name|
|»» ticketNos|[string]|true|none||Ticket numbers. There may be two tickets for the round trip, in which case the number of arrays is two.|
|»» airlinePNRs|[string]|true|none||A list containing airline PNR. There may be two PNRs for the round trip, in which case the number of arrays is two.|
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
|»» ticketStatus|string|true|none||Ticket status|
|» contact|object|true|none||none|
|»» email|string¦null|false|none||Contact email.|
|»» companyName|string¦null|false|none||Company name.|

#### 枚举值

|属性|值|
|---|---|
|status|99005|
|status|99006|
|status|99007|
|pnrStatus|OnHold|
|pnrStatus|Ticketed|
|pnrStatus|Cancelled|
|pnrStatus|Unknown|
|pnrUsed|used|
|pnrUsed|unused|
|ticketStatus|OPEN_FOR_USE|
|ticketStatus|REFUND|
|ticketStatus|USED|
|ticketStatus|PARTIALLY_USED|
|ticketStatus|NOSHOW|
|ticketStatus|UNKNOWN|

## POST getAtripToken

POST /getAtripToken.do

**Dependency**
No preceding function needs to be carried out.

> Body 请求参数

```json
{
  "cid": "xxxxxx",
  "orderNo": "XXXXXXXXXXXXXXXXXXX",
  "userName": "tony.kal",
  "role": "TICKETING"
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
|» orderNo|body|string| 是 |Order number. It can be an order for ticketing, or an order for add bags. The format of each kind of order is different.|
|» userName|body|string| 是 |This is to identifier the operator's name in client's system, Atlas will grant access to this operator and track his/her actions in Atlas customer service portal.|
|» role|body|string| 是 |This is to identify the operator's role. Atlas will grant access to this operator according to the role assigned. Here are the acceptable options:|

#### 详细说明

**» role**: This is to identify the operator's role. Atlas will grant access to this operator according to the role assigned. Here are the acceptable options:

Customer service : Access to manage orders and request post ticketing services

Finance : Access to manage the balance and check statements

Developer : Access to manage the system configurations

Admin : Full access

> 返回示例

> 200 Response

```json
{
  "url": "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
  "msg": null,
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
|» url|string|true|none||A url with token to access to Atlas customer service portal.|
|» status|integer|true|none||0: success<br /><br />2: System error<br /><br />3: unauthorized access|
|» msg|string¦null|false|none||Error message.<br /><br />The 'msg' element is for description of the results. Please DO NOT use this field to check the success or failure of the request. Only use the 'status' code to check the result.|

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

<h2 id="tocS_OrderStatus">OrderStatus</h2>

<a id="schemaorderstatus"></a>
<a id="schema_OrderStatus"></a>
<a id="tocSorderstatus"></a>
<a id="tocsorderstatus"></a>

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
|*anonymous*|-3|

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

