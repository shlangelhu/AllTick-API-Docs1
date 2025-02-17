# POST Batch Code Latest K-Line Query

English / [中文](https://apis.alltick.co/rest-api/gu-piao-http-jie-kou-api/get-pi-liangkxian-cha-xun)

## Post /batch-kline

> Please refer to the complete URL in [API Address Description](../../integration-process/market-address-description/http-quotes-api-address-description.md)

#### API Endpoints

1. **US Stocks, Hong Kong Stocks, A Shares, Major Index Data API Endpoints:**
   * **Base Path:** `/quote-stock-b-api/batch-kline`
   * **Full URL:** `https://quote.tradeswitcher.com/quote-stock-b-api/batch-kline`
2. **Forex, Precious Metals, Cryptocurrencies, Commodities API Endpoints:**
   * **Base Path:** `/quote-b-api/batch-kline`
   * **Full URL:** `https://quote.tradeswitcher.com/quote-b-api/batch-kline`

***

#### Request Examples

1.  **Request Example for US Stocks, Hong Kong Stocks, A Shares, Major Index Data:**\
    The batch query function for retrieving the latest K-line data requires many parameters, which should be included in the request body. Only the `token` parameter should be included in the URL.\
    When sending the query request, you must include the method name and token information. An example request is as follows:

    ```plaintext
    https://quote.tradeswitcher.com/quote-stock-b-api/batch-kline?token=your_token
    ```
2.  **Request Example for Forex, Precious Metals, Cryptocurrencies, Commodities:**\
    The batch query function for retrieving the latest K-line data requires many parameters, which should be included in the request body. Only the `token` parameter should be included in the URL.\
    When sending the query request, you must include the method name and token information. An example request is as follows:

    ```plaintext
    https://quote.tradeswitcher.com/quote-b-api/batch-kline?token=your_token
    ```

***

#### Additional Notes

* For both endpoints, the batch query parameters are expected to be provided in the request body, as the number of parameters can be extensive.
* Ensure that the token parameter is included in the URL for authentication purposes.

## Request Parameters

| Name  | Position | Type   | Required | Description                                       |
| ----- | -------- | ------ | -------- | ------------------------------------------------- |
| token | query    | string | No       |                                                   |
| query | query    | string | No       | See explanation of query request parameters below |

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

| Name                 | Type      | Required | Description                                             |
| -------------------- | --------- | -------- | ------------------------------------------------------- |
| » ret                | integer   | true     | Return code                                             |
| » msg                | string    | true     | Message corresponding to the return code                |
| » trace              | string    | true     | Request trace                                           |
| » data               | object    | true     |                                                         |
| »» tick\_list        | \[object] | true     |                                                         |
| »»» code             | string    | false    | Code                                                    |
| »»» seq              | string    | false    | Sequence                                                |
| »»» tick\_time       | string    | false    | Timestamp                                               |
| »»» price            | string    | false    | Price                                                   |
| »»» volume           | string    | false    | Volume                                                  |
| »»» turnover         | string    | false    | Turnover                                                |
| »»» trade\_direction | integer   | false    | Trading direction, 0 for default, 1 for BUY, 2 for SELL |

{% swagger src="../../.gitbook/assets/api (1).json" path="/quote-stock-b-api/batch-kline" method="post" %}
[api (1).json](<../../.gitbook/assets/api (1).json>)
{% endswagger %}

### Official Website

{% hint style="info" %}
Official website: [https://alltick.co/](https://alltick.co/)
{% endhint %}
