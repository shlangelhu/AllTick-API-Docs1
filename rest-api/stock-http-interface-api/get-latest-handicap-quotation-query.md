---
description: >-
  以下是每类产品最大的盘口深度： 1、不活跃的产品存在小于下面列的最大档的情况，属于正常情况
  2、存在单边深度是空的情况，例如股票涨停跌停时，单边盘口可能是空的
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# GET 最新盘口(最新深度、Order Book)查询

[English ](https://en.apis.alltick.co/rest-api/stock-http-interface-api/get-latest-handicap-quotation-query)/ 中文

## GET /depth-tick

## **接口说明**

以下是每类产品最大的盘口深度：

1、不活跃的产品存在小于下面列的最大档的情况，属于正常情况

2、存在单边深度是空的情况，例如股票涨停跌停时，单边盘口可能是空的

<table><thead><tr><th width="87"></th><th width="229">外汇、贵金属、原油</th><th width="97">加密货币</th><th width="100">港股</th><th width="92">美股</th><th>沪深A股</th></tr></thead><tbody><tr><td>深度说明</td><td>最大1 档<br>(只有委托价，没有量)</td><td>最大5档</td><td>最大10档</td><td>最大1档</td><td>最大5档</td></tr></tbody></table>

## **请求频率**

<table data-full-width="true"><thead><tr><th width="81">计划</th><th width="208">单独请求</th><th width="472">同时请求多个http接口</th></tr></thead><tbody><tr><td>免费</td><td>每10秒，只能1次请求</td><td><p>1、同1秒只能请求1个接口</p><p><mark style="color:red;">2、多个接口请求时，需注意/batch-kline接口需间隔10秒</mark><br>3、所有接口相加，1分钟最大请求10次(6秒1次)<br>4、每天总共最大可请求14400次，超过则第二天凌晨恢复使用</p></td></tr><tr><td>基础</td><td>每1秒，只能1次请求</td><td><p>1、同1秒只能请求1个接口</p><p><mark style="color:red;">2、多个接口请求时，需注意/batch-kline接口需间隔3秒</mark><br>3、所有接口相加，1分钟最大请求60次(1秒1次)<br>4、每天总共最大可请求86400次，超过则第二天凌晨恢复使用</p></td></tr><tr><td>高级</td><td>每1秒，最大可10次请求</td><td><p>1、所以接口相加，每1秒可请求10次</p><p><mark style="color:red;">2、多个接口请求时，需注意/batch-kline接口需间隔2秒</mark><br>3、所有接口相加，1分钟最大请求600次(1秒10次)<br>4、每天总共最大可请求864000次，超过则第二天凌晨恢复使用</p></td></tr><tr><td>专业</td><td>每1秒，最大可20次请求</td><td><p>1、所以接口相加，每1秒可请求20次</p><p><mark style="color:red;">2、多个接口请求时，需注意/batch-kline接口需间隔1秒</mark><br>3、所有接口相加，1分钟最大请求1200次(1秒20次)<br>4、每天总共最大可请求1728000次，超过则第二天凌晨恢复使用</p></td></tr><tr><td>全部港股</td><td>每1秒，最大可20次请求</td><td><p>1、所以接口相加，每1秒可请求20次</p><p><mark style="color:red;">2、多个接口请求时，需注意/batch-kline接口需间隔1秒</mark><br>3、所有接口相加，1分钟最大请求1200次(1秒20次)<br>4、每天总共最大可请求1728000次，超过则第二天凌晨恢复使用</p></td></tr><tr><td>全部A股</td><td>每1秒，最大可20次请求</td><td><p>1、所以接口相加，每1秒可请求20次</p><p><mark style="color:red;">2、多个接口请求时，需注意/batch-kline接口需间隔1秒</mark><br>3、所有接口相加，1分钟最大请求1200次(1秒20次)<br>4、每天总共最大可请求1728000次，超过则第二天凌晨恢复使用</p></td></tr><tr><td>全部美股</td><td>每1秒，最大可20次请求</td><td><p>1、所以接口相加，每1秒可请求20次</p><p><mark style="color:red;">2、多个接口请求时，需注意/batch-kline接口需间隔1秒</mark><br>3、所有接口相加，1分钟最大请求1200次(1秒20次)<br>4、每天总共最大可请求1728000次，超过则第二天凌晨恢复使用</p></td></tr></tbody></table>

## 接口限制 <a href="#jie-kou-xian-zhi" id="jie-kou-xian-zhi"></a>

1、请务必阅读：[HTTP接口限制说明](https://apis.alltick.co/integration-process/interface-restriction-description/http-interface-restrictions)

2、请务必阅读：[错误码说明](https://apis.alltick.co/integration-process/interface-restriction-description/error-code-description)

## 接口地址

**1、美股、港股、A股、大盘数据接口地址：**

* 基本路径: /quote-stock-b-api/depth-tick
* 完整URL: [https://quote.alltick.io/quote-stock-b-api/depth-tick](https://quote.alltick.io/quote-stock-b-api/depth-tick)

**2、外汇、贵金属、加密货币、原油、CFD指数、商品接口地址：**

* 基本路径: /quote-b-api/depth-tick
* 完整URL: [https://quote.alltick.io/quote-b-api/depth-tick](https://quote.alltick.io/quote-b-api/depth-tick)

## 请求示例

**1、美股、港股、A股、大盘数据接口地址：**

在发送查询请求时，必须包含方法名和token信息。一个请求的示例如下：\
[https://quote.alltick.io/quote-stock-b-api/depth-tick?token=您的token\&query=queryData](https://quote.alltick.io/quote-stock-b-api/depth-tick?token=%E6%82%A8%E7%9A%84token\&query=queryData)

**2、外汇、贵金属、加密货币、原油、CFD指数、商品接口地址：**

在发送查询请求时，必须包含方法名和token信息。一个请求的示例如下：\
[https://quote.alltick.io/quote-b-api/depth-tick?token=您的token\&query=queryData](https://quote.alltick.io/quote-b-api/depth-tick?token=%E6%82%A8%E7%9A%84token\&query=queryData)

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

<table><thead><tr><th width="146.37109375">名称</th><th width="116.65234375">类型</th><th width="82.66796875">必选</th><th>说明</th></tr></thead><tbody><tr><td>trace</td><td>string</td><td>是</td><td></td></tr><tr><td>data</td><td>object</td><td>是</td><td></td></tr><tr><td>» symbol_list</td><td>[object]</td><td>是</td><td></td></tr><tr><td>»» code</td><td>string</td><td>否</td><td>代码，选择你要查询的code：<a href="https://docs.google.com/spreadsheets/d/1avkeR1heZSj6gXIkDeBt8X3nv4EzJetw4yFuKjSDYtA/edit?gid=495387863#gid=495387863">[点击code列表]</a></td></tr></tbody></table>

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

<table><thead><tr><th width="160.484375">状态码</th><th width="158.4453125">状态码含义</th><th width="124.49609375">说明</th><th>数据模型</th></tr></thead><tbody><tr><td>200</td><td>OK</td><td>OK</td><td>Inline</td></tr></tbody></table>

<table><thead><tr><th width="156.6640625">名称</th><th width="156.48046875">类型</th><th width="123.80078125">必选</th><th>说明</th></tr></thead><tbody><tr><td>» ret</td><td>integer</td><td>true</td><td>返回code</td></tr><tr><td>» msg</td><td>string</td><td>true</td><td>返回code对应消息</td></tr><tr><td>» trace</td><td>string</td><td>true</td><td>请求的trace</td></tr><tr><td>» data</td><td>object</td><td>true</td><td></td></tr><tr><td>»» tick_list</td><td>[object]</td><td>true</td><td></td></tr><tr><td>»»» code</td><td>string</td><td>false</td><td>代码</td></tr><tr><td>»»» seq</td><td>string</td><td>false</td><td>报价序号</td></tr><tr><td>»»» tick_time</td><td>string</td><td>false</td><td>报价时间戳</td></tr><tr><td>»»» bids</td><td>[object]</td><td>false</td><td>bid列表</td></tr><tr><td>»»»» price</td><td>string</td><td>false</td><td>价</td></tr><tr><td>»»»» volume</td><td>string</td><td>false</td><td>量</td></tr><tr><td>»»» asks</td><td>[object]</td><td>false</td><td>ask列表</td></tr><tr><td>»»»» price</td><td>string</td><td>false</td><td>价</td></tr><tr><td>»»»» volume</td><td>string</td><td>false</td><td>量<br>1、外汇、贵金属、CFD指数不提供volume<br>2、股票，加密货币数据均提供volume</td></tr></tbody></table>

{% openapi src="../../.gitbook/assets/api.json" path="/quote-stock-b-api/depth-tick" method="get" %}
[api.json](../../.gitbook/assets/api.json)
{% endopenapi %}

#### AllTick网站

{% hint style="info" %}
官方网站：[https://alltick.co/](https://alltick.co/)
{% endhint %}
