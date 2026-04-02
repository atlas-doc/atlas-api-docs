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

# Refund

## POST Refund Quotation

POST /refundQuotation.do

**Dependency**
No preceding function needs to be carried out.

> ### Introduction
> The Refund section includes a series of steps required for refunds, including requesting a refund quote, submitting the refund, and returning the refund status and results. This service supports the submission of requests for cancellation that require Atlas to process or for refunds that need to be executed by Atlas. It also allows a variety of cancellation and refund types, including voluntary, involuntary and void, etc.
> ### Features
>   - Refund reason: Voluntary, Involuntary, Void
>   - Service Level:
>      &#9702; Our refund quotations fall into three scenarios:
>        a. We can obtain an accurate quotation from the airline and will quote it directly to you;
>        b. We cannot obtain an accurate quotation through the airline. You can still submit the refund request, then we will process the refund, but the refund amount will be based on the actual amount refunded by the airline;
>        c. Unrefundable
>      &#9702; Our refund service includes the below steps,
>        a. Atlas submits the refund request to the airline: We provide a service time guarantee;
>        b. Airline processes the refund request and responds with the result, and airline executes the refund. The duration for 2 steps depends on the airline's processing speed, and we will provide an estimated reference time based on our experience in handling such cases.
> 
> Please note the below while initiating a refund transaction.
>   1. **Refund of either inbound or outbound sector**: The full ticket needs to be refunded. Only outbound OR inbound sector cannot be refunded. Please contact the airline for the same.
>   2. **Refund for a partially used itinerary**: Partially used itinerary cannot be refunded. Please contact the airline for the same.
>   3. **Refund for a specific passenger**: We support the refund of a specific passenger in an itinerary. For example, if there are 3 passengers and only one of them is to be refunded, please send us your refund request.
>   4. Apart from voluntary, involuntary and void, we currently do not support other types of refunds, such as medical or death refunds. Please contact customer service for manual assistance.
>   5. The customer is responsible to check whether the traveler has already made ancillary purchase in the transaction.
>   6. No email notifications will be sent for refunds rejected by Atlas.

**Endpoint:**
https://sandbox.atriptech.com/refundQuotation.do

> Body 请求参数

