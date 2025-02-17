# GET Order Book（Depth） Query

English / [中文](https://apis.alltick.co/rest-api/gu-piao-http-jie-kou-api/get-zui-xin-pan-kou-bao-jia-cha-xun)

## GET /depth-tick

> Please refer to the complete URL in [API Address Description](../../integration-process/market-address-description/http-quotes-api-address-description.md)

## Interface Description

The following is the maximum market depth for each product type:

1. It is normal for inactive products to be smaller than the maximum range listed below.
2. There is a situation where the unilateral depth is empty. For example, when the stock price limit rises or falls, the unilateral market opening may be empty.

<table data-full-width="true"><thead><tr><th width="133"></th><th width="148">FX、Metals</th><th width="114">Cryptocurrency</th><th width="111">HK Stocks</th><th>CN Stocks</th></tr></thead><tbody><tr><td>Order Book Description</td><td>Maximum 5 gears</td><td>Maximum 5 gears</td><td>Maximum 10 gears</td><td>Maximum 5 gears</td></tr></tbody></table>

### Request Frequency

<table data-full-width="false"><thead><tr><th width="138">Plan</th><th width="194">Individual request</th><th width="332">Request multiple HTTP interfaces</th></tr></thead><tbody><tr><td>Free</td><td>Once every 10 seconds, only 1 request can be made</td><td><p>1、One request per second.</p><p>2、/batch-kline needs 10-second intervals.</p><p>3、Total of 10 requests per minute (every 6 seconds).</p><p>4、Max 14400 daily requests; excess resets at midnight.</p></td></tr><tr><td>Basic</td><td>Only 1 request per second</td><td><p>1、One request per second.</p><p>2、/batch-kline: 1 request every 3 seconds.</p><p>3、Total of 60 requests per minute (1 request per second).</p><p>4、Max 86400 daily requests; excess resets at midnight.</p></td></tr><tr><td>Premium</td><td>Up to 10 requests per second</td><td><p>1、Combined interfaces: 10 requests/second.</p><p>2、/batch-kline: 1 request/2 seconds.</p><p>3、Total: 600 requests/minute (10/second).</p><p>4、Daily limit: 864,000 requests; reset daily at midnight if exceeded.</p></td></tr><tr><td>Professional</td><td>Up to 20 requests per second</td><td><p>1、Combined interfaces: 20 requests/second.</p><p>2、/batch-kline: 1 request/second interval.</p><p>3、Total: 1200 requests/minute (20/second).</p><p>4、Daily limit: 1,728,000 requests; reset daily at midnight if exceeded.</p></td></tr><tr><td>All HK Stocks</td><td>Up to 20 requests per second</td><td><p>1、Combined interfaces: 20 requests/second.</p><p>2、/batch-kline: 1 request/second interval.</p><p>3、Total: 1200 requests/minute (20/second).</p><p>4、Daily limit: 1,728,000 requests; reset daily at midnight if exceeded.</p></td></tr><tr><td>All CN Stocks</td><td>Up to 20 requests per second</td><td><p>1、Combined interfaces: 20 requests/second.</p><p>2、/batch-kline: 1 request/second interval.</p><p>3、Total: 1200 requests/minute (20/second).</p><p>4、Daily limit: 1,728,000 requests; reset daily at midnight if exceeded.</p></td></tr></tbody></table>

## API Endpoints

1. **US Stocks, Hong Kong Stocks, A Shares, Major Index Data API Endpoints:**
   * **Base Path:** `/quote-stock-b-api/depth-tick`
   * **Full URL:** `https://quote.alltick.io/quote-stock-b-api/depth-tick`
2. **Forex, Precious Metals, Cryptocurrencies, Commodities API Endpoints:**
   * **Base Path:** `/quote-b-api/depth-tick`
   * **Full URL:** `https://quote.alltick.io/quote-b-api/depth-tick`

***

## Request Examples

1.  **Request Example for US Stocks, Hong Kong Stocks, A Shares, Major Index Data:**\
    When sending a query request, you must include the method name and token information. An example request is as follows:

    ```plaintext
    https://quote.alltick.io/quote-stock-b-api/depth-tick?token=your_token&query=queryData
    ```
2.  **Request Example for Forex, Precious Metals, Cryptocurrencies, Commodities:**\
    When sending a query request, you must include the method name and token information. An example request is as follows:

    ```plaintext
    https://quote.alltick.io/quote-b-api/depth-tick?token=your_token&query=queryData
    ```

## Request Parameters

| Name  | Position | Type   | Required | Description                                  |
| ----- | -------- | ------ | -------- | -------------------------------------------- |
| token | query    | string | No       |                                              |
| query | query    | string | No       | See explanation for query request parameters |

> Query Request Parameters

Encode the following JSON into URL format and assign it to the `query` query string in the URL.

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
| » » code       | string    | No       | Code        |

> Response Example

```
{
  "ret": 200,
  "msg": "ok",
  "trace": "edd5df80-df7f-4acf-8f67-68fd2f096426",
  "data": {
    "tick_list": [
      {
        "code": "857.HK",
        "seq": "30686349",
        "tick_time": "1677830357227",
        "bids": [
          {
            "price": "136.424",
            "volume": "100000.00"
          }
        ],
        "asks": [
          {
            "price": "136.427",
            "volume": "400000.00"
          }
        ]
      }
    ]
  }
}
```

## Response Result

| Status Code | Status Meaning | Description | Data Model |
| ----------- | -------------- | ----------- | ---------- |
| 200         | OK             | OK          | Inline     |

| Name            | Type      | Required | Description                              |
| --------------- | --------- | -------- | ---------------------------------------- |
| » ret           | integer   | true     | Return code                              |
| » msg           | string    | true     | Message corresponding to the return code |
| » trace         | string    | true     | Request trace                            |
| » data          | object    | true     |                                          |
| »» tick\_list   | \[object] | true     |                                          |
| »» » code       | string    | false    | Code                                     |
| »» » seq        | string    | false    | Quote sequence number                    |
| »» » tick\_time | string    | false    | Quote timestamp                          |
| »» » bids       | \[object] | false    | Bid list                                 |
| »» »» price     | string    | false    | Price                                    |
| »» »» volume    | string    | false    | Volume                                   |
| »» » asks       | \[object] | false    | Ask list                                 |
| »» »» price     | string    | false    | Price                                    |
| »» »» volume    | string    | false    | Volume                                   |



{% swagger src="../../.gitbook/assets/MultiMarkets-BusinessAPI.openapi (1).json" path="/quote-b-api/depth-tick" method="get" expanded="true" %}
[MultiMarkets-BusinessAPI.openapi (1).json](<../../.gitbook/assets/MultiMarkets-BusinessAPI.openapi (1).json>)
{% endswagger %}

### Official Website

{% hint style="info" %}
Official website: [https://alltick.co/](https://alltick.co/)
{% endhint %}
