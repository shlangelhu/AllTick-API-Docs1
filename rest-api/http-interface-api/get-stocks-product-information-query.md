---
description: >-
  This interface only supports batch requests for basic information on US, HK,
  and A-share products. Request Frequency
---

# GET Stocks product information query

English / [中文](https://apis.alltick.co/rest-api/stock-http-interface-api/get-latest-transaction-price-query-1)

## Stocks product information query

## Interface Description

This interface only supports batch requests for basic information on US, HK, and A-share products.

## Request Frequency

<table data-full-width="false"><thead><tr><th width="138">Plan</th><th width="194">Individual request</th><th width="332">Request multiple HTTP interfaces</th></tr></thead><tbody><tr><td>Free</td><td>Once every 10 seconds, only 1 request can be made</td><td><p>1、1 request per 10 seconds.</p><p>2、/batch-kline needs 10-second intervals.</p><p>3、Total of 10 requests per minute (every 6 seconds).</p><p>4、Max 1000 daily requests; excess resets at midnight.</p></td></tr><tr><td>Basic</td><td>Only 1 request per second</td><td><p>1、One request per second.</p><p>2、/batch-kline: 1 request every 3 seconds.</p><p>3、Total of 60 requests per minute (1 request per second).</p><p>4、Max 86400 daily requests; excess resets at midnight.</p></td></tr><tr><td>Premium</td><td>Up to 10 requests per second</td><td><p>1、Combined interfaces: 10 requests/second.</p><p>2、/batch-kline: 1 request/2 seconds.</p><p>3、Total: 600 requests/minute (10/second).</p><p>4、Daily limit: 864,000 requests; reset daily at midnight if exceeded.</p></td></tr><tr><td>Professional</td><td>Up to 20 requests per second</td><td><p>1、Combined interfaces: 20 requests/second.</p><p>2、/batch-kline: 1 request/second interval.</p><p>3、Total: 1200 requests/minute (20/second).</p><p>4、Daily limit: 1,728,000 requests; reset daily at midnight if exceeded.</p></td></tr><tr><td>All HK Stocks</td><td>Up to 20 requests per second</td><td><p>1、Combined interfaces: 20 requests/second.</p><p>2、/batch-kline: 1 request/second interval.</p><p>3、Total: 1200 requests/minute (20/second).</p><p>4、Daily limit: 1,728,000 requests; reset daily at midnight if exceeded.</p></td></tr><tr><td>All CN Stocks</td><td>Up to 20 requests per second</td><td><p>1、Combined interfaces: 20 requests/second.</p><p>2、/batch-kline: 1 request/second interval.</p><p>3、Total: 1200 requests/minute (20/second).</p><p>4、Daily limit: 1,728,000 requests; reset daily at midnight if exceeded.</p></td></tr></tbody></table>

## Interface Limitations <a href="#interface-limitations" id="interface-limitations"></a>

1. Please be sure to read:[ \[ HTTP Interface Limitations \].](https://en.apis.alltick.co/integration-process/interface-restriction-description/http-interface-restrictions)
2. Please be sure to read: [\[ Error Code Descriptions \].](https://en.apis.alltick.co/integration-process/interface-restriction-description/error-code-description)

## **Interface Address**

* **Base Path:** `/quote-stock-b-api/static_info`
* **Full URL:** `https://quote.alltick.co/quote-stock-b-api/static_info`

## **Request Example**

When sending a query request, it must include the method name and token information. An example of a request is as follows:

```arduino
https://quote.alltick.co/quote-stock-b-api/static_info?token=您的token&query=queryData
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

| Name           | Type      | Required | Description                                                                                                                               |
| -------------- | --------- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| trace          | string    | Yes      |                                                                                                                                           |
| data           | object    | Yes      |                                                                                                                                           |
| » symbol\_list | \[object] | Yes      |                                                                                                                                           |
| » » code       | string    | No       | <p>Code<br><mark style="color:$danger;">Note: The case of the code value must be consistent with the code in the product list.</mark></p> |

## Response Example

```
{
  "ret": 200,
  "msg": "ok",
  "trace": "edd5df80-df7f-4acf-8f67-68fd2f096426",
  "data": {
    "static_info_list": [
      {
        "board": "HKEquity",
        "bps": "101.7577888985738336",
        "circulating_shares": "9267359712",
        "currency": "HKD",
        "dividend_yield": "3.4558141358352833",
        "eps": "13.7190213011686429",
        "eps_ttm": "18.0567016900844671",
        "exchange": "SEHK",
        "hk_shares": "9267359712",
        "lot_size": "100",
        "name_cn": "腾讯控股",
        "name_en": "TENCENT",
        "name_hk": "騰訊控股",
        "symbol": "700.HK",
        "total_shares": "9267359712"
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

| Name                    | Type      | Required | Description                                            |
| ----------------------- | --------- | -------- | ------------------------------------------------------ |
| » ret                   | integer   | true     | Return code                                            |
| » msg                   | string    | true     | Message corresponding to the return code               |
| » trace                 | string    | true     | Request trace                                          |
| » data                  | object    | true     |                                                        |
| »» static\_info\_list   | \[object] | true     |                                                        |
| »»» board               | string    | false    | The sector to which the stock belongs                  |
| »»» bps                 | string    | false    | Net assets per share                                   |
| »»» circulating\_shares | string    | false    | circulating capital                                    |
| »»» currency            | string    | false    | Transaction currency                                   |
| »»» dividend\_yield     | string    | false    | dividends                                              |
| »»» eps                 | string    | false    | earnings per share                                     |
| »»» eps\_ttm            | string    | false    | earnings per share (TTM)                               |
| »»» exchange            | string    | false    | The exchange to which the product belongs              |
| »»» hk\_shares          | string    | false    | Hong Kong stocks share capital (Hong Kong stocks only) |
| »»» lot\_size           | string    | false    | Number of shares per lot                               |
| »»» name\_cn            | string    | false    | Product name in simplified Chinese                     |
| »»» name\_en            | string    | false    | English product name                                   |
| »»» name\_hk            | string    | false    | Product name in traditional Chinese                    |
| »»» symbol              | string    | false    | Product code                                           |
| »»» total\_shares       | string    | false    | total share capital                                    |

### Official Website

{% hint style="info" %}
Official website: [https://alltick.co/](https://alltick.co/)
{% endhint %}