```json
{
  "orderNo": "TESTA20250512100600259",
  "airlinePNR": null,
  "carrier": null,
  "displayCurrency": "EUR",
  "refundRequestList": [
    {
      "lastName": "ZHAO",
      "firstName": "YIER",
      "segments": [
        {
          "depDate": "20250513",
          "flightNo": "U22437",
          "depAirport": "LTN",
          "arrAirport": "CDG"
        }
      ],
      "refundReason": "1"
    },
    {
      "lastName": "QIAN",
      "firstName": "ERER",
      "segments": [
        {
          "depDate": "20250513",
          "flightNo": "U22437",
          "depAirport": "LTN",
          "arrAirport": "CDG"
        }
      ],
      "refundReason": "1"
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
|» orderNo|body|string¦null| 是 |Atlas original order number.  You can choose to request either orderNo or both airlinePNR and carrier. If you use `orderNo`, the `airlinePNR` and `carrier` fields may be null.|
|» airlinePNR|body|string¦null| 是 |The record locator of the airline. You can choose to request either orderNo or both airlinePNR and carrier. If you use `airlinePNR` and `carrier`, the `orderNo`  field may be null.|
|» carrier|body|string¦null| 是 |2 character IATA airline code. you can choose to request either orderNo or both airlinePNR and carrier. If you use `airlinePNR` and `carrier`, the `orderNo`  field may be null.|
|» refundRequestList|body|[[RefundPaxSegments](#schemarefundpaxsegments)]| 是 |none|
|»» lastName|body|string| 是 |Last name of the passenger requesting a refund.|
|»» firstName|body|string| 是 |First name of the passenger requesting a refund.|
|»» segments|body|[[RefundSegment](#schemarefundsegment)]| 是 |none|
|»»» depDate|body|string(date)| 是 |Departure date of the segment which the passenger wants to refund. the format is `yyyyMMdd`.|
|»»» flightNo|body|string| 是 |Flight number of the segment which the passenger wants to refund.|
|»»» depAirport|body|string| 是 |3-letter IATA code of the departure airport.|
|»»» arrAirport|body|string| 是 |3-letter IATA code of the arrival airport.|
|»» refundReason|body|string| 是 |Code representing the reason for the refund request.|

#### 详细说明

**»» refundReason**: Code representing the reason for the refund request.
- 0: Involuntary
- 1: Voluntary
- 4: Void

#### 枚举值

|属性|值|
|---|---|
|»» refundReason|0|
|»» refundReason|1|
|»» refundReason|4|

> 返回示例

```json
{
  "displayCurrency": "EUR",
  "fastConfirmation": 0,
  "expectedConfirmationDate": "20250522",
  "expectedRefundDate": "20250701",
  "refundQuoteType": "CannotQuote",
  "refundOfferId": "q_b893711fcfae4e9d949e9965576bfd3a",
  "refundMethod": "CashBackToOriginalPayment",
  "isRefundable": false,
  "refundTickets": [
    {
      "name": "QIAN/ERER",
      "lastName": "QIAN",
      "firstName": "ERER",
      "ticketNo": "S87579"
    },
    {
      "name": "ZHAO/YIER",
      "lastName": "ZHAO",
      "firstName": "YIER",
      "ticketNo": "S87579"
    }
  ],
  "refundFareAmount": {
    "currency": "USD",
    "originalFareAmount": 165.48,
    "estimatedRefundAmount": 0,
    "displayOriginalFareAmount": 153.46,
    "displayEstimatedRefundAmount": 0
  },
  "refundPostTicketingServiceAmounts": [],
  "refundVouchers": null,
  "serviceFee": {
    "currency": "USD",
    "transactionFee": 2,
    "displayTransactionFee": 1.85
  },
  "refundRules": [
    {
      "airline": "U2",
      "ruleType": "1",
      "passengerType": null,
      "penaltyAmount": null,
      "penaltyPercent": null,
      "penaltyPercentBase": null,
      "airlineFee": null,
      "taxRefundable": false,
      "fareRefundable": false,
      "refundableAncillaries": null,
      "startMinute": 525600,
      "endMinute": -525600,
      "refundMethod": "CashBackToOriginalPayment"
    }
  ],
  "orderNo": "TESTA20250512100600259",
  "status": 0,
  "msg": null
}
```

```json
{
  "displayCurrency": "EUR",
  "fastConfirmation": 0,
  "expectedConfirmationDate": "20250522",
  "expectedRefundDate": "20250701",
  "refundQuoteType": "CannotQuote",
  "refundOfferId": "q_ae894a769bfc4ddda11e38b3cd8153f4",
  "refundMethod": "CashBackToOriginalPayment",
  "isRefundable": true,
  "refundTickets": [
    {
      "name": "QIAN/ERER",
      "lastName": "QIAN",
      "firstName": "ERER",
      "ticketNo": "S87579"
    },
    {
      "name": "ZHAO/YIER",
      "lastName": "ZHAO",
      "firstName": "YIER",
      "ticketNo": "S87579"
    }
  ],
  "refundFareAmount": {
    "currency": "USD",
    "originalFareAmount": 165.48,
    "estimatedRefundAmount": 165.48,
    "displayOriginalFareAmount": 153.46,
    "displayEstimatedRefundAmount": 153.46
  },
  "refundPostTicketingServiceAmounts": [],
  "refundVouchers": null,
  "serviceFee": {
    "currency": "USD",
    "transactionFee": 3,
    "displayTransactionFee": 2.78
  },
  "refundRules": [
    {
      "airline": "U2",
      "ruleType": "0",
      "passengerType": null,
      "penaltyAmount": "0.00 USD",
      "penaltyPercent": 0,
      "penaltyPercentBase": "fare+tax",
      "airlineFee": "0.00 USD",
      "taxRefundable": true,
      "fareRefundable": true,
      "refundableAncillaries": [
        "ALL"
      ],
      "startMinute": 525600,
      "endMinute": -525600,
      "refundMethod": "CashBackToOriginalPayment"
    }
  ],
  "orderNo": "TESTA20250512100600259",
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
|» status|integer|true|none||Status code. 0 for Success, 2 for System error.|
|» msg|string¦null|false|none||Error message<br />The ‘msg’ element is for description of the results. Please do not use this field to check the success or failure of the request. Only use the ‘status’ code to check the result.|
|» fastConfirmation|integer|true|none||Fast confirmation depends on whether the airline supports auto fulfillment.<br />0 for False, 1 for True.|
|» expectedConfirmationDate|string|true|none||Expected date of getting airline refund confirmation. The format is `yyyyMMdd`.|
|» expectedRefundDate|string|true|none||Expected date of getting refund. The format is `yyyyMMdd`.|
|» refundQuoteType|string|true|none||Type of refund quote:<br />- AccurateQuote：quotation based on the calculated amount.<br />- CannotQuote: quotation is unknown and will be according to the airline's rates|
|» refundOfferId|string|true|none||Refund offer id for this quotation which can be used for the coming refund call.|
|» refundMethod|string|true|none||Refund method: CashBackToOriginalPayment or Voucher.<br />- CashBackToOriginalPayment: Refund cash back to the original form of payment.<br />- Voucher: Refund in the form of a voucher.|
|» refundTickets|[[RefundTicket](#schemarefundticket)]|true|none||The refund calculation for each of the passengers whose refund quote has been requested|
|»» lastName|string|true|none||Last name of the passenger who wants to refund.|
|»» firstName|string|true|none||First name of the passenger who wants to refund.|
|»» ticketNo|string|true|none||The PNR received from the airline in the retrieve PNR response.|
|» refundFareAmount|[RefundFareAmount](#schemarefundfareamount)¦null|false|none||If `refundMethod` is CashBackToOriginalPayment, the `refundFareAmount` field is not null and the `refundVouchers` is null.|
|»» currency|string|true|none||The refund calculation for flight fare and inflow ancillaries.<br />3-letter ISO currency code.|
|»» originalFareAmount|number|true|none||Original fare of the flight.|
|»» estimatedRefundAmount|number|true|none||Estimated amount which can be got back for this refund of flight.|
|»» displayOriginalFareAmount|number¦null|false|none||Original Fare Amount in display currency.|
|»» displayEstimatedRefundAmount|number¦null|false|none||EstimatedRefundAmount in display currency.|
|» refundPostTicketingServiceAmounts|[RefundPostTicketingServiceAmount](#schemarefundpostticketingserviceamount)¦null|false|none||The refund calculation for Post-ticketing Servrice, including baggage etc. Each post-ticketing order will be present as an object.|
|»» postTicketingOrderNo|string|true|none||Unique order number for the post-ticketing service.|
|»» currency|string|true|none||Currency used for post-ticketing service calculations.<br />3-letter ISO currency code.|
|»» originalPostTicketingServiceAmount|number|true|none||The original amount charged for the post-ticketing service.|
|»» estimatedRefundAmount|number|true|none||Estimated amount which can be got back for this refund of Ancillaries.|
|»» displayPostTicketingServiceAmount|number¦null|false|none||The original post-ticketing service amount in the display currency.|
|»» displayEstimatedRefundAmount|number¦null|false|none||The estimated refund amount displayed in the display currency.|
|» refundVouchers|[[RefundVoucher](#schemarefundvoucher)]¦null|false|none||If `refundMethod` is Voucher, the `refundVouchers` is not null.|
|»» voucherId|string¦null|false|none||A unique identifier of Atlas used to distinguish different vouchers.|
|»» voucherCode|string¦null|false|none||The voucherCode airline returned.|
|»» eligiblePassengers|[object]|false|none||The passenger information eligible to use this voucher.|
|»»» name|string¦null|false|none||The eligible passenger’s name.|
|»» airline|string¦null|false|none||The airline from which the voucher originates.|
|»» estimatedRefundAmount|number|true|none||The amount value of the voucher.|
|»» currency|string|true|none||The currency type of the voucher.|
|»» voucherStartDate|string¦null|false|none||The date on which the voucher can begin to be used. Defaults to the date when the refund status is set to "Refunded". The format is `yyyyMMdd`.|
|»» voucherEndDate|string¦null|false|none||The expiry date of the voucher. The format is `yyyyMMdd`.|
|»» travelStartDate|string¦null|false|none||The actual travel start date. The format is `yyyyMMdd`.|
|»» travelEndDate|string¦null|false|none||The actual travel end date. The format is `yyyyMMdd`.|
|»» note|string¦null|false|none||A brief description or usage rule explanation for the voucher.|
|» serviceFee|object|true|none||Service fee of refund.|
|»» currency|string|true|none||Currency used for the service fee.<br />3-letter ISO currency code.|
|»» transactionFee|number|true|none||Transaction Fee of refund.|
|» refundRules|[[RefundRule](#schemarefundrule)]|false|none||The refund rules for the fare whose refund quote has been requested.|
|»» airline|string|true|none||Airline code for which the refund rule applies.<br /> 2-letter IATA airline code.|
|»» ruleType|string|true|none||Rule type.<br />0: Involuntary Refund<br />1: Voluntary Refund <br />2: Tax Refund<br />3: Special Refund<br />4: Void Refund|
|»» passengerType|string|false|none||Passenger type for which the refund rule applies.<br />Can be ADT (Adult), CHD (Child), INF (Infant).|
|»» penaltyAmount|string|false|none||The penalty amount charged for the refund.<br />Monetary value with currency code.|
|»» penaltyPercent|number|false|none||The percentage of the fare charged as penalty.|
|»» penaltyPercentBase|string|false|none||The calculation on which the penalty percentage is based.<br />Can be fare, fare+tax.|
|»» airlineFee|string|false|none||Additional airline fee for processing the refund.<br /> Monetary value with currency code.|
|»» taxRefundable|boolean|false|none||Indicates whether the tax is refundable is available.<br />true or false|
|»» fareRefundable|boolean|false|none||Indicates whether the ticket is refundable.<br />true or false.|
|»» refundableAncillaries|[string]|false|none||List of refundable ancillary services, if any.|
|»» startMinute|integer|false|none||Starting time of rule application. <br />Positive numbers represent XXX minutes before departure.<br />Negative numbers represent XXX minutes after departure.|
|»» endMinute|integer|false|none||Ending time of rule application. <br />Positive numbers represent XXX minutes before departure. <br />Negative numbers represent XXX minutes after departure.|
|»» refundMethod|string|false|none||Refund method:<br />CashBackToOriginalPayment or Voucher.<br />- CashBackToOriginalPayment: Refund cash back to the original form of payment<br />- Voucher: Refund in the form of a voucher|
|» orderNo|string|true|none||Original order number|
|» isRefundable|boolean|true|none||True : Refundable False: Non-Refundable<br />true or false|

#### 枚举值

|属性|值|
|---|---|
|status|0|
|status|2|
|fastConfirmation|0|
|fastConfirmation|1|
|refundQuoteType|AccurateQuote|
|refundQuoteType|CannotQuote|
|refundMethod|CashBackToOriginalPayment|
|refundMethod|Voucher|
|ruleType|0|
|ruleType|1|
|ruleType|2|
|ruleType|3|
|ruleType|4|
|passengerType|ADT|
|passengerType|CHD|
|passengerType|INF|
|penaltyPercentBase|fare|
|penaltyPercentBase|fare+tax|
|refundMethod|CashBackToOriginalPayment|
|refundMethod|Voucher|

## POST Make a Refund

POST /refund.do

**Dependency**
Refund quotation function should be called in prior of this call

**Endpoint:**
https://sandbox.atriptech.com/refund.do

> Body 请求参数

```json
{
  "orderNo": "TESTA20240725164512131",
  "airlinePNR": null,
  "carrier": null,
  "displayCurrency": "EUR",
  "refundOfferId": "q_a86cd9c605c04f9cb3890ca3b037b254",
  "refundRequestList": null
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
|» orderNo|body|string¦null| 是 |Atlas original order number.  You can choose to request either orderNo or both airlinePNR and carrier. If you use `orderNo`, the `airlinePNR` and `carrier` fields may be null.|
|» airlinePNR|body|string¦null| 是 |The record locator of the airline. You can choose to request either orderNo or both airlinePNR and carrier. If you use `airlinePNR` and `carrier`, the `orderNo`  field may be null.|
|» carrier|body|string¦null| 是 |2 character IATA airline code. you can choose to request either orderNo or both airlinePNR and carrier. If you use `airlinePNR` and `carrier`, the `orderNo`  field may be null.|
|» displayCurrency|body|string¦null| 否 |The alternative currency in which the fare and taxes amount needs to be displayed. The 3-letter currency code should be entered.|
|» refundOfferId|body|string¦null| 是 |Get this from the refund quotation response. You can request with refundOfferId or refundRequestList. If you use `refundRequestList`, the field `refundOfferId` is null.|
|» refundRequestList|body|[[RefundPaxSegments](#schemarefundpaxsegments)]¦null| 否 |You can request with refundOfferId or refundRequestList. If you use `refundOfferId`, the field `refundRequestList` is null.|
|»» lastName|body|string| 是 |Last name of the passenger requesting a refund.|
|»» firstName|body|string| 是 |First name of the passenger requesting a refund.|
|»» segments|body|[[RefundSegment](#schemarefundsegment)]| 是 |none|
|»»» depDate|body|string(date)| 是 |Departure date of the segment which the passenger wants to refund. the format is `yyyyMMdd`.|
|»»» flightNo|body|string| 是 |Flight number of the segment which the passenger wants to refund.|
|»»» depAirport|body|string| 是 |3-letter IATA code of the departure airport.|
|»»» arrAirport|body|string| 是 |3-letter IATA code of the arrival airport.|
|»» refundReason|body|string| 是 |Code representing the reason for the refund request.|

#### 详细说明

**»» refundReason**: Code representing the reason for the refund request.
- 0: Involuntary
- 1: Voluntary
- 4: Void

#### 枚举值

|属性|值|
|---|---|
|»» refundReason|0|
|»» refundReason|1|
|»» refundReason|4|

> 返回示例

```json
{
  "refundStatus": 0,
  "refundCode": "202505-0012",
  "cancelReason": "",
  "refundReason": "0",
  "displayCurrency": "EUR",
  "fastConfirmation": null,
  "expectedConfirmationDate": "20250522",
  "expectedRefundDate": "20250701",
  "refundQuoteType": "CannotQuote",
  "refundOfferId": "q_a86cd9c605c04f9cb3890ca3b037b254",
  "refundMethod": "CashBackToOriginalPayment",
  "isRefundable": true,
  "refundTickets": [
    {
      "lastName": "ZHAO",
      "firstName": "YIER",
      "ticketNo": "S87579"
    },
    {
      "lastName": "QIAN",
      "firstName": "ERER",
      "ticketNo": "S87579"
    }
  ],
  "refundFareAmount": {
    "currency": "USD",
    "originalFareAmount": 165.48,
    "estimatedRefundAmount": 165.48,
    "displayOriginalFareAmount": 153.46,
    "displayEstimatedRefundAmount": 153.46
  },
  "refundPostTicketingServiceAmounts": [],
  "refundVouchers": null,
  "serviceFee": {
    "currency": "USD",
    "transactionFee": 3,
    "displayTransactionFee": 2.78
  },
  "refundRules": [
    {
      "airline": "U2",
      "ruleType": "0",
      "passengerType": null,
      "penaltyAmount": "0.00 USD",
      "penaltyPercent": 0,
      "penaltyPercentBase": "fare+tax",
      "airlineFee": "0.00 USD",
      "taxRefundable": true,
      "fareRefundable": true,
      "refundableAncillaries": [
        "ALL"
      ],
      "startMinute": 525600,
      "endMinute": -525600,
      "refundMethod": "CashBackToOriginalPayment"
    }
  ],
  "orderNo": "TESTA20250512100600259",
  "status": 0,
  "msg": null
}
```

```json
{
  "refundStatus": 0,
  "refundCode": "202505-0013",
  "cancelReason": "",
  "refundReason": "0",
  "displayCurrency": "EUR",
  "fastConfirmation": null,
  "expectedConfirmationDate": "20250522",
  "expectedRefundDate": "20250701",
  "refundQuoteType": "CannotQuote",
  "refundOfferId": "q_6f99d2a1ffc74486be67a98772fa159d",
  "refundMethod": "CashBackToOriginalPayment",
  "isRefundable": true,
  "refundTickets": [
    {
      "lastName": "ZHAO",
      "firstName": "YIER",
      "ticketNo": "S87579"
    },
    {
      "lastName": "QIAN",
      "firstName": "ERER",
      "ticketNo": "S87579"
    }
  ],
  "refundFareAmount": {
    "currency": "USD",
    "originalFareAmount": 165.48,
    "estimatedRefundAmount": 165.48,
    "displayOriginalFareAmount": 153.46,
    "displayEstimatedRefundAmount": 153.46
  },
  "refundPostTicketingServiceAmounts": [],
  "refundVouchers": null,
  "serviceFee": {
    "currency": "USD",
    "transactionFee": 3,
    "displayTransactionFee": 2.78
  },
  "refundRules": [
    {
      "airline": "U2",
      "ruleType": "0",
      "passengerType": null,
      "penaltyAmount": "0.00 USD",
      "penaltyPercent": 0,
      "penaltyPercentBase": "fare+tax",
      "airlineFee": "0.00 USD",
      "taxRefundable": true,
      "fareRefundable": true,
      "refundableAncillaries": [
        "ALL"
      ],
      "startMinute": 525600,
      "endMinute": -525600,
      "refundMethod": "CashBackToOriginalPayment"
    }
  ],
  "orderNo": "TESTA20250512100600259",
  "status": 0,
  "msg": null
}
```

```json
{
  "refundStatus": 0,
  "refundCode": "202505-0014",
  "cancelReason": "",
  "refundReason": "0",
  "displayCurrency": "EUR",
  "fastConfirmation": null,
  "expectedConfirmationDate": "20250522",
  "expectedRefundDate": "20250701",
  "refundQuoteType": "CannotQuote",
  "refundOfferId": "q_b6acb29ec23b47148542172cba609054",
  "refundMethod": "CashBackToOriginalPayment",
  "isRefundable": true,
  "refundTickets": [
    {
      "lastName": "ZHAO",
      "firstName": "YIER",
      "ticketNo": "S87579"
    },
    {
      "lastName": "QIAN",
      "firstName": "ERER",
      "ticketNo": "S87579"
    }
  ],
  "refundFareAmount": {
    "currency": "USD",
    "originalFareAmount": 165.48,
    "estimatedRefundAmount": 165.48,
    "displayOriginalFareAmount": 153.46,
    "displayEstimatedRefundAmount": 153.46
  },
  "refundPostTicketingServiceAmounts": [],
  "refundVouchers": null,
  "serviceFee": {
    "currency": "USD",
    "transactionFee": 3,
    "displayTransactionFee": 2.78
  },
  "refundRules": [
    {
      "airline": "U2",
      "ruleType": "0",
      "passengerType": null,
      "penaltyAmount": "0.00 USD",
      "penaltyPercent": 0,
      "penaltyPercentBase": "fare+tax",
      "airlineFee": "0.00 USD",
      "taxRefundable": true,
      "fareRefundable": true,
      "refundableAncillaries": [
        "ALL"
      ],
      "startMinute": 525600,
      "endMinute": -525600,
      "refundMethod": "CashBackToOriginalPayment"
    }
  ],
  "orderNo": "TESTA20250512100600259",
  "status": 0,
  "msg": null
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|none|[ApiRefundApplyResponse](#schemaapirefundapplyresponse)|

## POST Query Refund Status

POST /queryRefundOrders.do

**Dependency**
No preceding function needs to be carried out.

**Endpoint:**
https://sandbox.atriptech.com/queryRefundOrders.do

> Body 请求参数

```json
{
  "refundCode": "202505-0013",
  "orderNo": "TESTA20250512100600259",
  "airlinePNR": null,
  "carrier": null,
  "displayCurrency": "EUR"
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
|» refundCode|body|string| 是 |The code of the refund transaction received in the refund.do response.|
|» orderNo|body|string¦null| 是 |Atlas original order number. You can choose to request either orderNo or both airlinePNR and carrier. If you use `orderNo`, the `airlinePNR` and `carrier` fields may be null.|
|» airlinePNR|body|string¦null| 是 |The record locator of the airline. You can choose to request either orderNo or both airlinePNR and carrier. If you use `airlinePNR` and `carrier`, the `orderNo`  field may be null.|
|» carrier|body|string¦null| 是 |2 character IATA airline code. you can choose to request either orderNo or both airlinePNR and carrier. If you use `airlinePNR` and `carrier`, the `orderNo`  field may be null.|
|» displayCurrency|body|string¦null| 否 |The alternative currency in which the fare and taxes amount needs to be displayed. The 3-letter currency code should be entered.|

> 返回示例

```json
{
  "refundOrders": [
    {
      "orderNo": "TESTA20250512100600259",
      "refundCode": "202505-0013",
      "displayCurrency": "EUR",
      "expectedConfirmationDate": null,
      "expectedRefundDate": null,
      "refundQuoteType": "CannotQuote",
      "refundTickets": [
        {
          "lastName": "ZHAO",
          "firstName": "YIER",
          "ticketNo": "S87579"
        },
        {
          "lastName": "QIAN",
          "firstName": "ERER",
          "ticketNo": "S87579"
        }
      ],
      "refundFareAmount": {
        "currency": "USD",
        "originalFareAmount": 165.48,
        "estimatedRefundAmount": 165.48,
        "displayOriginalFareAmount": 153.46,
        "displayEstimatedRefundAmount": 153.46
      },
      "refundPostTicketingServiceAmounts": [],
      "refundVouchers": null,
      "serviceFee": {
        "currency": "USD",
        "transactionFee": 3,
        "displayTransactionFee": 2.78
      },
      "refundRules": [],
      "refundStatus": 4,
      "cancelReason": "hahaha11111",
      "refundOfferId": "q_6f99d2a1ffc74486be67a98772fa159d",
      "refundMethod": "CashBackToOriginalPayment"
    }
  ],
  "status": 0,
  "msg": null
}
```

```json
{
  "refundOrders": [
    {
      "orderNo": "TESTA20250512100600259",
      "refundCode": "202505-0014",
      "displayCurrency": "EUR",
      "expectedConfirmationDate": "20250522",
      "expectedRefundDate": "20250701",
      "refundQuoteType": "CannotQuote",
      "refundTickets": [
        {
          "lastName": "ZHAO",
          "firstName": "YIER",
          "ticketNo": "S87579"
        },
        {
          "lastName": "QIAN",
          "firstName": "ERER",
          "ticketNo": "S87579"
        }
      ],
      "refundFareAmount": {
        "currency": "USD",
        "originalFareAmount": 165.48,
        "estimatedRefundAmount": 165.48,
        "displayOriginalFareAmount": 153.46,
        "displayEstimatedRefundAmount": 153.46
      },
      "refundPostTicketingServiceAmounts": [],
      "refundVouchers": null,
      "serviceFee": {
        "currency": "USD",
        "transactionFee": 3,
        "displayTransactionFee": 2.78
      },
      "refundRules": [],
      "refundStatus": 0,
      "cancelReason": "",
      "refundOfferId": "q_b6acb29ec23b47148542172cba609054",
      "refundMethod": "CashBackToOriginalPayment"
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
|» refundOrders|[[RefundOrder](#schemarefundorder)]|true|none||none|
|»» orderNo|string|true|none||Original order number|
|»» refundCode|string|true|none||Refund order number generated for this refund request|
|»» displayCurrency|string¦null|false|none||The alternative currency in which the fare and taxes amount needs to be displayed. The 3-letter currency code should be entered.|
|»» expectedConfirmationDate|string|true|none||Expected date of getting airline refund confirmation. The format is `yyyyMMdd`.|
|»» expectedRefundDate|string|true|none||Expected date of getting refund. The format is `yyyyMMdd`.|
|»» refundQuoteType|string|true|none||Type of refund quote:<br />AccurateQuote：quotation based on the calculated amount.<br />CannotQuote: quotation is unknown and will be according to the airline's rates|
|»» refundTickets|[[RefundTicket](#schemarefundticket)]|true|none||The refund calculation for each of the passengers whose refund quote has been requested|
|»»» lastName|string|true|none||Last name of the passenger who wants to refund.|
|»»» firstName|string|true|none||First name of the passenger who wants to refund.|
|»»» ticketNo|string|true|none||The PNR received from the airline in the retrieve PNR response.|
|»» refundFareAmount|[RefundFareAmount](#schemarefundfareamount)¦null|false|none||If `refundMethod` is CashBackToOriginalPayment, the `refundFareAmount` field is not null.|
|»»» currency|string|true|none||The refund calculation for flight fare and inflow ancillaries.<br />3-letter ISO currency code.|
|»»» originalFareAmount|number|true|none||Original fare of the flight.|
|»»» estimatedRefundAmount|number|true|none||Estimated amount which can be got back for this refund of flight.|
|»»» displayOriginalFareAmount|number¦null|false|none||Original Fare Amount in display currency.|
|»»» displayEstimatedRefundAmount|number¦null|false|none||EstimatedRefundAmount in display currency.|
|»» refundPostTicketingServiceAmounts|[[RefundPostTicketingServiceAmount](#schemarefundpostticketingserviceamount)]¦null|false|none||The refund calculation for Post-ticketing Servrice, including baggage etc. Each post-ticketing order will be present as an object.|
|»»» postTicketingOrderNo|string|true|none||Unique order number for the post-ticketing service.|
|»»» currency|string|true|none||Currency used for post-ticketing service calculations.<br />3-letter ISO currency code.|
|»»» originalPostTicketingServiceAmount|number|true|none||The original amount charged for the post-ticketing service.|
|»»» estimatedRefundAmount|number|true|none||Estimated amount which can be got back for this refund of Ancillaries.|
|»»» displayPostTicketingServiceAmount|number¦null|false|none||The original post-ticketing service amount in the display currency.|
|»»» displayEstimatedRefundAmount|number¦null|false|none||The estimated refund amount displayed in the display currency.|
|»» refundVouchers|[[RefundVoucher](#schemarefundvoucher)]¦null|false|none||If `refundMethod` is Voucher,  the `refundVouchers` field is not null.|
|»»» voucherId|string¦null|false|none||A unique identifier of Atlas used to distinguish different vouchers.|
|»»» voucherCode|string¦null|false|none||The voucherCode airline returned.|
|»»» eligiblePassengers|[object]|false|none||The passenger information eligible to use this voucher.|
|»»»» name|string¦null|false|none||The eligible passenger’s name.|
|»»» airline|string¦null|false|none||The airline from which the voucher originates.|
|»»» estimatedRefundAmount|number|true|none||The amount value of the voucher.|
|»»» currency|string|true|none||The currency type of the voucher.|
|»»» voucherStartDate|string¦null|false|none||The date on which the voucher can begin to be used. Defaults to the date when the refund status is set to "Refunded". The format is `yyyyMMdd`.|
|»»» voucherEndDate|string¦null|false|none||The expiry date of the voucher. The format is `yyyyMMdd`.|
|»»» travelStartDate|string¦null|false|none||The actual travel start date. The format is `yyyyMMdd`.|
|»»» travelEndDate|string¦null|false|none||The actual travel end date. The format is `yyyyMMdd`.|
|»»» note|string¦null|false|none||A brief description or usage rule explanation for the voucher.|
|»» serviceFee|[ServiceFee](#schemaservicefee)|true|none||Service fee of refund.|
|»»» currency|string|true|none||Currency used for the service fee.<br />3-letter ISO currency code.|
|»»» transactionFee|number|true|none||Transaction Fee of refund.|
|»»» displayTransactionFee|number¦null|false|none||TransactionFee in display currency.|
|»» refundRules|[[RefundRule](#schemarefundrule)]|true|none||The refund rules for the fare whose refund quote has been requested.|
|»»» airline|string|true|none||Airline code for which the refund rule applies.<br /> 2-letter IATA airline code.|
|»»» ruleType|string|true|none||Rule type.<br />0: Involuntary Refund<br />1: Voluntary Refund <br />2: Tax Refund<br />3: Special Refund<br />4: Void Refund|
|»»» passengerType|string|false|none||Passenger type for which the refund rule applies.<br />Can be ADT (Adult), CHD (Child), INF (Infant).|
|»»» penaltyAmount|string|false|none||The penalty amount charged for the refund.<br />Monetary value with currency code.|
|»»» penaltyPercent|number|false|none||The percentage of the fare charged as penalty.|
|»»» penaltyPercentBase|string|false|none||The calculation on which the penalty percentage is based.<br />Can be fare, fare+tax.|
|»»» airlineFee|string|false|none||Additional airline fee for processing the refund.<br /> Monetary value with currency code.|
|»»» taxRefundable|boolean|false|none||Indicates whether the tax is refundable is available.<br />true or false|
|»»» fareRefundable|boolean|false|none||Indicates whether the ticket is refundable.<br />true or false.|
|»»» refundableAncillaries|[string]|false|none||List of refundable ancillary services, if any.|
|»»» startMinute|integer|false|none||Starting time of rule application. <br />Positive numbers represent XXX minutes before departure.<br />Negative numbers represent XXX minutes after departure.|
|»»» endMinute|integer|false|none||Ending time of rule application. <br />Positive numbers represent XXX minutes before departure. <br />Negative numbers represent XXX minutes after departure.|
|»»» refundMethod|string|false|none||Refund method:<br />CashBackToOriginalPayment or Voucher.<br />- CashBackToOriginalPayment: Refund cash back to the original form of payment<br />- Voucher: Refund in the form of a voucher|
|»» refundStatus|integer|true|none||The present status of the refund.<br />The options are:<br />0: Atlas Processing<br />1: Airline Processing (Submitted to airline by Atlas)<br />2: Refunded<br />3: Airline Refunding<br />4: Rejected<br />5: Fullfillment Done<br />6: Withdrew<br />If the ticket is paid by deposit: the status can be 0,1,2,3,4<br />If the ticket is paid by VCC pass through: the status can be 0,1,4,5,6<br />Withdrew is only in the refund claim|
|»» cancelReason|string¦null|false|none||The reason why the refund was cancelled.<br />The refund reasons are:<br />Does not match airline policy.<br />There is no schedule change from the airline side. \nPlease refer the ticket Fare Rules available in ATRIP flight deck for cancellation charges.<br />Voluntary Cancellation - Non-Refundable<br />As per airline policy, only voucher refund is available for the ticket<br />Refund request cancelled by the user<br />Travel has been completed by the passenger.<br />Refund not yet received from the airline. Please try again later.<br />The order is paid by your VCC. please refund by yourself<br />It's issued via your B2B account, please refund by yourself<br />Refund is availalbe through airline's B2C website. Please refund by yourself.<br />The refund claim voucher is invalid.<br />Duplicate Refund Record<br />Need to provide more materials that meet airline requirements<br />Actual refund amount less than service fee. Will reject it.|
|»» refundOfferId|string|true|none||Refund offer id for this quotation which can be used for the coming refund call.|
|»» refundMethod|string|true|none||Refund method: CashBackToOriginalPayment or Voucher|
|» status|integer|true|none||Status code. 0 for Success, 2 for System error.|
|» msg|string¦null|false|none||Error message|

#### 枚举值

|属性|值|
|---|---|
|refundQuoteType|AccurateQuote|
|refundQuoteType|CannotQuote|
|ruleType|0|
|ruleType|1|
|ruleType|2|
|ruleType|3|
|ruleType|4|
|passengerType|ADT|
|passengerType|CHD|
|passengerType|INF|
|penaltyPercentBase|fare|
|penaltyPercentBase|fare+tax|
|refundMethod|CashBackToOriginalPayment|
|refundMethod|Voucher|
|refundStatus|0|
|refundStatus|1|
|refundStatus|2|
|refundStatus|3|
|refundStatus|4|
|refundStatus|5|
|refundStatus|6|

# 数据模型

<h2 id="tocS_RefundSegment">RefundSegment</h2>

<a id="schemarefundsegment"></a>
<a id="schema_RefundSegment"></a>
<a id="tocSrefundsegment"></a>
<a id="tocsrefundsegment"></a>

```json
{
  "depDate": "2019-08-24",
  "flightNo": "string",
  "depAirport": "string",
  "arrAirport": "string"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|depDate|string(date)|true|none||Departure date of the segment which the passenger wants to refund. the format is `yyyyMMdd`.|
|flightNo|string|true|none||Flight number of the segment which the passenger wants to refund.|
|depAirport|string|true|none||3-letter IATA code of the departure airport.|
|arrAirport|string|true|none||3-letter IATA code of the arrival airport.|

<h2 id="tocS_RefundPaxSegments">RefundPaxSegments</h2>

<a id="schemarefundpaxsegments"></a>
<a id="schema_RefundPaxSegments"></a>
<a id="tocSrefundpaxsegments"></a>
<a id="tocsrefundpaxsegments"></a>

```json
{
  "lastName": "string",
  "firstName": "string",
  "segments": [
    {
      "depDate": "2019-08-24",
      "flightNo": "string",
      "depAirport": "string",
      "arrAirport": "string"
    }
  ],
  "refundReason": "0"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|lastName|string|true|none||Last name of the passenger requesting a refund.|
|firstName|string|true|none||First name of the passenger requesting a refund.|
|segments|[[RefundSegment](#schemarefundsegment)]|true|none||none|
|refundReason|string|true|none||Code representing the reason for the refund request.<br />- 0: Involuntary<br />- 1: Voluntary<br />- 4: Void|

#### 枚举值

|属性|值|
|---|---|
|refundReason|0|
|refundReason|1|
|refundReason|4|

<h2 id="tocS_ApiRefundQuotationRequest">ApiRefundQuotationRequest</h2>

<a id="schemaapirefundquotationrequest"></a>
<a id="schema_ApiRefundQuotationRequest"></a>
<a id="tocSapirefundquotationrequest"></a>
<a id="tocsapirefundquotationrequest"></a>

```json
{
  "orderNo": "string",
  "airlinePNR": "string",
  "carrier": "string",
  "displayCurrency": "string",
  "refundRequestList": [
    {
      "lastName": "string",
      "firstName": "string",
      "segments": [
        {
          "depDate": "2019-08-24",
          "flightNo": "string",
          "depAirport": "string",
          "arrAirport": "string"
        }
      ],
      "refundReason": "0"
    }
  ]
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|orderNo|string¦null|true|none||Atlas original order number.  You can choose to request either orderNo or both airlinePNR and carrier. If you use `orderNo`, the `airlinePNR` and `carrier` fields may be null.|
|airlinePNR|string¦null|true|none||The record locator of the airline. You can choose to request either orderNo or both airlinePNR and carrier. If you use `airlinePNR` and `carrier`, the `orderNo`  field may be null.|
|carrier|string¦null|true|none||2 character IATA airline code. you can choose to request either orderNo or both airlinePNR and carrier. If you use `airlinePNR` and `carrier`, the `orderNo`  field may be null.|
|displayCurrency|string|false|none||The alternative currency in which the fare and taxes amount needs to be displayed. The 3-letter currency code should be entered.|
|refundRequestList|[[RefundPaxSegments](#schemarefundpaxsegments)]|true|none||none|

<h2 id="tocS_ServiceFee">ServiceFee</h2>

<a id="schemaservicefee"></a>
<a id="schema_ServiceFee"></a>
<a id="tocSservicefee"></a>
<a id="tocsservicefee"></a>

```json
{
  "currency": "string",
  "transactionFee": 0,
  "displayTransactionFee": 0
}

```

Service fee of refund.

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|currency|string|true|none||Currency used for the service fee.<br />3-letter ISO currency code.|
|transactionFee|number|true|none||Transaction Fee of refund.|
|displayTransactionFee|number¦null|false|none||TransactionFee in display currency.|

<h2 id="tocS_RefundVoucher">RefundVoucher</h2>

<a id="schemarefundvoucher"></a>
<a id="schema_RefundVoucher"></a>
<a id="tocSrefundvoucher"></a>
<a id="tocsrefundvoucher"></a>

```json
{
  "voucherId": "string",
  "voucherCode": "string",
  "eligiblePassengers": [
    {
      "name": "ZHANG/SAN"
    }
  ],
  "airline": "string",
  "estimatedRefundAmount": 0,
  "currency": "string",
  "voucherStartDate": "string",
  "voucherEndDate": "string",
  "travelStartDate": "string",
  "travelEndDate": "string",
  "note": "string"
}

```

Information about the voucher refund.

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|voucherId|string¦null|false|none||A unique identifier of Atlas used to distinguish different vouchers.|
|voucherCode|string¦null|false|none||The voucherCode airline returned.|
|eligiblePassengers|[object]|false|none||The passenger information eligible to use this voucher.|
|» name|string¦null|false|none||The eligible passenger’s name.|
|airline|string¦null|false|none||The airline from which the voucher originates.|
|estimatedRefundAmount|number|true|none||The amount value of the voucher.|
|currency|string|true|none||The currency type of the voucher.|
|voucherStartDate|string¦null|false|none||The date on which the voucher can begin to be used. Defaults to the date when the refund status is set to "Refunded". The format is `yyyyMMdd`.|
|voucherEndDate|string¦null|false|none||The expiry date of the voucher. The format is `yyyyMMdd`.|
|travelStartDate|string¦null|false|none||The actual travel start date. The format is `yyyyMMdd`.|
|travelEndDate|string¦null|false|none||The actual travel end date. The format is `yyyyMMdd`.|
|note|string¦null|false|none||A brief description or usage rule explanation for the voucher.|

<h2 id="tocS_RefundPostTicketingServiceAmount">RefundPostTicketingServiceAmount</h2>

<a id="schemarefundpostticketingserviceamount"></a>
<a id="schema_RefundPostTicketingServiceAmount"></a>
<a id="tocSrefundpostticketingserviceamount"></a>
<a id="tocsrefundpostticketingserviceamount"></a>

```json
{
  "postTicketingOrderNo": "string",
  "currency": "string",
  "originalPostTicketingServiceAmount": 0,
  "estimatedRefundAmount": 0,
  "displayPostTicketingServiceAmount": 0,
  "displayEstimatedRefundAmount": 0
}

```

The refund calculation for Post-ticketing Servrice, including baggage

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|postTicketingOrderNo|string|true|none||Unique order number for the post-ticketing service.|
|currency|string|true|none||Currency used for post-ticketing service calculations.<br />3-letter ISO currency code.|
|originalPostTicketingServiceAmount|number|true|none||The original amount charged for the post-ticketing service.|
|estimatedRefundAmount|number|true|none||Estimated amount which can be got back for this refund of Ancillaries.|
|displayPostTicketingServiceAmount|number¦null|false|none||The original post-ticketing service amount in the display currency.|
|displayEstimatedRefundAmount|number¦null|false|none||The estimated refund amount displayed in the display currency.|

<h2 id="tocS_RefundFareAmount">RefundFareAmount</h2>

<a id="schemarefundfareamount"></a>
<a id="schema_RefundFareAmount"></a>
<a id="tocSrefundfareamount"></a>
<a id="tocsrefundfareamount"></a>

```json
{
  "currency": "string",
  "originalFareAmount": 0,
  "estimatedRefundAmount": 0,
  "displayOriginalFareAmount": 0,
  "displayEstimatedRefundAmount": 0
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|currency|string|true|none||The refund calculation for flight fare and inflow ancillaries.<br />3-letter ISO currency code.|
|originalFareAmount|number|true|none||Original fare of the flight.|
|estimatedRefundAmount|number|true|none||Estimated amount which can be got back for this refund of flight.|
|displayOriginalFareAmount|number¦null|false|none||Original Fare Amount in display currency.|
|displayEstimatedRefundAmount|number¦null|false|none||EstimatedRefundAmount in display currency.|

<h2 id="tocS_RefundTicket">RefundTicket</h2>

<a id="schemarefundticket"></a>
<a id="schema_RefundTicket"></a>
<a id="tocSrefundticket"></a>
<a id="tocsrefundticket"></a>

```json
{
  "lastName": "string",
  "firstName": "string",
  "ticketNo": "string"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|lastName|string|true|none||Last name of the passenger who wants to refund.|
|firstName|string|true|none||First name of the passenger who wants to refund.|
|ticketNo|string|true|none||The PNR received from the airline in the retrieve PNR response.|

<h2 id="tocS_RefundRule">RefundRule</h2>

<a id="schemarefundrule"></a>
<a id="schema_RefundRule"></a>
<a id="tocSrefundrule"></a>
<a id="tocsrefundrule"></a>

```json
{
  "airline": "string",
  "ruleType": "0",
  "passengerType": "ADT",
  "penaltyAmount": "string",
  "penaltyPercent": 0,
  "penaltyPercentBase": "fare",
  "airlineFee": "string",
  "taxRefundable": true,
  "fareRefundable": true,
  "refundableAncillaries": [
    "StandardCheckInBaggage"
  ],
  "startMinute": 0,
  "endMinute": 0,
  "refundMethod": "CashBackToOriginalPayment"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|airline|string|true|none||Airline code for which the refund rule applies.<br /> 2-letter IATA airline code.|
|ruleType|string|true|none||Rule type.<br />0: Involuntary Refund<br />1: Voluntary Refund <br />2: Tax Refund<br />3: Special Refund<br />4: Void Refund|
|passengerType|string|false|none||Passenger type for which the refund rule applies.<br />Can be ADT (Adult), CHD (Child), INF (Infant).|
|penaltyAmount|string|false|none||The penalty amount charged for the refund.<br />Monetary value with currency code.|
|penaltyPercent|number|false|none||The percentage of the fare charged as penalty.|
|penaltyPercentBase|string|false|none||The calculation on which the penalty percentage is based.<br />Can be fare, fare+tax.|
|airlineFee|string|false|none||Additional airline fee for processing the refund.<br /> Monetary value with currency code.|
|taxRefundable|boolean|false|none||Indicates whether the tax is refundable is available.<br />true or false|
|fareRefundable|boolean|false|none||Indicates whether the ticket is refundable.<br />true or false.|
|refundableAncillaries|[string]|false|none||List of refundable ancillary services, if any.|
|startMinute|integer|false|none||Starting time of rule application. <br />Positive numbers represent XXX minutes before departure.<br />Negative numbers represent XXX minutes after departure.|
|endMinute|integer|false|none||Ending time of rule application. <br />Positive numbers represent XXX minutes before departure. <br />Negative numbers represent XXX minutes after departure.|
|refundMethod|string|false|none||Refund method:<br />CashBackToOriginalPayment or Voucher.<br />- CashBackToOriginalPayment: Refund cash back to the original form of payment<br />- Voucher: Refund in the form of a voucher|

#### 枚举值

|属性|值|
|---|---|
|ruleType|0|
|ruleType|1|
|ruleType|2|
|ruleType|3|
|ruleType|4|
|passengerType|ADT|
|passengerType|CHD|
|passengerType|INF|
|penaltyPercentBase|fare|
|penaltyPercentBase|fare+tax|
|refundMethod|CashBackToOriginalPayment|
|refundMethod|Voucher|

<h2 id="tocS_ApiRefundQuotationResponse">ApiRefundQuotationResponse</h2>

<a id="schemaapirefundquotationresponse"></a>
<a id="schema_ApiRefundQuotationResponse"></a>
<a id="tocSapirefundquotationresponse"></a>
<a id="tocsapirefundquotationresponse"></a>

```json
{
  "status": 0,
  "msg": "string",
  "displayCurrency": "string",
  "fastConfirmation": 0,
  "expectedConfirmationDate": "20241217",
  "expectedRefundDate": "string",
  "refundQuoteType": "AccurateQuote",
  "refundOfferId": "string",
  "refundMethod": "CashBackToOriginalPayment",
  "refundTickets": [
    {
      "lastName": "string",
      "firstName": "string",
      "ticketNo": "string"
    }
  ],
  "refundFareAmount": {
    "currency": "string",
    "originalFareAmount": 0,
    "estimatedRefundAmount": 0,
    "displayOriginalFareAmount": 0,
    "displayEstimatedRefundAmount": 0
  },
  "refundPostTicketingServiceAmounts": {
    "postTicketingOrderNo": "string",
    "currency": "string",
    "originalPostTicketingServiceAmount": 0,
    "estimatedRefundAmount": 0,
    "displayPostTicketingServiceAmount": 0,
    "displayEstimatedRefundAmount": 0
  },
  "refundVouchers": [
    {
      "voucherId": "string",
      "voucherCode": "string",
      "eligiblePassengers": [
        {
          "name": "ZHANG/SAN"
        }
      ],
      "airline": "string",
      "estimatedRefundAmount": 0,
      "currency": "string",
      "voucherStartDate": "string",
      "voucherEndDate": "string",
      "travelStartDate": "string",
      "travelEndDate": "string",
      "note": "string"
    }
  ],
  "serviceFee": {
    "currency": "string",
    "transactionFee": 0,
    "displayTransactionFee": 0
  },
  "refundRules": [
    {
      "airline": "string",
      "ruleType": "0",
      "passengerType": "ADT",
      "penaltyAmount": "string",
      "penaltyPercent": 0,
      "penaltyPercentBase": "fare",
      "airlineFee": "string",
      "taxRefundable": true,
      "fareRefundable": true,
      "refundableAncillaries": [
        "StandardCheckInBaggage"
      ],
      "startMinute": 0,
      "endMinute": 0,
      "refundMethod": "CashBackToOriginalPayment"
    }
  ],
  "orderNo": "string",
  "isRefundable": true
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|status|integer|true|none||Status code. 0 for Success, 2 for System error.|
|msg|string¦null|false|none||Error message<br />The ‘msg’ element is for description of the results. Please do not use this field to check the success or failure of the request. Only use the ‘status’ code to check the result.|
|displayCurrency|string¦null|false|none||The alternative currency in which the fare and taxes amount needs to be displayed. The 3-letter currency code should be entered.|
|fastConfirmation|integer|true|none||Fast confirmation depends on whether the airline supports auto fulfillment.<br />0 for False, 1 for True.|
|expectedConfirmationDate|string|true|none||Expected date of getting airline refund confirmation. The format is `yyyyMMdd`.|
|expectedRefundDate|string|true|none||Expected date of getting refund. The format is `yyyyMMdd`.|
|refundQuoteType|string|true|none||Type of refund quote:<br />- AccurateQuote：quotation based on the calculated amount.<br />- CannotQuote: quotation is unknown and will be according to the airline's rates|
|refundOfferId|string|true|none||Refund offer id for this quotation which can be used for the coming refund call.|
|refundMethod|string|true|none||Refund method: CashBackToOriginalPayment or Voucher.<br />- CashBackToOriginalPayment: Refund cash back to the original form of payment.<br />- Voucher: Refund in the form of a voucher.|
|refundTickets|[[RefundTicket](#schemarefundticket)]|true|none||The refund calculation for each of the passengers whose refund quote has been requested|
|refundFareAmount|[RefundFareAmount](#schemarefundfareamount)|false|none||If `refundMethod` is CashBackToOriginalPayment, the `refundFareAmount` field is not null and the `refundVouchers` is null.|
|refundPostTicketingServiceAmounts|[RefundPostTicketingServiceAmount](#schemarefundpostticketingserviceamount)|false|none||The refund calculation for Post-ticketing Servrice, including baggage etc. Each post-ticketing order will be present as an object.|
|refundVouchers|[[RefundVoucher](#schemarefundvoucher)]¦null|false|none||If `refundMethod` is Voucher, the `refundVouchers` is not null.|
|serviceFee|[ServiceFee](#schemaservicefee)|true|none||Service fee of refund.|
|refundRules|[[RefundRule](#schemarefundrule)]|false|none||The refund rules for the fare whose refund quote has been requested.|
|orderNo|string|true|none||Original order number|
|isRefundable|boolean|true|none||True : Refundable False: Non-Refundable<br />true or false|

#### 枚举值

|属性|值|
|---|---|
|status|0|
|status|2|
|fastConfirmation|0|
|fastConfirmation|1|
|refundQuoteType|AccurateQuote|
|refundQuoteType|CannotQuote|
|refundMethod|CashBackToOriginalPayment|
|refundMethod|Voucher|

<h2 id="tocS_ApiRefundApplyRequest">ApiRefundApplyRequest</h2>

<a id="schemaapirefundapplyrequest"></a>
<a id="schema_ApiRefundApplyRequest"></a>
<a id="tocSapirefundapplyrequest"></a>
<a id="tocsapirefundapplyrequest"></a>

```json
{
  "orderNo": "string",
  "airlinePNR": "string",
  "carrier": "string",
  "displayCurrency": "string",
  "refundOfferId": "string",
  "refundRequestList": [
    {
      "lastName": "string",
      "firstName": "string",
      "segments": [
        {
          "depDate": "2019-08-24",
          "flightNo": "string",
          "depAirport": "string",
          "arrAirport": "string"
        }
      ],
      "refundReason": "0"
    }
  ]
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|orderNo|string¦null|true|none||Atlas original order number.  You can choose to request either orderNo or both airlinePNR and carrier. If you use `orderNo`, the `airlinePNR` and `carrier` fields may be null.|
|airlinePNR|string¦null|true|none||The record locator of the airline. You can choose to request either orderNo or both airlinePNR and carrier. If you use `airlinePNR` and `carrier`, the `orderNo`  field may be null.|
|carrier|string¦null|true|none||2 character IATA airline code. you can choose to request either orderNo or both airlinePNR and carrier. If you use `airlinePNR` and `carrier`, the `orderNo`  field may be null.|
|displayCurrency|string¦null|false|none||The alternative currency in which the fare and taxes amount needs to be displayed. The 3-letter currency code should be entered.|
|refundOfferId|string¦null|true|none||Get this from the refund quotation response. You can request with refundOfferId or refundRequestList. If you use `refundRequestList`, the field `refundOfferId` is null.|
|refundRequestList|[[RefundPaxSegments](#schemarefundpaxsegments)]¦null|true|none||You can request with refundOfferId or refundRequestList. If you use `refundOfferId`, the field `refundRequestList` is null.|

<h2 id="tocS_ApiRefundApplyResponse">ApiRefundApplyResponse</h2>

<a id="schemaapirefundapplyresponse"></a>
<a id="schema_ApiRefundApplyResponse"></a>
<a id="tocSapirefundapplyresponse"></a>
<a id="tocsapirefundapplyresponse"></a>

```json
{
  "status": 0,
  "msg": "string",
  "displayCurrency": "string",
  "fastConfirmation": 0,
  "expectedConfirmationDate": "20241217",
  "expectedRefundDate": "string",
  "refundQuoteType": "AccurateQuote",
  "refundOfferId": "string",
  "refundMethod": "CashBackToOriginalPayment",
  "refundTickets": [
    {
      "lastName": "string",
      "firstName": "string",
      "ticketNo": "string"
    }
  ],
  "refundFareAmount": {
    "currency": "string",
    "originalFareAmount": 0,
    "estimatedRefundAmount": 0,
    "displayOriginalFareAmount": 0,
    "displayEstimatedRefundAmount": 0
  },
  "refundPostTicketingServiceAmounts": {
    "postTicketingOrderNo": "string",
    "currency": "string",
    "originalPostTicketingServiceAmount": 0,
    "estimatedRefundAmount": 0,
    "displayPostTicketingServiceAmount": 0,
    "displayEstimatedRefundAmount": 0
  },
  "refundVouchers": [
    {
      "voucherId": "string",
      "voucherCode": "string",
      "eligiblePassengers": [
        {
          "name": "ZHANG/SAN"
        }
      ],
      "airline": "string",
      "estimatedRefundAmount": 0,
      "currency": "string",
      "voucherStartDate": "string",
      "voucherEndDate": "string",
      "travelStartDate": "string",
      "travelEndDate": "string",
      "note": "string"
    }
  ],
  "serviceFee": {
    "currency": "string",
    "transactionFee": 0,
    "displayTransactionFee": 0
  },
  "refundRules": [
    {
      "airline": "string",
      "ruleType": "0",
      "passengerType": "ADT",
      "penaltyAmount": "string",
      "penaltyPercent": 0,
      "penaltyPercentBase": "fare",
      "airlineFee": "string",
      "taxRefundable": true,
      "fareRefundable": true,
      "refundableAncillaries": [
        "StandardCheckInBaggage"
      ],
      "startMinute": 0,
      "endMinute": 0,
      "refundMethod": "CashBackToOriginalPayment"
    }
  ],
  "orderNo": "string",
  "isRefundable": true,
  "refundStatus": 0,
  "refundCode": "string",
  "cancelReason": "string",
  "refundReason": "0"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|status|integer|true|none||Status code. 0 for Success, 2 for System error.|
|msg|string¦null|false|none||Error message<br />The ‘msg’ element is for description of the results. Please do not use this field to check the success or failure of the request. Only use the ‘status’ code to check the result.|
|displayCurrency|string¦null|false|none||The alternative currency in which the fare and taxes amount needs to be displayed. The 3-letter currency code should be entered.|
|fastConfirmation|integer|true|none||Fast confirmation depends on whether the airline supports auto fulfillment.<br />0 for False, 1 for True.|
|expectedConfirmationDate|string|true|none||Expected date of getting airline refund confirmation. The format is `yyyyMMdd`.|
|expectedRefundDate|string|true|none||Expected date of getting refund. The format is `yyyyMMdd`.|
|refundQuoteType|string|true|none||Type of refund quote:<br />- AccurateQuote：quotation based on the calculated amount.<br />- CannotQuote: quotation is unknown and will be according to the airline's rates|
|refundOfferId|string|true|none||Refund offer id for this quotation which can be used for the coming refund call.|
|refundMethod|string|true|none||Refund method: CashBackToOriginalPayment or Voucher.<br />- CashBackToOriginalPayment: Refund cash back to the original form of payment.<br />- Voucher: Refund in the form of a voucher.|
|refundTickets|[[RefundTicket](#schemarefundticket)]|true|none||The refund calculation for each of the passengers whose refund quote has been requested|
|refundFareAmount|[RefundFareAmount](#schemarefundfareamount)|false|none||If `refundMethod` is CashBackToOriginalPayment, the `refundFareAmount` field is not null and the `refundVouchers` is null.|
|refundPostTicketingServiceAmounts|[RefundPostTicketingServiceAmount](#schemarefundpostticketingserviceamount)|false|none||The refund calculation for Post-ticketing Servrice, including baggage etc. Each post-ticketing order will be present as an object.|
|refundVouchers|[[RefundVoucher](#schemarefundvoucher)]¦null|false|none||If `refundMethod` is Voucher, the `refundVouchers` is not null.|
|serviceFee|[ServiceFee](#schemaservicefee)|true|none||Service fee of refund.|
|refundRules|[[RefundRule](#schemarefundrule)]|false|none||The refund rules for the fare whose refund quote has been requested.|
|orderNo|string|true|none||Original order number|
|isRefundable|boolean|true|none||True : Refundable False: Non-Refundable<br />true or false|
|refundStatus|integer|true|none||The present status of the refund.<br />The options are:<br />0: Atlas Processing<br />1: Airline Processing (Submitted to airline by Atlas)<br />2: Refunded<br />3: Airline Refunding<br />4: Rejected<br />5: Fullfillment Done<br />6: Withdrew<br />If the ticket is paid by deposit: the status can be 0,1,2,3,4<br />If the ticket is paid by VCC pass through: the status can be 0,1,4,5,6<br />Withdrew is only in the refund claim|
|refundCode|string|true|none||Refund order number generated for this refund request|
|cancelReason|string¦null|false|none||The reason why the refund was cancelled.<br />The refund reasons are:<br />Does not match airline policy<br />There is no schedule change from the airline side. Please refer the ticket Fare Rules available in ATRIP flight deck for cancellation charges.<br />Voluntary Cancellation - Non-Refundable<br />As per airline policy, only voucher refund is available for the ticket<br />Refund request cancelled by the user<br />Travel has been completed by the passenger<br />Refund not yet received from the airline. Please try again later.|
|refundReason|string¦null|false|none||Refund reason<br />0: Involuntary<br />1: Voluntary<br />4: Void|

#### 枚举值

|属性|值|
|---|---|
|status|0|
|status|2|
|fastConfirmation|0|
|fastConfirmation|1|
|refundQuoteType|AccurateQuote|
|refundQuoteType|CannotQuote|
|refundMethod|CashBackToOriginalPayment|
|refundMethod|Voucher|
|refundReason|0|
|refundReason|1|
|refundReason|4|

<h2 id="tocS_RefundOrder">RefundOrder</h2>

<a id="schemarefundorder"></a>
<a id="schema_RefundOrder"></a>
<a id="tocSrefundorder"></a>
<a id="tocsrefundorder"></a>

```json
{
  "orderNo": "string",
  "refundCode": "string",
  "displayCurrency": "string",
  "expectedConfirmationDate": "string",
  "expectedRefundDate": "string",
  "refundQuoteType": "AccurateQuote",
  "refundTickets": [
    {
      "lastName": "string",
      "firstName": "string",
      "ticketNo": "string"
    }
  ],
  "refundFareAmount": {
    "currency": "string",
    "originalFareAmount": 0,
    "estimatedRefundAmount": 0,
    "displayOriginalFareAmount": 0,
    "displayEstimatedRefundAmount": 0
  },
  "refundPostTicketingServiceAmounts": [
    {
      "postTicketingOrderNo": "string",
      "currency": "string",
      "originalPostTicketingServiceAmount": 0,
      "estimatedRefundAmount": 0,
      "displayPostTicketingServiceAmount": 0,
      "displayEstimatedRefundAmount": 0
    }
  ],
  "refundVouchers": [
    {
      "voucherId": "string",
      "voucherCode": "string",
      "eligiblePassengers": [
        {
          "name": "ZHANG/SAN"
        }
      ],
      "airline": "string",
      "estimatedRefundAmount": 0,
      "currency": "string",
      "voucherStartDate": "string",
      "voucherEndDate": "string",
      "travelStartDate": "string",
      "travelEndDate": "string",
      "note": "string"
    }
  ],
  "serviceFee": {
    "currency": "string",
    "transactionFee": 0,
    "displayTransactionFee": 0
  },
  "refundRules": [
    {
      "airline": "string",
      "ruleType": "0",
      "passengerType": "ADT",
      "penaltyAmount": "string",
      "penaltyPercent": 0,
      "penaltyPercentBase": "fare",
      "airlineFee": "string",
      "taxRefundable": true,
      "fareRefundable": true,
      "refundableAncillaries": [
        "StandardCheckInBaggage"
      ],
      "startMinute": 0,
      "endMinute": 0,
      "refundMethod": "CashBackToOriginalPayment"
    }
  ],
  "refundStatus": 0,
  "cancelReason": "string",
  "refundOfferId": "string",
  "refundMethod": "string"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|orderNo|string|true|none||Original order number|
|refundCode|string|true|none||Refund order number generated for this refund request|
|displayCurrency|string¦null|false|none||The alternative currency in which the fare and taxes amount needs to be displayed. The 3-letter currency code should be entered.|
|expectedConfirmationDate|string|true|none||Expected date of getting airline refund confirmation. The format is `yyyyMMdd`.|
|expectedRefundDate|string|true|none||Expected date of getting refund. The format is `yyyyMMdd`.|
|refundQuoteType|string|true|none||Type of refund quote:<br />AccurateQuote：quotation based on the calculated amount.<br />CannotQuote: quotation is unknown and will be according to the airline's rates|
|refundTickets|[[RefundTicket](#schemarefundticket)]|true|none||The refund calculation for each of the passengers whose refund quote has been requested|
|refundFareAmount|[RefundFareAmount](#schemarefundfareamount)|false|none||If `refundMethod` is CashBackToOriginalPayment, the `refundFareAmount` field is not null.|
|refundPostTicketingServiceAmounts|[[RefundPostTicketingServiceAmount](#schemarefundpostticketingserviceamount)]¦null|false|none||The refund calculation for Post-ticketing Servrice, including baggage etc. Each post-ticketing order will be present as an object.|
|refundVouchers|[[RefundVoucher](#schemarefundvoucher)]¦null|false|none||If `refundMethod` is Voucher,  the `refundVouchers` field is not null.|
|serviceFee|[ServiceFee](#schemaservicefee)|true|none||Service fee of refund.|
|refundRules|[[RefundRule](#schemarefundrule)]|true|none||The refund rules for the fare whose refund quote has been requested.|
|refundStatus|integer|true|none||The present status of the refund.<br />The options are:<br />0: Atlas Processing<br />1: Airline Processing (Submitted to airline by Atlas)<br />2: Refunded<br />3: Airline Refunding<br />4: Rejected<br />5: Fullfillment Done<br />6: Withdrew<br />If the ticket is paid by deposit: the status can be 0,1,2,3,4<br />If the ticket is paid by VCC pass through: the status can be 0,1,4,5,6<br />Withdrew is only in the refund claim|
|cancelReason|string¦null|false|none||The reason why the refund was cancelled.<br />The refund reasons are:<br />Does not match airline policy.<br />There is no schedule change from the airline side. \nPlease refer the ticket Fare Rules available in ATRIP flight deck for cancellation charges.<br />Voluntary Cancellation - Non-Refundable<br />As per airline policy, only voucher refund is available for the ticket<br />Refund request cancelled by the user<br />Travel has been completed by the passenger.<br />Refund not yet received from the airline. Please try again later.<br />The order is paid by your VCC. please refund by yourself<br />It's issued via your B2B account, please refund by yourself<br />Refund is availalbe through airline's B2C website. Please refund by yourself.<br />The refund claim voucher is invalid.<br />Duplicate Refund Record<br />Need to provide more materials that meet airline requirements<br />Actual refund amount less than service fee. Will reject it.|
|refundOfferId|string|true|none||Refund offer id for this quotation which can be used for the coming refund call.|
|refundMethod|string|true|none||Refund method: CashBackToOriginalPayment or Voucher|

#### 枚举值

|属性|值|
|---|---|
|refundQuoteType|AccurateQuote|
|refundQuoteType|CannotQuote|
|refundStatus|0|
|refundStatus|1|
|refundStatus|2|
|refundStatus|3|
|refundStatus|4|
|refundStatus|5|
|refundStatus|6|

