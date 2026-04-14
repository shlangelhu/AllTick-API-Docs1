---
description: 接口说明 该接口仅支持批量请求美股、港股、A股产品的部分基础信息。 请求频率
---

# GET 股票产品基础信息批量查询

[English](https://en.apis.alltick.co/rest-api/stock-http-interface-api/get-product-information-query) / 中文

## GET /static\_info

## 接口说明

该接口仅支持批量请求美股、港股、A股产品的部分基础信息。

## **请求频率**

<table data-full-width="false"><thead><tr><th width="91">计划</th><th width="221">单独请求</th><th width="472">同时请求多个http接口</th></tr></thead><tbody><tr><td>免费</td><td>每10秒，只能1次请求</td><td><p>1、10秒只能请求1个接口</p><p><mark style="color:red;">2、多个接口请求时，需注意/batch-kline接口需间隔10秒</mark><br>3、所有接口相加，1分钟最大请求10次(6秒1次)<br>4、每天总共最大可请求1000次，超过则第二天凌晨恢复使用</p></td></tr><tr><td>基础</td><td>每1秒，只能1次请求</td><td><p>1、同1秒只能请求1个接口</p><p><mark style="color:red;">2、多个接口请求时，需注意/batch-kline接口需间隔3秒</mark><br>3、所有接口相加，1分钟最大请求60次(1秒1次)<br>4、每天总共最大可请求86400次，超过则第二天凌晨恢复使用</p></td></tr><tr><td>高级</td><td>每1秒，最大可10次请求</td><td><p>1、所以接口相加，每1秒可请求10次</p><p><mark style="color:red;">2、多个接口请求时，需注意/batch-kline接口需间隔2秒</mark><br>3、所有接口相加，1分钟最大请求600次(1秒10次)<br>4、每天总共最大可请求864000次，超过则第二天凌晨恢复使用</p></td></tr><tr><td>专业</td><td>每1秒，最大可20次请求</td><td><p>1、所以接口相加，每1秒可请求20次</p><p><mark style="color:red;">2、多个接口请求时，需注意/batch-kline接口需间隔1秒</mark><br>3、所有接口相加，1分钟最大请求1200次(1秒20次)<br>4、每天总共最大可请求1728000次，超过则第二天凌晨恢复使用</p></td></tr><tr><td>全部港股</td><td>每1秒，最大可20次请求</td><td><p>1、所以接口相加，每1秒可请求20次</p><p><mark style="color:red;">2、多个接口请求时，需注意/batch-kline接口需间隔1秒</mark><br>3、所有接口相加，1分钟最大请求1200次(1秒20次)<br>4、每天总共最大可请求1728000次，超过则第二天凌晨恢复使用</p></td></tr><tr><td>全部A股</td><td>每1秒，最大可20次请求</td><td><p>1、所以接口相加，每1秒可请求20次</p><p><mark style="color:red;">2、多个接口请求时，需注意/batch-kline接口需间隔1秒</mark><br>3、所有接口相加，1分钟最大请求1200次(1秒20次)<br>4、每天总共最大可请求1728000次，超过则第二天凌晨恢复使用</p></td></tr><tr><td>全部美股</td><td>每1秒，最大可20次请求</td><td><p>1、所以接口相加，每1秒可请求20次</p><p><mark style="color:red;">2、多个接口请求时，需注意/batch-kline接口需间隔1秒</mark><br>3、所有接口相加，1分钟最大请求1200次(1秒20次)<br>4、每天总共最大可请求1728000次，超过则第二天凌晨恢复使用</p></td></tr></tbody></table>

## 接口限制 <a href="#jie-kou-xian-zhi" id="jie-kou-xian-zhi"></a>

1、请务必阅读：[HTTP接口限制说明](https://apis.alltick.co/integration-process/interface-restriction-description/http-interface-restrictions)

2、请务必阅读：[错误码说明](https://apis.alltick.co/integration-process/interface-restriction-description/error-code-description)

## **接口地址**

* **基本路径**: `/quote-stock-b-api/static_info`
* **完整URL**: `https://quote.alltick.co/quote-stock-b-api/static_info`

## **请求示例**

在发送查询请求时，必须包含方法名和token信息。一个请求的示例如下：

```arduino
https://quote.alltick.co/quote-stock-b-api/static_info?token=您的token&query=queryData
```

## 请求参数

| 名称    | 位置    | 类型     | 必选 | 说明            |
| ----- | ----- | ------ | -- | ------------- |
| token | query | string | 否  |               |
| query | query | string | 否  | 查看query请求参数说明 |

<mark style="color:red;">**将如下json进行UrlEncode编码，赋值到url的查询字符串的query里**</mark>

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

## query请求参数

<table><thead><tr><th width="154.02734375">名称</th><th width="139.6171875">类型</th><th width="139.73828125">必选</th><th>说明</th></tr></thead><tbody><tr><td>trace</td><td>string</td><td>是</td><td></td></tr><tr><td>data</td><td>object</td><td>是</td><td></td></tr><tr><td>» symbol_list</td><td>[object]</td><td>是</td><td></td></tr><tr><td>»» code</td><td>string</td><td>否</td><td>代码：<a href="https://docs.google.com/spreadsheets/d/1avkeR1heZSj6gXIkDeBt8X3nv4EzJetw4yFuKjSDYtA/edit?gid=495387863#gid=495387863">[点击code列表]</a><br><mark style="color:$danger;">注意：code值大小写与产品列表中的code保持一致</mark></td></tr></tbody></table>

## 返回示例

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

## 返回结果

| 状态码 | 状态码含义 | 说明 | 数据模型   |
| --- | ----- | -- | ------ |
| 200 | OK    | OK | Inline |

## 返回数据结构

| 名称                      | 类型        | 必选    | 说明         |
| ----------------------- | --------- | ----- | ---------- |
| » ret                   | integer   | true  | 返回code     |
| » msg                   | string    | true  | 返回code对应消息 |
| » trace                 | string    | true  | 请求的trace   |
| » data                  | object    | true  |            |
| »» static\_info\_list   | \[object] | true  |            |
| »»» board               | string    | false | 股票所属板块     |
| »»» bps                 | string    | false | 每股净资产      |
| »»» circulating\_shares | string    | false | 流通股本       |
| »»» currency            | string    | false | 交易币种       |
| »»» dividend\_yield     | string    | false | 股息         |
| »»» eps                 | string    | false | 每股盈利       |
| »»» eps\_ttm            | string    | false | 每股盈利 (TTM) |
| »»» exchange            | string    | false | 产品所属交易所    |
| »»» hk\_shares          | string    | false | 港股股本 (仅港股) |
| »»» lot\_size           | string    | false | 每手股数       |
| »»» name\_cn            | string    | false | 中文简体产品的名称  |
| »»» name\_en            | string    | false | 英文产品的名称    |
| »»» name\_hk            | string    | false | 中文繁体产品的名称  |
| »»» symbol              | string    | false | 产品code     |
| »»» total\_shares       | string    | false | 总股本        |

#### AllTick网站

{% hint style="info" %}
官方网站：[https://alltick.co/](https://alltick.co/)
{% endhint %}
