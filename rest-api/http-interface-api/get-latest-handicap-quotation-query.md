# GET Latest handicap quotation query

English / [中文](https://apis.alltick.co/rest-api/gu-piao-http-jie-kou-api/get-zui-xin-pan-kou-bao-jia-cha-xun)

## GET /depth-tick

> Please refer to the complete URL in [API Address Description](../../integration-process/market-address-description/http-quotes-api-address-description.md)

#### API Endpoints

1. **US Stocks, Hong Kong Stocks, A Shares, Major Index Data API Endpoints:**
   * **Base Path:** `/quote-stock-b-api/depth-tick`
   * **Full URL:** `https://quote.alltick.io/quote-stock-b-api/depth-tick`
2. **Forex, Precious Metals, Cryptocurrencies, Commodities API Endpoints:**
   * **Base Path:** `/quote-b-api/depth-tick`
   * **Full URL:** `https://quote.alltick.io/quote-b-api/depth-tick`

***

#### Request Examples

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
