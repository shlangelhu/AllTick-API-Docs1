---
description: >-
  This interface allows batch querying of multiple products and multiple K-line
  types (e.g., 1-minute, 15-minute, 30-minute), but only the latest two K-lines
  can be queried at once. For clients using th
---

# POST Query the latest 2 K lines of products in batches（High , Low, Open, Close）

English / [中文](https://app.gitbook.com/s/AnPIgTqJ2rek1QSPVUja/rest-api/stock-http-interface-api/post-pi-liang-cha-xun-chan-pin-zui-xin-2-genkxian)

## Post /batch-kline

## Interface Description

This interface allows batch querying of multiple products and multiple K-line types (e.g., 1-minute, 15-minute, 30-minute), but only the latest two K-lines can be queried at once.

For clients using the HTTP interface to obtain K-lines, it is advisable to combine the `/kline` and `/batch-kline` interfaces as follows:

* First, use the `/kline` interface to poll for historical data and store it in a local database. Subsequent historical data can be retrieved directly from the client's database without needing to make additional requests through the interface.
* Then, continuously use the `/batch-kline` interface to request the latest two K-lines for multiple products in bulk and update the database with this data.

This method allows for quick updates of the latest K-lines while avoiding limitations on request frequency caused by frequent requests for historical K-lines.

## Request Frequency

<table data-full-width="false"><thead><tr><th width="138">Plan</th><th width="248">Individual request</th><th width="332">Request multiple HTTP interfaces</th></tr></thead><tbody><tr><td>Free</td><td><p>1、1 request allowed every 10 seconds.</p><p>2、Each query can batch retrieve 10 items, where 10 equals the product count times the candlestick type.</p></td><td><p>1、1 request per 10 seconds.</p><p>2、/batch-kline needs 10-second intervals.</p><p>3、Total of 10 requests per minute (every 6 seconds).</p><p>4、Max 14400 daily requests; excess resets at midnight.</p></td></tr><tr><td>Basic</td><td><p>1、1 request every 3 seconds.</p><p>2、Each query can batch retrieve 100 items, where 100 equals the product count times the candlestick type.</p></td><td><p>1、One request per second.</p><p>2、/batch-kline: 1 request every 3 seconds.</p><p>3、Total of 60 requests per minute (1 request per second).</p><p>4、Max 86400 daily requests; excess resets at midnight.</p></td></tr><tr><td>Premium</td><td><p>1、1 request every 2 seconds.</p><p>2、Each query can batch retrieve 200 items, where 200 equals the product count times the candlestick type.</p></td><td><p>1、Combined interfaces: 10 requests/second.</p><p>2、/batch-kline: 1 request/2 seconds.</p><p>3、Total: 600 requests/minute (10/second).</p><p>4、Daily limit: 864,000 requests; reset daily at midnight if exceeded.</p></td></tr><tr><td>Professional</td><td><p>1、1 request per second.</p><p>2、Each query can batch retrieve 500 items, where 500 equals the product count times the candlestick type.</p></td><td><p>1、Combined interfaces: 20 requests/second.</p><p>2、/batch-kline: 1 request/second interval.</p><p>3、Total: 1200 requests/minute (20/second).</p><p>4、Daily limit: 1,728,000 requests; reset daily at midnight if exceeded.</p></td></tr><tr><td>All HK Stocks</td><td><p>1、1 request per second.</p><p>2、Each query can batch retrieve 500 items, where 500 equals the product count times the candlestick type.</p></td><td><p>1、Combined interfaces: 20 requests/second.</p><p>2、/batch-kline: 1 request/second interval.</p><p>3、Total: 1200 requests/minute (20/second).</p><p>4、Daily limit: 1,728,000 requests; reset daily at midnight if exceeded.</p></td></tr><tr><td>All CN Stocks</td><td><p>1、1 request per second.</p><p>2、Each query can batch retrieve 500 items, where 500 equals the product count times the candlestick type.</p></td><td><p>1、Combined interfaces: 20 requests/second.</p><p>2、/batch-kline: 1 request/second interval.</p><p>3、Total: 1200 requests/minute (20/second).</p><p>4、Daily limit: 1,728,000 requests; reset daily at midnight if exceeded.</p></td></tr></tbody></table>

## Interface Limitations

1. Please be sure to read:[ \[ HTTP Interface Limitations \].](../../integration-process/interface-restriction-description/http-interface-restrictions.md)
2. Please be sure to read: [\[ Error Code Descriptions \].](../../integration-process/interface-restriction-description/error-code-description.md)

## API Endpoints

1. **US Stocks, Hong Kong Stocks, A Shares, Major Index Data API Endpoints:**
   * **Base Path:** `/quote-stock-b-api/batch-kline`
   * **Full URL:** `https://quote.alltick.io/quote-stock-b-api/batch-kline`
2. **Forex, Precious Metals, Cryptocurrencies, Commodities API Endpoints:**
   * **Base Path:** `/quote-b-api/batch-kline`
   * **Full URL:** `https://quote.alltick.io/quote-b-api/batch-kline`

***

## Request Examples

1.  **Request Example for US Stocks, Hong Kong Stocks, A Shares, Major Index Data:**\
    The batch query function for retrieving the latest K-line data requires many parameters, which should be included in the request body. Only the `token` parameter should be included in the URL.\
    When sending the query request, you must include the method name and token information. An example request is as follows:

    ```plaintext
    https://quote.alltick.io/quote-stock-b-api/batch-kline?token=your_token
    ```
2.  **Request Example for Forex, Precious Metals, Cryptocurrencies, Commodities:**\
    The batch query function for retrieving the latest K-line data requires many parameters, which should be included in the request body. Only the `token` parameter should be included in the URL.\
    When sending the query request, you must include the method name and token information. An example request is as follows:

    ```plaintext
    https://quote.alltick.io/quote-b-api/batch-kline?token=your_token
    ```

***

## <mark style="color:red;">The batch query for the latest product K-lines includes many parameters, so they are placed in the request body. Only the</mark> <mark style="color:red;"></mark><mark style="color:red;">`token`</mark> <mark style="color:red;"></mark><mark style="color:red;">parameter is kept in the URL.</mark>

## Body request parameters

```
{
  "trace": "c2a8a146-a647-4d6f-ac07-8c4805bf0b74",
  "data": {
    "data_list": [
      {
        "code": "700.HK",
        "kline_type": 1,
        "kline_timestamp_end": 0,
        "query_kline_num": 1,
        "adjust_type": 0
      },
      {
        "code": "GOOGL.US",
        "kline_type": 1,
        "kline_timestamp_end": 0,
        "query_kline_num": 1,
        "adjust_type": 0
      }
    ]
  }
}
```

## Request parameters

<table data-full-width="false"><thead><tr><th width="182.836669921875">Name</th><th width="88.910888671875">Position</th><th width="82.2265625">Type</th><th width="90.3702392578125">Required</th><th>Description</th></tr></thead><tbody><tr><td>token</td><td>query</td><td>string</td><td>Yes</td><td></td></tr><tr><td>body</td><td>body</td><td>object</td><td>No</td><td></td></tr><tr><td>» trace</td><td>body</td><td>string</td><td>Yes</td><td>Trace code used for logging purposes, ensure uniqueness for each request</td></tr><tr><td>» data</td><td>body</td><td>object</td><td>Yes</td><td></td></tr><tr><td>»» data_list</td><td>body</td><td>[object]</td><td>Yes</td><td></td></tr><tr><td>»»» code</td><td>body</td><td>string</td><td>Yes</td><td>Refer to the code list and select the code you want to query：<a href="https://docs.google.com/spreadsheets/d/1avkeR1heZSj6gXIkDeBt8X3nv4EzJetw4yFuKjSDYtA/edit?gid=495387863#gid=495387863">[Click on the code list]</a></td></tr><tr><td>»»» kline_type</td><td>body</td><td>integer</td><td>Yes</td><td>Type of K-line: <br>1、1 represents 1-minute K-line, 2 represents 5-minute K-line, 3 represents 15-minute K-line, 4 represents 30-minute K-line, 5 represents 1-hour K-line, 6 represents 2-hour K-line (not supported for stocks), 7 represents 4-hour K-line (not supported for stocks), 8 represents daily K-line, 9 represents weekly K-line, and 10 represents monthly K-line. (Note: Stocks do not support 2-hour and 4-hour K-lines.)<br>2、The shortest K-line supported is 1 minute.<br>3、Query yesterday's closing price, with kline_type set to 8.</td></tr><tr><td>»»» kline_timestamp_end</td><td>body</td><td>integer</td><td>Yes</td><td><p>Query K-lines from a specified time:</p><p>1、Send 0 to query from the latest trading day.</p><p>2、Send a timestamp to query from that time.</p><p>3、Only forex, precious metals, and cryptocurrencies support timestamps; stock codes do not.</p></td></tr><tr><td>»»» query_kline_num</td><td>body</td><td>integer</td><td>Yes</td><td>1、Number of K-lines to query, maximum of 2<br>2、To query yesterday's closing price, set kline_type to 8 and query_kline_num to 2. From the 2 returned k-line data points, the one with the smaller timestamp represents yesterday's closing price.</td></tr><tr><td>»»» adjust_type</td><td>body</td><td>integer</td><td>Yes</td><td>Adjustment type, effective only for stock codes, e.g., 0: ex-rights, 1: pre-adjustment, currently only supports 0</td></tr></tbody></table>

## **Response example**

```
{
  "ret": 200,
  "msg": "ok",
  "trace": "c2a8a146-a647-4d6f-ac07-8c4805bf0b74",
  "data": {
    "kline_list": [
      {
        "code": "700.HK",
        "kline_type": 1,
        "kline_data": [
          {
            "timestamp": "1677829200",
            "open_price": "136.421",
            "close_price": "136.412",
            "high_price": "136.422",
            "low_price": "136.407",
            "volume": "0",
            "turnover": "0"
          }
        ]
      },
      {
        "code": "GOOGL.US",
        "kline_type": 1,
        "kline_data": [
          {
            "timestamp": "1677829200",
            "open_price": "136.421",
            "close_price": "136.412",
            "high_price": "136.422",
            "low_price": "136.407",
            "volume": "0",
            "turnover": "0"
          }
        ]
      }
    ]
  }
}
```

## Response Result

<table><thead><tr><th>Status Code</th><th>Status Meaning</th><th width="148.5999755859375">Description</th><th>Data Model</th></tr></thead><tbody><tr><td>200</td><td>OK</td><td>OK</td><td>Inline</td></tr></tbody></table>

<table><thead><tr><th width="165.199951171875">Name</th><th width="96">Type</th><th width="135.00006103515625">Required</th><th>Description</th></tr></thead><tbody><tr><td>» ret</td><td>integer</td><td>true</td><td>Return code</td></tr><tr><td>» msg</td><td>string</td><td>true</td><td>Message corresponding to the return code</td></tr><tr><td>» trace</td><td>string</td><td>true</td><td>Request trace</td></tr><tr><td>» data</td><td>object</td><td>true</td><td></td></tr><tr><td>»» kline_list</td><td>[object]</td><td>true</td><td></td></tr><tr><td>»»» code</td><td>string</td><td>false</td><td>Code</td></tr><tr><td>»»» kline_type</td><td>integer</td><td>integer</td><td><p>Kline Types:</p><ol><li>1= 1-minute,2 = 5-minute,3 = 15-minute,<br>4 = 30-minute,<br>5 = 1-hour,<br>6 = 2-hour (not supported for stocks),<br>7 = 4-hour (not supported for stocks),<br>8 = daily, 9 = weekly,<br>10 = monthly(Note: 2-hour and 4-hour Klines are not supported for stocks)</li><li>The shortest supported Kline is 1-minute.</li></ol></td></tr><tr><td>»»» kline_data</td><td>[array]</td><td>true</td><td></td></tr><tr><td>»»» timestamp</td><td>string</td><td>true</td><td>Timestamp of the Kline</td></tr><tr><td>»»» open_price</td><td>string</td><td>false</td><td>Open price of the Kline</td></tr><tr><td>»»» close_price</td><td>string</td><td>true</td><td><p><strong>Close price of the Kline</strong>:</p><ol><li>During trading hours, for the latest Kline, this is also the <strong>last traded price</strong></li><li>During market closure, for the latest Kline, this is the <strong>official closing price</strong></li></ol></td></tr><tr><td>»»» high_price</td><td>integer</td><td>true</td><td>High price of the Kline</td></tr><tr><td>»»» low_price</td><td>integer</td><td>true</td><td>Low price of the Kline</td></tr><tr><td>»»» volume</td><td>string</td><td>true</td><td>Trade volume of the Kline</td></tr><tr><td>»»» turnover</td><td>string</td><td>true</td><td>Trade amount (turnover) of the Kline</td></tr></tbody></table>

### Official Website

{% hint style="info" %}
Official website: [https://alltick.co/](https://alltick.co/)
{% endhint %}
