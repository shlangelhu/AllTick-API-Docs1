# GET 最新盘口报价查询

[English ](https://en.apis.alltick.co/rest-api/stock-http-interface-api/get-latest-handicap-quotation-query)/ 中文

## GET /depth-tick

> 完整的URL请参见[API地址说明](../../integration-process/market-address-description/http-quotes-api-address-description.md)

## **接口说明**

以下是每类产品最大的盘口深度：

1、不活跃的产品存在小于下面列的最大档的情况，属于正常情况

2、存在单边深度是空的情况，例如股票涨停跌停时，单边盘口可能是空的

<table><thead><tr><th width="87"></th><th width="229">外汇、贵金属、原油</th><th width="97">加密货币</th><th width="100">港股</th><th width="92">美股</th><th>沪深A股</th></tr></thead><tbody><tr><td>深度说明</td><td>最大5档</td><td>最大5档</td><td>最大10档</td><td>最大1档</td><td>最大5档</td></tr></tbody></table>

## **请求频率**

<table data-full-width="true"><thead><tr><th width="81">计划</th><th width="208">单独请求</th><th width="472">同时请求多个http接口</th></tr></thead><tbody><tr><td>免费</td><td>每10秒，只能1次请求</td><td><p>1、同1秒只能请求1个接口</p><p><mark style="color:red;">2、多个接口请求时，需注意/batch-kline接口需间隔10秒</mark><br>3、所有接口相加，1分钟最大请求10次(6秒1次) <br>4、每天总共最大可请求14400次，超过则第二天凌晨恢复使用</p></td></tr><tr><td>基础</td><td>每1秒，只能1次请求</td><td><p>1、同1秒只能请求1个接口</p><p><mark style="color:red;">2、多个接口请求时，需注意/batch-kline接口需间隔3秒</mark><br>3、所有接口相加，1分钟最大请求60次(1秒1次)<br>4、每天总共最大可请求86400次，超过则第二天凌晨恢复使用</p></td></tr><tr><td>高级</td><td>每1秒，最大可10次请求</td><td><p>1、所以接口相加，每1秒可请求10次</p><p><mark style="color:red;">2、多个接口请求时，需注意/batch-kline接口需间隔2秒</mark><br>3、所有接口相加，1分钟最大请求600次(1秒10次)<br>4、每天总共最大可请求864000次，超过则第二天凌晨恢复使用</p></td></tr><tr><td>专业</td><td>每1秒，最大可20次请求</td><td><p>1、所以接口相加，每1秒可请求20次</p><p><mark style="color:red;">2、多个接口请求时，需注意/batch-kline接口需间隔1秒</mark><br>3、所有接口相加，1分钟最大请求1200次(1秒20次)<br>4、每天总共最大可请求1728000次，超过则第二天凌晨恢复使用</p></td></tr><tr><td>全部港股</td><td>每1秒，最大可20次请求</td><td><p>1、所以接口相加，每1秒可请求20次</p><p><mark style="color:red;">2、多个接口请求时，需注意/batch-kline接口需间隔1秒</mark><br>3、所有接口相加，1分钟最大请求1200次(1秒20次)<br>4、每天总共最大可请求1728000次，超过则第二天凌晨恢复使用</p></td></tr><tr><td>全部A股</td><td>每1秒，最大可20次请求</td><td><p>1、所以接口相加，每1秒可请求20次</p><p><mark style="color:red;">2、多个接口请求时，需注意/batch-kline接口需间隔1秒</mark><br>3、所有接口相加，1分钟最大请求1200次(1秒20次)<br>4、每天总共最大可请求1728000次，超过则第二天凌晨恢复使用</p></td></tr><tr><td>全部美股</td><td>每1秒，最大可20次请求</td><td><p>1、所以接口相加，每1秒可请求20次</p><p><mark style="color:red;">2、多个接口请求时，需注意/batch-kline接口需间隔1秒</mark><br>3、所有接口相加，1分钟最大请求1200次(1秒20次)<br>4、每天总共最大可请求1728000次，超过则第二天凌晨恢复使用</p></td></tr></tbody></table>

## 接口地址

**1、美股、港股、A股、大盘数据接口地址：**

* 基本路径: /quote-stock-b-api/depth-tick
* 完整URL: [https://quote.tradeswitcher.com/quote-stock-b-api/depth-tick](https://quote.tradeswitcher.com/quote-stock-b-api/depth-tick)

**2、外汇、贵金属、加密货币、商品接口地址：**

* 基本路径: /quote-b-api/depth-tick
* 完整URL: [https://quote.tradeswitcher.com/quote-b-api/depth-tick](https://quote.tradeswitcher.com/quote-b-api/depth-tick)

## 请求示例

**1、美股、港股、A股、大盘数据接口地址：**

在发送查询请求时，必须包含方法名和token信息。一个请求的示例如下：\
[https://quote.tradeswitcher.com/quote-stock-b-api/depth-tick?token=您的token\&query=queryData](https://quote.tradeswitcher.com/quote-stock-b-api/depth-tick?token=%E6%82%A8%E7%9A%84token\&query=queryData)

**2、外汇、贵金属、加密货币、商品接口地址：**

在发送查询请求时，必须包含方法名和token信息。一个请求的示例如下：\
[https://quote.tradeswitcher.com/quote-b-api/depth-tick?token=您的token\&query=queryData](https://quote.tradeswitcher.com/quote-b-api/depth-tick?token=%E6%82%A8%E7%9A%84token\&query=queryData)

## 请求参数

| 名称    | 位置    | 类型     | 必选 | 说明            |
| ----- | ----- | ------ | -- | ------------- |
| token | query | string | 否  |               |
| query | query | string | 否  | 查看query请求参数说明 |

## query请求参数

将如下json进行UrlEncode编码，赋值到url的查询字符串的query里

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

| 名称             | 类型        | 必选 | 说明 |
| -------------- | --------- | -- | -- |
| trace          | string    | 是  |    |
| data           | object    | 是  |    |
| » symbol\_list | \[object] | 是  |    |
| »» code        | string    | 否  | 代码 |

## 返回示例

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

## 返回结果

| 状态码 | 状态码含义 | 说明 | 数据模型   |
| --- | ----- | -- | ------ |
| 200 | OK    | OK | Inline |

| 名称             | 类型        | 必选    | 说明         |
| -------------- | --------- | ----- | ---------- |
| » ret          | integer   | true  | 返回code     |
| » msg          | string    | true  | 返回code对应消息 |
| » trace        | string    | true  | 请求的trace   |
| » data         | object    | true  |            |
| »» tick\_list  | \[object] | true  |            |
| »»» code       | string    | false | 代码         |
| »»» seq        | string    | false | 报价序号       |
| »»» tick\_time | string    | false | 报价时间戳      |
| »»» bids       | \[object] | false | bid列表      |
| »»»» price     | string    | false | 价          |
| »»»» volume    | string    | false | 量          |
| »»» asks       | \[object] | false | ask列表      |
| »»»» price     | string    | false | 价          |
| »»»» volume    | string    | false | 量          |

{% swagger src="../../.gitbook/assets/api.json" path="/quote-stock-b-api/depth-tick" method="get" %}
[api.json](../../.gitbook/assets/api.json)
{% endswagger %}

#### AllTick网站

{% hint style="info" %}
官方网站：[https://alltick.co/](https://alltick.co/)
{% endhint %}
