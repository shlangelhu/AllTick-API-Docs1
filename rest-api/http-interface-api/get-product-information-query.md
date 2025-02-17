# GET Product information query

English / [中文](https://apis.alltick.co/rest-api/stock-http-interface-api/get-latest-transaction-price-query-1)

### Product information query

**Interface Address**

* **Base Path:** `/quote-stock-b-api/static_info`
* **Full URL:** `https://quote.alltick.io/quote-stock-b-api/static_info`

**Request Example**

When sending a query request, it must include the method name and token information. An example of a request is as follows:

```arduino
https://quote.alltick.io/quote-stock-b-api/static_info?token=您的token&query=queryData
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
