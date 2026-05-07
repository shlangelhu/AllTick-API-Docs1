# GET Latest transaction price query（Latest Price）

English / [中文](https://apis.alltick.co/rest-api/gu-piao-http-jie-kou-api/get-zui-xin-cheng-jiao-jia-cha-xun)

## GET /trade-tick

## Interface Description

This interface supports batch requests for the latest trade prices (latest tick data、Latest Price) but does not support requests for historical trade prices (historical tick data).

## Request Frequency

<table data-full-width="false"><thead><tr><th width="138">Plan</th><th width="194">Individual request</th><th width="332">Request multiple HTTP interfaces</th></tr></thead><tbody><tr><td>Free</td><td>1、Once every 10 seconds, only 1 request can be made<br>2、5 products per batch max</td><td><p>1、1 request per 10 seconds.</p><p>2、/batch-kline needs 10-second intervals.</p><p>3、Total of 10 requests per minute (every 6 seconds).</p><p>4、Max 1000 daily requests; excess resets at midnight.</p></td></tr><tr><td>Basic</td><td>1、Only 1 request per second<br>2、Suggest 50 code requests max due to GET URL length limit</td><td><p>1、One request per second.</p><p>2、/batch-kline: 1 request every 3 seconds.</p><p>3、Total of 60 requests per minute (1 request per second).</p><p>4、Max 86400 daily requests; excess resets at midnight.</p></td></tr><tr><td>Premium</td><td>1、Up to 10 requests per second<br>2、Suggest 50 code requests max due to GET URL length limit</td><td><p>1、Combined interfaces: 10 requests/second.</p><p>2、/batch-kline: 1 request/2 seconds.</p><p>3、Total: 600 requests/minute (10/second).</p><p>4、Daily limit: 864,000 requests; reset daily at midnight if exceeded.</p></td></tr><tr><td>Professional</td><td>1、Up to 20 requests per second<br>2、Suggest 50 code requests max due to GET URL length limit</td><td><p>1、Combined interfaces: 20 requests/second.</p><p>2、/batch-kline: 1 request/second interval.</p><p>3、Total: 1200 requests/minute (20/second).</p><p>4、Daily limit: 1,728,000 requests; reset daily at midnight if exceeded.</p></td></tr><tr><td>All HK Stocks</td><td>1、Up to 20 requests per second<br>2、Suggest 50 code requests max due to GET URL length limit</td><td><p>1、Combined interfaces: 20 requests/second.</p><p>2、/batch-kline: 1 request/second interval.</p><p>3、Total: 1200 requests/minute (20/second).</p><p>4、Daily limit: 1,728,000 requests; reset daily at midnight if exceeded.</p></td></tr><tr><td>All CN Stocks</td><td>1、Up to 20 requests per second<br>2、Suggest 50 code requests max due to GET URL length limit</td><td><p>1、Combined interfaces: 20 requests/second.</p><p>2、/batch-kline: 1 request/second interval.</p><p>3、Total: 1200 requests/minute (20/second).</p><p>4、Daily limit: 1,728,000 requests; reset daily at midnight if exceeded.</p></td></tr></tbody></table>

## Interface Limitations <a href="#interface-limitations" id="interface-limitations"></a>

1. Please be sure to read:[ \[ HTTP Interface Limitations \].](https://en.apis.alltick.co/integration-process/interface-restriction-description/http-interface-restrictions)
2. Please be sure to read: [\[ Error Code Descriptions \].](https://en.apis.alltick.co/integration-process/interface-restriction-description/error-code-description)

## API Endpoints

#### API Endpoints

1. **US Stocks, Hong Kong Stocks, A Shares, Major Index Data API Endpoints:**
   * **Base Path:** `/quote-stock-b-api/trade-tick`
   * **Full URL:** `https://quote.alltick.co/quote-stock-b-api/trade-tick`
2. **Forex, Precious Metals, Cryptocurrencies, Commodities API Endpoints:**
   * **Base Path:** `/quote-b-api/trade-tick`
   * **Full URL:** `https://quote.alltick.co/quote-b-api/trade-tick`

## Request Examples

1.  **Request Example for US Stocks, Hong Kong Stocks, A Shares, Major Index Data:**\
    When sending a query request, you must include the method name and token information. An example request is as follows:

    ```plaintext
    https://quote.alltick.co/quote-stock-b-api/trade-tick?token=your_token&query=queryData
    ```
2.  **Request Example for Forex, Precious Metals, Cryptocurrencies, Commodities:**\
    When sending a query request, you must include the method name and token information. An example request is as follows:

    ```plaintext
    https://quote.alltick.co/quote-b-api/trade-tick?token=your_token&query=queryData
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

| Name           | Type      | Required | Description                                                                                                                               |
| -------------- | --------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| trace          | string    | Yes      |                                                                                                                                           |
| data           | object    | Yes      |                                                                                                                                           |
| » symbol\_list | \[object] | Yes      |                                                                                                                                           |
| »» code        | string    | No       | <p>Code<br><mark style="color:$danger;">Note: The case of the code value must be consistent with the code in the product list.</mark></p> |

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

<table><thead><tr><th width="164.828125">Name</th><th width="94.3515625">Type</th><th width="99.4140625">Required</th><th>Description</th></tr></thead><tbody><tr><td>» ret</td><td>integer</td><td>true</td><td>Return code</td></tr><tr><td>» msg</td><td>string</td><td>true</td><td>Message corresponding to the return code</td></tr><tr><td>» trace</td><td>string</td><td>true</td><td>Request trace</td></tr><tr><td>» data</td><td>object</td><td>true</td><td></td></tr><tr><td>»» tick_list</td><td>[object]</td><td>true</td><td></td></tr><tr><td>»»» code</td><td>string</td><td>false</td><td>Code</td></tr><tr><td>»»» seq</td><td>string</td><td>false</td><td>Sequence</td></tr><tr><td>»»» tick_time</td><td>string</td><td>false</td><td>Timestamp</td></tr><tr><td>»»» price</td><td>string</td><td>false</td><td>Price</td></tr><tr><td>»»» volume</td><td>string</td><td>false</td><td>Volume</td></tr><tr><td>»»» turnover</td><td>string</td><td>false</td><td><strong>Turnover (Trade Amount)</strong></td></tr><tr><td>»»» trade_direction</td><td>integer</td><td>false</td><td><p>Trade Direction:</p><ol><li>0 is the default value, 1 is Buy, and 2 is Sell.</li><li>For forex, precious metals, and energy, the default return is only 1.</li><li>For stocks and cryptocurrencies, it can return 0, 1, or 2 based on market conditions.</li><li><p>Detailed Explanation:</p><ul><li>0: Neutral, indicating a trade executed at a price between the best bid and best ask.</li><li>1: Aggressive Buy, indicating a trade executed at the ask price or higher.</li><li>2: Aggressive Sell, indicating a trade executed at the bid price or lower.</li></ul></li></ol></td></tr></tbody></table>

### Official Website

{% hint style="info" %}
Official website: [https://alltick.co/](https://alltick.co/)
{% endhint %}
