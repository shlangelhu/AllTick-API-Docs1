# GET Latest transaction price query

English / [中文](https://apis.alltick.co/rest-api/gu-piao-http-jie-kou-api/get-zui-xin-cheng-jiao-jia-cha-xun)

## GET /trade-tick

> Please refer to the complete URL in [API Address Description](../../integration-process/market-address-description/http-quotes-api-address-description.md)

### Request Frequency

<table data-full-width="false"><thead><tr><th width="138">Plan</th><th width="194">Individual request</th><th width="332">Request multiple HTTP interfaces</th></tr></thead><tbody><tr><td>Free</td><td>1、Once every 10 seconds, only 1 request can be made<br>2、5 products per batch max</td><td><p>1、One request per second.</p><p>2、/batch-kline needs 10-second intervals.</p><p>3、Total of 10 requests per minute (every 6 seconds).</p><p>4、Max 14400 daily requests; excess resets at midnight.</p></td></tr><tr><td>Basic</td><td>1、Only 1 request per second<br>2、Suggest 50 code requests max due to GET URL length limit</td><td><p>1、One request per second.</p><p>2、/batch-kline: 1 request every 3 seconds.</p><p>3、Total of 60 requests per minute (1 request per second).</p><p>4、Max 86400 daily requests; excess resets at midnight.</p></td></tr><tr><td>Premium</td><td>1、Up to 10 requests per second<br>2、Suggest 50 code requests max due to GET URL length limit</td><td><p>1、Combined interfaces: 10 requests/second.</p><p>2、/batch-kline: 1 request/2 seconds.</p><p>3、Total: 600 requests/minute (10/second).</p><p>4、Daily limit: 864,000 requests; reset daily at midnight if exceeded.</p></td></tr><tr><td>Professional</td><td>1、Up to 20 requests per second<br>2、Suggest 50 code requests max due to GET URL length limit</td><td><p>1、Combined interfaces: 20 requests/second.</p><p>2、/batch-kline: 1 request/second interval.</p><p>3、Total: 1200 requests/minute (20/second).</p><p>4、Daily limit: 1,728,000 requests; reset daily at midnight if exceeded.</p></td></tr><tr><td>All HK Stocks</td><td>1、Up to 20 requests per second<br>2、Suggest 50 code requests max due to GET URL length limit</td><td><p>1、Combined interfaces: 20 requests/second.</p><p>2、/batch-kline: 1 request/second interval.</p><p>3、Total: 1200 requests/minute (20/second).</p><p>4、Daily limit: 1,728,000 requests; reset daily at midnight if exceeded.</p></td></tr><tr><td>All CN Stocks</td><td>1、Up to 20 requests per second<br>2、Suggest 50 code requests max due to GET URL length limit</td><td><p>1、Combined interfaces: 20 requests/second.</p><p>2、/batch-kline: 1 request/second interval.</p><p>3、Total: 1200 requests/minute (20/second).</p><p>4、Daily limit: 1,728,000 requests; reset daily at midnight if exceeded.</p></td></tr></tbody></table>

## API Endpoints

#### API Endpoints

1. **US Stocks, Hong Kong Stocks, A Shares, Major Index Data API Endpoints:**
   * **Base Path:** `/quote-stock-b-api/trade-tick`
   * **Full URL:** `https://quote.tradeswitcher.com/quote-stock-b-api/trade-tick`
2. **Forex, Precious Metals, Cryptocurrencies, Commodities API Endpoints:**
   * **Base Path:** `/quote-b-api/trade-tick`
   * **Full URL:** `https://quote.tradeswitcher.com/quote-b-api/trade-tick`

***

## Request Examples

1.  **Request Example for US Stocks, Hong Kong Stocks, A Shares, Major Index Data:**\
    When sending a query request, you must include the method name and token information. An example request is as follows:

    ```plaintext
    https://quote.tradeswitcher.com/quote-stock-b-api/trade-tick?token=your_token&query=queryData
    ```
2.  **Request Example for Forex, Precious Metals, Cryptocurrencies, Commodities:**\
    When sending a query request, you must include the method name and token information. An example request is as follows:

    ```plaintext
    https://quote.tradeswitcher.com/quote-b-api/trade-tick?token=your_token&query=queryData
    ```

## Request Parameters

<table><thead><tr><th width="141">Name</th><th>Position</th><th>Type</th><th>Required</th><th>Description</th></tr></thead><tbody><tr><td>token</td><td>query</td><td>string</td><td>No</td><td></td></tr><tr><td>query</td><td>query</td><td>string</td><td>No</td><td>See explanation of query request parameters below</td></tr></tbody></table>

> Query Request Parameters

The following JSON should be URL-encoded and assigned to the `query` query string in the URL.

```
{
  "trace": "edd5df80-df7f-4acf-8f67-68fd2f096426",
  "data": {
    "symbol_list": [
      {
        "code": "857.HK"
      },
      {
        "code": "UNH.US"
      }
    ]
  }
}
```

## Query Request Parameters

| Name           | Type      | Required | Description |
| -------------- | --------- | -------- | ----------- |
| trace          | string    | Yes      |             |
| data           | object    | Yes      |             |
| » symbol\_list | \[object] | Yes      |             |
| »» code        | string    | No       | Code        |

> Response Example

> OK

```
{
  "ret": 200,
  "msg": "ok",
  "trace": "edd5df80-df7f-4acf-8f67-68fd2f096426",
  "data": {
    "tick_list": [
      {
        "code": "857.HK",
        "seq": "30841439",
        "tick_time": "1677831545217",
        "price": "136.302",
        "volume": "0",
        "turnover": "0",
        "trade_direction": 0
      }
    ]
  }
}
```

## Response Result



| Status Code | Status Meaning | Description | Data Model |
| ----------- | -------------- | ----------- | ---------- |
| 200         | OK             | OK          | Inline     |

## Response Data Structure

Status Code **200**

<table><thead><tr><th>Name</th><th>Type</th><th>Required</th><th>Constraint</th><th width="40">Chinese Name</th><th>Description</th></tr></thead><tbody><tr><td>» ret</td><td>integer</td><td>true</td><td></td><td></td><td>Return code</td></tr><tr><td>» msg</td><td>string</td><td>true</td><td></td><td></td><td>Message corresponding to the return code</td></tr><tr><td>» trace</td><td>string</td><td>true</td><td></td><td></td><td>Request trace</td></tr><tr><td>» data</td><td>object</td><td>true</td><td></td><td></td><td></td></tr><tr><td>»» tick_list</td><td>[object]</td><td>true</td><td></td><td></td><td></td></tr><tr><td>»»» code</td><td>string</td><td>false</td><td></td><td></td><td>Code</td></tr><tr><td>»»» seq</td><td>string</td><td>false</td><td></td><td></td><td>Sequence</td></tr><tr><td>»»» tick_time</td><td>string</td><td>false</td><td></td><td></td><td>Timestamp</td></tr><tr><td>»»» price</td><td>string</td><td>false</td><td></td><td></td><td>Price</td></tr><tr><td>»»» volume</td><td>string</td><td>false</td><td></td><td></td><td>Volume</td></tr><tr><td>»»» turnover</td><td>string</td><td>false</td><td></td><td></td><td>Turnover</td></tr><tr><td>»»» trade_direction</td><td>integer</td><td>false</td><td></td><td></td><td>Trading direction, 0 for default, 1 for BUY, 2 for SELL</td></tr></tbody></table>

{% swagger src="../../.gitbook/assets/MultiMarkets-BusinessAPI.openapi (1).json" path="/quote-b-api/trade-tick" method="get" expanded="true" %}
[MultiMarkets-BusinessAPI.openapi (1).json](<../../.gitbook/assets/MultiMarkets-BusinessAPI.openapi (1).json>)
{% endswagger %}

### Official Website

{% hint style="info" %}
Official website: [https://alltick.co/](https://alltick.co/)
{% endhint %}
