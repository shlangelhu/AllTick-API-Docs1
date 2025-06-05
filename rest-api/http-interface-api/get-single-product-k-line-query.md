---
description: >-
  This interface can be used to query historical K-line data, but it only allows
  querying one product at a time. It is recommended to cache the retrieved
  historical K-lines in a local database. For clie
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# GET Single Product K line query（High Low, Open, Close）

English / [中文](https://apis.alltick.co/rest-api/gu-piao-http-jie-kou-api/getkxian-cha-xun)

## GET /kline

## Interface Description

This interface can be used to query historical K-line data, but it only allows querying one product at a time. It is recommended to cache the retrieved historical K-lines in a local database.

For clients using the HTTP interface to obtain K-lines, it is advisable to combine the `/kline` and `/batch-kline` interfaces as follows:

* First, use the `/kline` interface to poll for historical data and store it in a local database. Subsequent historical data can be retrieved directly from the client's database without needing to make additional requests through the interface.
* Then, continuously use the `/batch-kline` interface to request the latest two K-lines for multiple products in bulk and update the database with this data.

This method allows for quick updates of the latest K-lines while avoiding limitations on request frequency caused by frequent requests for historical K-lines.

## Request Frequency

<table data-full-width="false"><thead><tr><th width="138">Plan</th><th width="248">Individual request</th><th width="332">Request multiple HTTP interfaces</th></tr></thead><tbody><tr><td>Free</td><td>Once every 10 seconds, only 1 request can be made</td><td><p>1、One request per second.</p><p>2、/batch-kline needs 10-second intervals.</p><p>3、Total of 10 requests per minute (every 6 seconds).</p><p>4、Max 14400 daily requests; excess resets at midnight.</p></td></tr><tr><td>Basic</td><td>Only 1 request per second</td><td><p>1、One request per second.</p><p>2、/batch-kline: 1 request every 3 seconds.</p><p>3、Total of 60 requests per minute (1 request per second).</p><p>4、Max 86400 daily requests; excess resets at midnight.</p></td></tr><tr><td>Premium</td><td>Up to 10 requests per second</td><td><p>1、Combined interfaces: 10 requests/second.</p><p>2、/batch-kline: 1 request/2 seconds.</p><p>3、Total: 600 requests/minute (10/second).</p><p>4、Daily limit: 864,000 requests; reset daily at midnight if exceeded.</p></td></tr><tr><td>Professional</td><td>Up to 20 requests per second</td><td><p>1、Combined interfaces: 20 requests/second.</p><p>2、/batch-kline: 1 request/second interval.</p><p>3、Total: 1200 requests/minute (20/second).</p><p>4、Daily limit: 1,728,000 requests; reset daily at midnight if exceeded.</p></td></tr><tr><td>All HK Stocks</td><td>Up to 20 requests per second</td><td><p>1、Combined interfaces: 20 requests/second.</p><p>2、/batch-kline: 1 request/second interval.</p><p>3、Total: 1200 requests/minute (20/second).</p><p>4、Daily limit: 1,728,000 requests; reset daily at midnight if exceeded.</p></td></tr><tr><td>All CN Stocks</td><td>Up to 20 requests per second</td><td><p>1、Combined interfaces: 20 requests/second.</p><p>2、/batch-kline: 1 request/second interval.</p><p>3、Total: 1200 requests/minute (20/second).</p><p>4、Daily limit: 1,728,000 requests; reset daily at midnight if exceeded.</p></td></tr></tbody></table>

## Interface Limitations

1. Please be sure to read:[ \[ HTTP Interface Limitations \].](../../integration-process/interface-restriction-description/http-interface-restrictions.md)
2. Please be sure to read: [\[ Error Code Descriptions \].](../../integration-process/interface-restriction-description/error-code-description.md)

## API Endpoints

1. **US Stocks, Hong Kong Stocks, A Shares, Major Index Data API Endpoints:**

* **Base Path:** `/quote-stock-b-api/kline`
* **Full URL:** `https://quote.alltick.io/quote-stock-b-api/kline`

2. **Forex, Precious Metals, Cryptocurrencies, Commodities API Endpoints:**

* **Base Path:** `/quote-b-api/kline`
* **Full URL:** `https://quote.alltick.io/quote-b-api/kline`

## Request Examples

1. **Request Example for US Stocks, Hong Kong Stocks, A Shares, Major Index Data:**

When sending a query request, you must include the method name and token information. An example request is as follows:\
`https://quote.alltick.io/quote-stock-b-api/kline?token=your_token&query=queryData`

2. **Request Example for Forex, Precious Metals, Cryptocurrencies, Commodities:**

When sending a query request, you must include the method name and token information. An example request is as follows:\
`https://quote.alltick.io/quote-b-api/kline?token=your_token&query=queryData`

## Request Parameters

<table><thead><tr><th>Name</th><th width="149">Position</th><th>Type</th><th>Required</th><th>Description</th></tr></thead><tbody><tr><td>token</td><td>query</td><td>string</td><td>No</td><td></td></tr><tr><td>query</td><td>query</td><td>string</td><td>No</td><td>See explanation for query request parameter below</td></tr></tbody></table>

> Explanation for query request parameter

Encode the following JSON using URL encoding and assign it to the 'query' query string in the URL:

```
{
  "trace": "3baaa938-f92c-4a74-a228-fd49d5e2f8bc-1678419657806",
  "data": {
    "code": "857.HK",
    "kline_type": 1,
    "kline_timestamp_end": 0,
    "query_kline_num": 2,
    "adjust_type": 0
  }
}
```

## Query Request Parameters

<table><thead><tr><th width="185.38671875">Name</th><th width="92.25">Type</th><th width="85.22265625">Required</th><th>Description</th></tr></thead><tbody><tr><td>trace</td><td>string</td><td>Yes</td><td>Trace code used for logging purposes, ensure uniqueness for each request</td></tr><tr><td>data</td><td>object</td><td>Yes</td><td></td></tr><tr><td>» code</td><td>string</td><td>Yes</td><td>Refer to the code list and select the code you want to query：<a href="https://docs.google.com/spreadsheets/d/1avkeR1heZSj6gXIkDeBt8X3nv4EzJetw4yFuKjSDYtA/edit?gid=495387863#gid=495387863">[Click on the code list]</a></td></tr><tr><td>» kline_type</td><td>integer</td><td>Yes</td><td>Type of K-line: <br>1、1 represents 1-minute K-line, 2 represents 5-minute K-line, 3 represents 15-minute K-line, 4 represents 30-minute K-line, 5 represents 1-hour K-line, 6 represents 2-hour K-line (not supported for stocks), 7 represents 4-hour K-line (not supported for stocks), 8 represents daily K-line, 9 represents weekly K-line, and 10 represents monthly K-line. (Note: Stocks do not support 2-hour and 4-hour K-lines.)<br>2、The shortest K-line supported is 1 minute.<br>3、Query yesterday's closing price, with kline_type set to 8.</td></tr><tr><td>» kline_timestamp_end</td><td>integer</td><td>Yes</td><td><p>Query K-lines from a specified time:</p><p>1、Send 0 to query from the latest trading day.</p><p>2、Send a timestamp to query from that time.</p><p>3、Only forex, precious metals, and cryptocurrencies support timestamps; stock codes do not.</p></td></tr><tr><td>» query_kline_num</td><td>integer</td><td>Yes</td><td>1、Number of K-lines to query, maximum of 1000<br>2、To query yesterday's closing price, set kline_type to 8 and query_kline_num to 2. From the 2 returned k-line data points, the one with the smaller timestamp represents yesterday's closing price.</td></tr><tr><td>» adjust_type</td><td>integer</td><td>Yes</td><td>Adjustment type, effective only for stock codes, e.g., 0: ex-rights, 1: pre-adjustment, currently only supports 0</td></tr></tbody></table>

> Response Example OK

```
{
  "ret": 200,
  "msg": "ok",
  "trace": "3baaa938-f92c-4a74-a228-fd49d5e2f8bc-1678419657806",
  "data": {
    "code": "857.HK",
    "kline_type": 1,
    "kline_list": [
      {
        "timestamp": "1677829200",
        "open_price": "136.421",
        "close_price": "136.412",
        "high_price": "136.422",
        "low_price": "136.407",
        "volume": "0",
        "turnover": "0"
      },
      {
        "timestamp": "1677829260",
        "open_price": "136.412",
        "close_price": "136.401",
        "high_price": "136.415",
        "low_price": "136.397",
        "volume": "0",
        "turnover": "0"
      }
    ]
  }
}
```

## Response Results

<table><thead><tr><th width="161.30078125">Status Code</th><th width="196.50390625">Status Code Meaning</th><th>Description</th><th>Data Model</th></tr></thead><tbody><tr><td>200</td><td>OK</td><td>OK</td><td>Inline</td></tr></tbody></table>

<table><thead><tr><th width="157.20703125">Name</th><th width="109.15625">Type</th><th width="98.421875">Required</th><th>Description</th></tr></thead><tbody><tr><td>» ret</td><td>integer</td><td>true</td><td></td></tr><tr><td>» msg</td><td>string</td><td>true</td><td></td></tr><tr><td>» trace</td><td>string</td><td>true</td><td></td></tr><tr><td>» data</td><td>object</td><td>true</td><td></td></tr><tr><td>»» code</td><td>string</td><td>true</td><td>Code</td></tr><tr><td>»» kline_type</td><td>integer</td><td>true</td><td>Type of K-line: <br>1、1 represents 1-minute K-line, 2 represents 5-minute K-line, 3 represents 15-minute K-line, 4 represents 30-minute K-line, 5 represents 1-hour K-line, 6 represents 2-hour K-line (not supported for stocks), 7 represents 4-hour K-line (not supported for stocks), 8 represents daily K-line, 9 represents weekly K-line, and 10 represents monthly K-line. (Note: Stocks do not support 2-hour and 4-hour K-lines.)<br>2、The shortest K-line supported is 1 minute.</td></tr><tr><td>»» kline_list</td><td>[object]</td><td>true</td><td></td></tr><tr><td>»»» timestamp</td><td>string</td><td>true</td><td>Timestamp of the K-line</td></tr><tr><td>»»» open_price</td><td>string</td><td>true</td><td>Opening price of the K-line</td></tr><tr><td>»»» close_price</td><td>string</td><td>true</td><td>Closing price of the K-line</td></tr><tr><td>»»» high_price</td><td>string</td><td>true</td><td>Highest price of the K-line</td></tr><tr><td>»»» low_price</td><td>string</td><td>true</td><td>Lowest price of the K-line</td></tr><tr><td>»»» volume</td><td>string</td><td>true</td><td>Trading volume of the K-line</td></tr><tr><td>»»» turnover</td><td>string</td><td>true</td><td>Trading turnover of the K-line</td></tr></tbody></table>

### Official Website

{% hint style="info" %}
Official website: [https://alltick.co/](https://alltick.co/)
{% endhint %}
