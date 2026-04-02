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

# Notifications and Webhook

## POST Register Webhook

POST /updateWebhookURL.do

**Endpoint:**
https://sandbox.atriptech.com/updateWebhookURL.do

> Body 请求参数

```json
{
  "cid": "XXXXXXXX",
  "url": "https://xxx.com/xxxx"
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
|» url|body|string| 是 |The URL for receiving webhook notifications|

> 返回示例

> 200 Response

```json
{
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
|» msg|[ResponseMessage](#schemaresponsemessage)¦null|false|none||It serves as an additional description of the response result. Especially when the interface reports an error (`status` !=`0`), it is usually a human-readable error message. Note: Do not use this field in any programming scenarios. For example, do not judge whether the interface responds successfully based on this field. Instead, you should only determine it by checking whether the status is equal to`0`at any time.|

## POST Incident List

POST /event/getPageList.do

**Endpoint:**
https://sandbox.atriptech.com/event/getPageList.do

> Body 请求参数

```json
{
  "eventId": "",
  "orderNo": "",
  "eventType": "",
  "eventStatus": [
    0,
    1
  ],
  "airline": "",
  "eventTimeStart": "2023-04-01 00:00:00",
  "eventTimeEnd": "2023-05-01 00:00:00",
  "depTimeStart": null,
  "depTimeEnd": null,
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
|» eventId|body|string| 否 |Incident ID|
|» orderNo|body|string| 否 |Order number|
|» eventType|body|string| 否 |Incident type:|
|» pnr|body|string| 否 |Order's pnr.|
|» paxName|body|string| 否 |Order's passenger names.|
|» paxEmail|body|string| 否 |Order's passenger Email. Email address passed to the Airline.|
|» airline|body|string| 否 |Airline IATA code.|
|» eventStatus|body|[integer]| 否 |A list containing incident stauses|
|» eventTimeStart|body|string| 否 |Incident Receiving Time Start|
|» eventTimeEnd|body|string| 否 |Incident Receiving Time End|
|» depTimeStart|body|string| 否 |Departure Time Start(Departure local time)|
|» depTimeEnd|body|string| 否 |Departure Time End(Departure local time)|
|» updateTimeStart|body|string| 否 |none|
|» pageIndex|body|integer¦null| 否 |Pagination|
|» pageSize|body|integer| 是 |Number of records per page|

#### 详细说明

**» eventType**: Incident type:
- `email.schedulechange`: Schedule Change-Email Notification
- `abnormal.cancelled`: Unacounted Cancellation
- `order.schedulechange`: Schedule Change-API Notification

**» eventStatus**: A list containing incident stauses
- `0`: Unconfirmed
- `1`: Confirmed

**» eventTimeStart**: Incident Receiving Time Start
Format: yyyy-MM-dd HH:mm:ss UTC+08:00

**» eventTimeEnd**: Incident Receiving Time End
Format: yyyy-MM-dd HH:mm:ss UTC+08:00

**» depTimeStart**: Departure Time Start(Departure local time)
Format: yyyy-MM-dd HH:mm:ss

**» depTimeEnd**: Departure Time End(Departure local time)
Format: yyyy-MM-dd HH:mm:ss

> 返回示例

> 200 Response

```json
{
  "records": [
    {
      "eventId": "20230401003644225YJQGR",
      "orderNo": "HCNMN20230227142411968",
      "subOrderNo": "HCNMN20230227142411968_1",
      "eventType": "email.schedulechange",
      "eventStatus": 0,
      "eventTime": "Apr 1, 2023 12:36:44 AM",
      "extraInfo": "4775822",
      "confirmedResult": null,
      "confirmedRemark": null,
      "clientCode": "TAC00001",
      "createTime": "Apr 1, 2023 12:36:44 AM",
      "updateIme": "Apr 1, 2023 12:36:44 AM",
      "airline": "F9",
      "depTime": "Mar 31, 2023 11:12:00 AM",
      "confirmTime": null,
      "confirmUsr": null,
      "notified": 1,
      "pnr": "G7ZNW5",
      "paxName": "SOWERS/REBECCA MUSETTA,STEPHENS/DAVID JEROME",
      "paxEmail": "GeraldineDushkin2005@ttjipiao.top"
    },
    "…"
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
|» msg|string¦null|false|none||none|
|» records|[object]|true|none||none|
|»» eventId|string|true|none||Incident Id.|
|»» orderNo|string|true|none||Order Number.|
|»» eventType|string|true|none||Incident type<br />-`email.schedulechange`: Schedule Change-Email Notification<br />-`abnormal.cancelled`: Unacounted Cancellation<br />-`order.schedulechange`: Schedule Change-API Notification|
|»» eventStatus|integer|true|none||Incident staus<br />-`0`: Unconfirmed<br />-`1`: Confirmed|
|»» eventTime|string|true|none||Incident recieving time.<br />Format: yyyy-MM-dd HH:mm:ss UTC+08:00|
|»» confirmedResult|string¦null|false|none||Incident Reason. Schedule Change Type & Cancelled Type.|
|»» confirmedRemark|string¦null|false|none||Remark.|
|»» createTime|string|true|none||Incident create time.<br />Format: yyyy-MM-dd HH:mm:ss UTC+08:00|
|»» airline|string|true|none||Airline IATA code.|
|»» depTime|string|true|none||Flight depature time. Depature local time.|
|»» confirmTime|string¦null|false|none||Confirmed Time.<br />Format: yyyy-MM-dd HH:mm:ss UTC+08:00|
|»» notified|integer¦null|false|none||Send the notification or not. 1: YES. 0: No|
|»» pnr|string|true|none||Order's pnr.|
|»» paxName|string|true|none||Order's passenger names.|
|»» paxEmail|string|true|none||Order's passenger Email. Email address passed to the Airline.|
|» pageIndex|string|true|none||Current pagination|
|» pageSize|string|true|none||Page size|
|» total|string|true|none||Total number of records|

# 数据模型

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

