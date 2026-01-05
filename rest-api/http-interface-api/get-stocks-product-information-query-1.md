---
description: >-
  This interface only supports batch requests for basic information on US, HK,
  and A-share products. Request Frequency
---

# GET Resumption Information Query API

English / [中文](https://apis.alltick.co/rest-api/stock-http-interface-api/get-latest-transaction-price-query-1)

## Resumption Information Query API&#x20;

## Interface Description

This API provides queries for suspension and resumption information from major global exchanges (SSE, NYSE, NASDAQ). All APIs return data in JSON format, sorted in descending order by announcement time.

## Request Frequency

<table data-full-width="false"><thead><tr><th width="138">Plan</th><th width="194">Individual request</th><th width="332">Request multiple HTTP interfaces</th></tr></thead><tbody><tr><td>Free</td><td>Once every 10 seconds, only 1 request can be made</td><td><p>1、1 request per 10 seconds.</p><p>2、/batch-kline needs 10-second intervals.</p><p>3、Total of 10 requests per minute (every 6 seconds).</p><p>4、Max 14400 daily requests; excess resets at midnight.</p></td></tr><tr><td>Basic</td><td>Only 1 request per second</td><td><p>1、One request per second.</p><p>2、/batch-kline: 1 request every 3 seconds.</p><p>3、Total of 60 requests per minute (1 request per second).</p><p>4、Max 86400 daily requests; excess resets at midnight.</p></td></tr><tr><td>Premium</td><td>Up to 10 requests per second</td><td><p>1、Combined interfaces: 10 requests/second.</p><p>2、/batch-kline: 1 request/2 seconds.</p><p>3、Total: 600 requests/minute (10/second).</p><p>4、Daily limit: 864,000 requests; reset daily at midnight if exceeded.</p></td></tr><tr><td>Professional</td><td>Up to 20 requests per second</td><td><p>1、Combined interfaces: 20 requests/second.</p><p>2、/batch-kline: 1 request/second interval.</p><p>3、Total: 1200 requests/minute (20/second).</p><p>4、Daily limit: 1,728,000 requests; reset daily at midnight if exceeded.</p></td></tr><tr><td>All HK Stocks</td><td>Up to 20 requests per second</td><td><p>1、Combined interfaces: 20 requests/second.</p><p>2、/batch-kline: 1 request/second interval.</p><p>3、Total: 1200 requests/minute (20/second).</p><p>4、Daily limit: 1,728,000 requests; reset daily at midnight if exceeded.</p></td></tr><tr><td>All CN Stocks</td><td>Up to 20 requests per second</td><td><p>1、Combined interfaces: 20 requests/second.</p><p>2、/batch-kline: 1 request/second interval.</p><p>3、Total: 1200 requests/minute (20/second).</p><p>4、Daily limit: 1,728,000 requests; reset daily at midnight if exceeded.</p></td></tr></tbody></table>

## Interface Limitations <a href="#interface-limitations" id="interface-limitations"></a>

1. Please be sure to read:[ \[ HTTP Interface Limitations \].](https://en.apis.alltick.co/integration-process/interface-restriction-description/http-interface-restrictions)
2. Please be sure to read: [\[ Error Code Descriptions \].](https://en.apis.alltick.co/integration-process/interface-restriction-description/error-code-description)

## **Interface Address**

1. **Query Suspension/Resumption Information of the Shanghai Stock Exchange (SSE):**

* Base Path: `/api/suspension/sse`
* Full URL: `https://quote.alltick.co/api/suspension/sse`

2. **Query Suspension/Resumption Information of the New York Stock Exchange (NYSE):**

* Base Path: `/api/suspension/nyse`
* Full URL: `https://quote.alltick.co/api/suspension/nyse`

3. **Query Suspension/Resumption Information of the Nasdaq Stock Exchange:**

* Base Path: `/api/suspension/nasdaq`
* Full URL: `https://quote.alltick.co/api/suspension/nasdaq`

## **Request Example**

### 1. Retrieve the Shanghai Stock Exchange data API

#### API Information

* **URL**: `/api/suspension/sse`
* **Method**: GET
* **Description**: Retrieve all suspension and resumption information from the Shanghai Stock Exchange (SSE).

#### Request Parameters

<table><thead><tr><th>Field</th><th width="151.4000244140625">Type</th><th width="155">Required</th><th>Description</th></tr></thead><tbody><tr><td>token</td><td>string</td><td>Yes</td><td>User subscription token</td></tr></tbody></table>

#### Response Example

```json
{
  "success": true,
  "timestamp": "2024-01-15T10:30:00",
  "totalCount": 125,
  "data": [
    {
      "symbol": "600000",
      "symbolName": "浦发银行",
      "haltReason": "重大事项停牌",
      "haltDate": "2024-01-15",
      "haltTime": "09:30:00",
      "haltPeriod": "全天停牌",
      "resumeDate": "2024-01-16",
      "resumeTime": "09:30:00",
      "publishDate": "2024-01-14 18:00:00"
    }
  ]
}

```

#### Response Field Description

#### Common Fields

<table><thead><tr><th width="160.4000244140625">Field</th><th width="107.4000244140625">Type</th><th width="163.800048828125">Required</th><th>Description</th></tr></thead><tbody><tr><td>success</td><td>boolean</td><td>Yes</td><td>Whether the request was successful</td></tr><tr><td>timestamp</td><td>string</td><td>Yes</td><td>Response timestamp (format: yyyy-MM-dd'T'HH:mm:ss)</td></tr><tr><td>totalCount</td><td>integer</td><td>Yes</td><td>Total number of records</td></tr><tr><td>data</td><td>array</td><td>Yes</td><td>List of suspension/resumption records</td></tr></tbody></table>

#### data（Object Fields）

Fields in each object:

<table><thead><tr><th>Field</th><th width="157.39990234375">Type</th><th width="160">Nullable</th><th>Description</th></tr></thead><tbody><tr><td>symbol</td><td>string</td><td>No</td><td>Stock symbol</td></tr><tr><td>symbolName</td><td>string</td><td>Yes</td><td>Stock name</td></tr><tr><td>haltReason</td><td>string</td><td>Yes</td><td>Reason for suspension</td></tr><tr><td>haltDate</td><td>string</td><td>Yes</td><td>Suspension date</td></tr><tr><td>haltTime</td><td>string</td><td>Yes</td><td>Suspension time</td></tr><tr><td>haltPeriod</td><td>string</td><td>Yes</td><td>Suspension duration</td></tr><tr><td>resumeDate</td><td>string</td><td>Yes</td><td>Resumption date</td></tr><tr><td>resumeTime</td><td>string</td><td>Yes</td><td>Resumption time</td></tr><tr><td>publishDate</td><td>string</td><td>No</td><td>Announcement time</td></tr></tbody></table>

#### Example Request

```bash
curl -X GET "<https://quote.alltick.co/api/suspension/sse?token=您的Token>" -H "Accept: application/json"
```

***

### 2. Obtain the NYSE data API

#### API Information

* **URL**: `/api/suspension/nyse`
* Method: GET
* Description: Retrieve all suspension and resumption information from the New York Stock Exchange (NYSE).

#### Request Parameters

<table><thead><tr><th>Field</th><th width="161.199951171875">Type</th><th width="139.7999267578125">Required</th><th>Description</th></tr></thead><tbody><tr><td>token</td><td>string</td><td>Yes</td><td>User subscription token</td></tr></tbody></table>

#### Response Example

```json
{
  "success": true,
  "timestamp": "2024-01-15T10:30:00",
  "totalCount": 89,
  "data": [
    {
      "symbol": "AAPL",
      "haltReason": "新闻待公布",
      "haltDate": "2024-01-15",
      "haltTime": "10:15:00",
      "haltDateTime": "2024-01-15 10:15:00",
      "resumeDate": "2024-01-15",
      "resumeTime": "11:00:00",
      "resumeDateTime": "2024-01-15 11:00:00",
      "sourceExchange": "NYSE"
      "publishDate": "2024-01-15 10:10:00
    }
  ]
}

```

#### Response Field Description

#### Common Fields

<table><thead><tr><th width="166.199951171875">Field</th><th width="150.2000732421875">Type</th><th width="126.2000732421875">Required</th><th>Description</th></tr></thead><tbody><tr><td>success</td><td>boolean</td><td>Yes</td><td>Whether the request was successful</td></tr><tr><td>timestamp</td><td>string</td><td>Yes</td><td>Response timestamp (format: yyyy-MM-dd'T'HH:mm:ss)</td></tr><tr><td>totalCount</td><td>integer</td><td>Yes</td><td>Total number of records</td></tr><tr><td>data</td><td>array</td><td>Yes</td><td>List of suspension/resumption records</td></tr></tbody></table>

#### data（Object Fields）

Fields in each object:

<table><thead><tr><th>Field</th><th width="154.4000244140625">Type</th><th width="146.199951171875">Nullable</th><th>Description</th></tr></thead><tbody><tr><td>symbol</td><td>string</td><td>No</td><td>Stock symbol</td></tr><tr><td>haltReason</td><td>string</td><td>Yes</td><td>Reason for suspension</td></tr><tr><td>haltTime</td><td>string</td><td>Yes</td><td>Suspension time</td></tr><tr><td>haltDateTime</td><td>string</td><td>Yes</td><td>Suspension date and time</td></tr><tr><td>resumeDate</td><td>string</td><td>Yes</td><td>Resumption date</td></tr><tr><td>resumeTime</td><td>string</td><td>Yes</td><td>Resumption time</td></tr><tr><td>resumeDateTime</td><td>string</td><td>Yes</td><td>Resumption date and time</td></tr><tr><td>sourceExchange</td><td>string</td><td>Yes</td><td>Exchange code</td></tr><tr><td>publishDate</td><td>string</td><td>No</td><td>Announcement time</td></tr></tbody></table>

#### Example Request

```bash
curl -X GET "<https://quote.alltick.co/api/suspension/nyse?token=您的Token>" -H "Accept: application/json"
```

***

### 3. NASDAQ Suspension/Resumption Data API

#### API Information

* **URL**: `/api/suspension/nasdaq`
* **Method**: GET
* **Description**: Retrieve all suspension and resumption information from the NASDAQ Stock Exchange.

#### Request Parameters

<table><thead><tr><th width="173.800048828125">Field</th><th width="126.60009765625">Type</th><th width="131">Required</th><th>Description</th></tr></thead><tbody><tr><td>token</td><td>string</td><td>Yes</td><td>User subscription token</td></tr></tbody></table>

#### Response Example

```json
{
  "success": true,
  "timestamp": "2024-01-15T10:30:00",
  "totalCount": 156,
  "data": [
    {
      "symbol": "GOOGL",
      "haltDate": "2024-01-15",
      "haltTime": "13:45:00",
      "haltDateTime": "2024-01-15 13:45:00",
      "sourceExchange": "NASDAQ",
      "haltReason": "波动性暂停",
      "pauseThresholdPrice": "145.50",
      "resumeDate": "2024-01-15",
      "resumeTime": "14:00:00",
      "resumeDateTime": "2024-01-15 14:00:00",
      "publishDate": "2024-01-15 13:44:30"
    }
  ]
}

```

#### Response Field Description

#### Common Fields

<table><thead><tr><th width="141.800048828125">Field</th><th width="119">Type</th><th width="144.60009765625">Required</th><th>Description</th></tr></thead><tbody><tr><td>success</td><td>boolean</td><td>Yes</td><td>Whether the request was successfu</td></tr><tr><td>timestamp</td><td>string</td><td>Yes</td><td>Response timestamp (format: yyyy-MM-dd'T'HH:mm:ss)</td></tr><tr><td>totalCount</td><td>integer</td><td>Yes</td><td>Total number of records</td></tr><tr><td>data</td><td>array</td><td>Yes</td><td>List of suspension/resumption records</td></tr></tbody></table>

#### data（Object Fields）

Fields in each object:

<table><thead><tr><th width="185.4000244140625">Field</th><th width="126.2000732421875">Type</th><th width="142">Nullable</th><th>Description</th></tr></thead><tbody><tr><td>symbol</td><td>string</td><td>No</td><td>Stock symbol</td></tr><tr><td>haltDate</td><td>string</td><td>Yes</td><td>Suspension date</td></tr><tr><td>haltTime</td><td>string</td><td>Yes</td><td>Suspension time</td></tr><tr><td>haltDateTime</td><td>string</td><td>Yes</td><td>Suspension date and time</td></tr><tr><td>sourceExchange</td><td>string</td><td>Yes</td><td>Exchange code</td></tr><tr><td>haltReason</td><td>string</td><td>Yes</td><td>Reason for suspension</td></tr><tr><td>pauseThresholdPrice</td><td>string</td><td>Yes</td><td>Pause threshold price</td></tr><tr><td>resumeDate</td><td>string</td><td>Yes</td><td>Resumption date</td></tr><tr><td>resumeTime</td><td>string</td><td>Yes</td><td>Quote resumption time</td></tr><tr><td>resumeDateTime</td><td>string</td><td>Yes</td><td>Trading resumption time</td></tr><tr><td>publishDate</td><td>string</td><td>No</td><td>Announcement time</td></tr></tbody></table>

#### Example Request

```bash
curl -X GET "<https://quote.alltick.co/api/suspension/nasdaq?token=您的Token>" -H "Accept: application/json"
```

***

### Error Response

All APIs return the following format when an error occurs:

```json
{
  "success": false,
  "error": "Error description"
}

```

**HTTP Status Code:** 500

#### Error Response Fields

| Field   | Type    | Required | Description       |
| ------- | ------- | -------- | ----------------- |
| success | boolean | Yes      | Always `false`    |
| error   | string  | Yes      | Error description |

***

### Notes

* Pagination is **not supported**; all APIs return the full dataset for the **most recent one year**.
* Data is sorted by **announcement time in descending order** (latest first).
* Time format details:
  * `timestamp`: ISO format (`yyyy-MM-dd'T'HH:mm:ss`)
  * Other time fields: `yyyy-MM-dd HH:mm:ss`
* It is recommended to set an appropriate timeout, as large data volumes may require longer response times.
* Field nullability:
  * **"No"**: The field always has a value and will never be null.
  * **"Yes"**: The field may be null or an empty string; callers should handle null checks accordingly.

### Official Website

{% hint style="info" %}
Official website: [https://alltick.co/](https://alltick.co/)
{% endhint %}
