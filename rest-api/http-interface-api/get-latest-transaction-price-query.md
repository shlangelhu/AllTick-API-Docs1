# GET Latest transaction price query

English / [中文](https://apis.alltick.co/rest-api/gu-piao-http-jie-kou-api/get-zui-xin-cheng-jiao-jia-cha-xun)

## GET /trade-tick

> Please refer to the complete URL in [API Address Description](../../integration-process/market-address-description/http-quotes-api-address-description.md)

#### API Endpoints

1. **US Stocks, Hong Kong Stocks, A Shares, Major Index Data API Endpoints:**
   * **Base Path:** `/quote-stock-b-api/trade-tick`
   * **Full URL:** `https://quote.alltick.io/quote-stock-b-api/trade-tick`
2. **Forex, Precious Metals, Cryptocurrencies, Commodities API Endpoints:**
   * **Base Path:** `/quote-b-api/trade-tick`
   * **Full URL:** `https://quote.alltick.io/quote-b-api/trade-tick`

***

#### Request Examples

1.  **Request Example for US Stocks, Hong Kong Stocks, A Shares, Major Index Data:**\
    When sending a query request, you must include the method name and token information. An example request is as follows:

    ```plaintext
    https://quote.alltick.io/quote-stock-b-api/trade-tick?token=your_token&query=queryData
    ```
2.  **Request Example for Forex, Precious Metals, Cryptocurrencies, Commodities:**\
    When sending a query request, you must include the method name and token information. An example request is as follows:

    ```plaintext
    https://quote.alltick.io/quote-b-api/trade-tick?token=your_token&query=queryData
    ```

#### Batch Code Latest K-Line Query functionality. Due to the large number of batch query parameters, they are placed in the body, with only the token field parameter remaining in the URL parameters.

> Body Request Parameters

```
{
  "trace": "py_http_test1",
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

## Request Parameters

| Name                      | Position | Type      | Required | Description                                                                                                                                                                                                                                |
| ------------------------- | -------- | --------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| token                     | query    | string    | Yes      | If you don't know your token, please contact the relevant personnel to request                                                                                                                                                             |
| body                      | body     | object    | No       |                                                                                                                                                                                                                                            |
| » trace                   | body     | string    | Yes      | Trace code, used for querying logs, please ensure it's unique for each request                                                                                                                                                             |
| » data                    | body     | object    | Yes      |                                                                                                                                                                                                                                            |
| »» data\_list             | body     | \[object] | Yes      |                                                                                                                                                                                                                                            |
| »»» code                  | body     | string    | Yes      | Please refer to the code list and select the code you want to query                                                                                                                                                                        |
| »»» kline\_type           | body     | integer   | Yes      | K-line type, 1 for 1-minute K, 2 for 5-minute K, 3 for 15-minute K, 4 for 30-minute K, 5 for hourly K, 6 for 2-hour K, 7 for 4-hour K, 8 for daily K, 9 for weekly K, 10 for monthly K (Note: Stocks do not support 2-hour K and 4-hour K) |
| »»» kline\_timestamp\_end | body     | integer   | Yes      | From which timestamp to query backward, 0 means from the current time, only effective for non-stock type codes                                                                                                                             |
| »»» query\_kline\_num     | body     | integer   | Yes      | Number of K-lines to query, up to 1 or 2                                                                                                                                                                                                   |
| »»» adjust\_type          | body     | integer   | Yes      | Adjustment type, only effective for stock type codes, e.g., 0: ex-right, 1: pre-adjustment, currently only supports 0                                                                                                                      |

> Response Example

```
{
  "ret": 200,
  "msg": "ok",
  "trace": "asdfsdfa",
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

## Response

| Status Code | Status Meaning | Explanation | Data Model |
| ----------- | -------------- | ----------- | ---------- |
| 200         | OK             | OK          | Inline     |

| Name              | Type     | Required | Description                                                                                                                                                                                                                                               |
| ----------------- | -------- | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| » ret             | integer  | true     |                                                                                                                                                                                                                                                           |
| » msg             | string   | true     |                                                                                                                                                                                                                                                           |
| » trace           | string   | true     |                                                                                                                                                                                                                                                           |
| » data            | object   | true     |                                                                                                                                                                                                                                                           |
| »» kline\_list    | \[array] | true     |                                                                                                                                                                                                                                                           |
| »»» code          | string   | true     | Product Code                                                                                                                                                                                                                                              |
| »»» kline\_type   | integer  | true     | K-line type, where 1 represents 1-minute K, 2 for 5-minute K, 3 for 15-minute K, 4 for 30-minute K, 5 for hour K, 6 for 2-hour K, 7 for 4-hour K, 8 for daily K, 9 for weekly K, and 10 for monthly K (Note: Stocks do not support 2-hour K and 4-hour K) |
| »»» kline\_data   | \[array] | true     |                                                                                                                                                                                                                                                           |
| »»»» timestamp    | string   | true     | Timestamp of the K-line                                                                                                                                                                                                                                   |
| »»»» open\_price  | string   | true     | Opening price of the K-line                                                                                                                                                                                                                               |
| »»»» close\_price | string   | true     | Closing price of the K-line                                                                                                                                                                                                                               |
| »»»» high\_price  | string   | true     | Highest price of the K-line                                                                                                                                                                                                                               |
| »»»» low\_price   | string   | true     | Lowest price of the K-line                                                                                                                                                                                                                                |
| »»»» volume       | string   | true     | Volume of the K-line                                                                                                                                                                                                                                      |
| »»»» turnover     | string   | true     | Turnover of the K-line                                                                                                                                                                                                                                    |

{% swagger src="../../.gitbook/assets/MultiMarkets-BusinessAPI.openapi (1).json" path="/quote-b-api/trade-tick" method="get" expanded="true" %}
[MultiMarkets-BusinessAPI.openapi (1).json](<../../.gitbook/assets/MultiMarkets-BusinessAPI.openapi (1).json>)
{% endswagger %}

### Official Website

{% hint style="info" %}
Official website: [https://alltick.co/](https://alltick.co/)
{% endhint %}
