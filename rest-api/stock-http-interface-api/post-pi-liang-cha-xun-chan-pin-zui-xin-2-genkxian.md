# POST 批量查询产品最新2根K线

[English](https://en.apis.alltick.co/rest-api/stock-http-interface-api/get-batch-k-line-query) / 中文

## POST /batch-kline

## **接口说明**

该接口可以一次性批量查询多个产品，且可批量一次性查询多个k线类型（k线类型指的是1分钟，15分钟，30分钟等），<mark style="color:red;">**但只能批量查询最新的2根k线。**</mark>

使用HTTP接口获取K线的客户，建议将/kline和/batch-kline这2个接口结合使用,步骤如下：

* 首先，通过 /kline 接口轮询请求历史数据并存储到本地数据库，后续历史数据可直接从客户的数据库获取，无需再通过接口请求。
* 然后，后续持续使用 /batch-kline 接口批量请求多个产品的最新2根K线，并将数据更新到数据库。&#x20;

这种方式能够快速更新最新的K线，同时避免频繁请求历史K线造成频率受到限制。

## 请求频率

<table data-full-width="true"><thead><tr><th width="81">计划</th><th width="363">单独请求</th><th width="375">同时请求多个http接口</th></tr></thead><tbody><tr><td>免费</td><td>1、每10秒，可1次请求<br>2、每次可批量查询10组数据，每1组数据=1只产品数量+1种K线类型，例如同时获取BTCUSDT的1分钟k线和5分钟k线，这就是2组数据</td><td>1、同1秒只能请求1个口<br>2、所有接口相加，1分钟最大请求10次(6秒1次)<br><mark style="color:red;">3、需注意/batch-kline接口需间隔10秒</mark><br>4、每天总共最大可请求14400次，超过则第二天凌晨恢复使用</td></tr><tr><td>基础</td><td>1、每3秒，只能1次请求<br>2、每次可批量查询100组数据，每1组数据=1只产品数量+1种K线类型，例如同时获取BTCUSDT的1分钟k线和5分钟k线，这就是2组数据</td><td>1、同1秒只能请求1个接口<br>2、所有接口相加，1分钟最大请求60次(1秒1次)<br><mark style="color:red;">3、需注意/batch-kline接口需间隔3秒</mark><br>4、每天总共最大可请求86400次，超过则第二天凌晨恢复使用</td></tr><tr><td>高级</td><td>1、每2秒，只能1次请求<br>2、每次可批量查询200组数据，每1组数据=1只产品数量+1种K线类型，例如同时获取BTCUSDT的1分钟k线和5分钟k线，这就是2组数据</td><td>1、所有接口相加，1分钟最大请求600次(1秒10次)<br><mark style="color:red;">2、需注意/batch-kline接口需间隔2秒</mark><br>3、每天总共最大可请求864000次，超过则第二天凌晨恢复使用</td></tr><tr><td>专业</td><td>1、每1秒，只能1次请求<br>2、每次可批量查询500组数据，每1组数据=1只产品数量+1种K线类型，例如同时获取BTCUSDT的1分钟k线和5分钟k线，这就是2组数据</td><td>1、所有接口相加，1分钟最大请求1200次(1秒20次)<br><mark style="color:red;">2、需注意/batch-kline接口需间隔1秒</mark><br>3、每天总共最大可请求1728000次，超过则第二天凌晨恢复使用</td></tr><tr><td>全部港股</td><td>1、每1秒，只能1次请求<br>2、每次可批量查询500组数据，每1组数据=1只产品数量+1种K线类型，例如同时获取BTCUSDT的1分钟k线和5分钟k线，这就是2组数据</td><td>1、所有接口相加，1分钟最大请求1200次(1秒20次)<br><mark style="color:red;">2、需注意/batch-kline接口需间隔1秒</mark><br>3、每天总共最大可请求1728000次，超过则第二天凌晨恢复使用</td></tr><tr><td>全部A股</td><td>1、每1秒，只能1次请求<br>2、每次可批量查询500组数据，每1组数据=1只产品数量+1种K线类型，例如同时获取BTCUSDT的1分钟k线和5分钟k线，这就是2组数据</td><td>1、所有接口相加，1分钟最大请求1200次(1秒20次)<br><mark style="color:red;">2、需注意/batch-kline接口需间隔1秒</mark><br>3、每天总共最大可请求1728000次，超过则第二天凌晨恢复使用</td></tr><tr><td>全部美股</td><td>1、每1秒，只能1次请求<br>2、每次可批量查询500组数据，每1组数据=1只产品数量+1种K线类型，例如同时获取BTCUSDT的1分钟k线和5分钟k线，这就是2组数据</td><td>1、所有接口相加，1分钟最大请求1200次(1秒20次)<br><mark style="color:red;">2、需注意/batch-kline接口需间隔1秒</mark><br>3、每天总共最大可请求1728000次，超过则第二天凌晨恢复使用</td></tr></tbody></table>

## 接口限制 <a href="#jie-kou-xian-zhi" id="jie-kou-xian-zhi"></a>

1、请务必阅读：[HTTP接口限制说明](https://apis.alltick.co/integration-process/interface-restriction-description/http-interface-restrictions)

2、请务必阅读：[错误码说明](https://apis.alltick.co/integration-process/interface-restriction-description/error-code-description)

## 接口地址

**1、美股、港股、A股、大盘数据接口地址：**

* 基本路径: /quote-stock-b-api/batch-kline
* 完整URL: [https://quote.alltick.io/quote-stock-b-api/batch-kline](https://quote.alltick.io/quote-stock-b-api/batch-kline)

**2、外汇、贵金属、加密货币、商品接口地址：**

* 基本路径: /quote-b-api/batch-kline
* 完整URL: [https://quote.alltick.io/quote-b-api/](https://quote.alltick.io/quote-b-api/kline)[batch-kline](https://quote.alltick.io/quote-stock-b-api/batch-kline)

## 请求示例

**1、美股、港股、A股、大盘数据请求示例：**

批量查询产品最新K线功能，由于批量查询参数比较多，放入body中，url参数中只保留token字段参数。\
在发送查询请求时，必须包含方法名和token信息。一个请求的示例如下：\
[https://quote.alltick.io/quote-stock-b-api/batch-kline?token=您的token](https://quote.alltick.io/quote-stock-b-api/batch-kline?token=%E6%82%A8%E7%9A%84token)

**2、外汇、贵金属、加密货币、商品请求示例：**

批量查询产品最新K线功能，由于批量查询参数比较多，放入body中，url参数中只保留token字段参数。\
在发送查询请求时，必须包含方法名和token信息。一个请求的示例如下：\
[https://quote.alltick.io/quote-b-api/batch-kline?token=您的token](https://quote.alltick.io/quote-b-api/batch-kline?token=%E6%82%A8%E7%9A%84token)

## <mark style="color:red;">批量查询产品最新K线功能，由于批量查询参数比较多，放入body中，url参数中只保留token字段参数。</mark>

## Body 请求参数

```
{
  "trace": "c2a8a146-a647-4d6f-ac07-8c4805bf0b74",
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

## 请求参数

<table data-full-width="true"><thead><tr><th width="258.734375">名称</th><th width="116">位置</th><th width="135">类型</th><th width="98">必选</th><th>说明</th></tr></thead><tbody><tr><td>token</td><td>query</td><td>string</td><td>是</td><td>如果不知道你的token，请联系相关人员索要</td></tr><tr><td>body</td><td>body</td><td>object</td><td>否</td><td></td></tr><tr><td>» trace</td><td>body</td><td>string</td><td>是</td><td>追踪码，用来查询日志使用，请保证每次请求时唯一</td></tr><tr><td>» data</td><td>body</td><td>object</td><td>是</td><td></td></tr><tr><td>»» data_list</td><td>body</td><td>[object]</td><td>是</td><td></td></tr><tr><td>»»» code</td><td>body</td><td>string</td><td>是</td><td>请查看code列表，选择你要查询的code：<a href="https://docs.google.com/spreadsheets/d/1avkeR1heZSj6gXIkDeBt8X3nv4EzJetw4yFuKjSDYtA/edit?gid=495387863#gid=495387863">[点击code列表]</a></td></tr><tr><td>»»» kline_type</td><td>body</td><td>integer</td><td>是</td><td>k线类型<br>1、1是1分钟K，2是5分钟K，3是15分钟K，4是30分钟K，5是小时K，6是2小时K(股票不支持2小时)，7是4小时K(股票不支持4小时)，8是日K，9是周K，10是月K （注：股票不支持2小时K、4小时K）<br>2、最短的k线只支持1分钟</td></tr><tr><td>»»» kline_timestamp_end</td><td>body</td><td>integer</td><td>是</td><td>从指定时间往前查询K线<br>1、传0表示从当前最新的交易日往前查k线<br>2、指定时间请传时间戳，传时间戳表示从该时间戳往前查k线<br>3、只有外汇贵金属加密货币支持传时间戳，股票类的code不支持</td></tr><tr><td>»»» query_kline_num</td><td>body</td><td>integer</td><td>是</td><td>表示查询多少根K线，该接口最大只能查询2根k线</td></tr><tr><td>»»» adjust_type</td><td>body</td><td>integer</td><td>是</td><td>复权类型,对于股票类的code才有效，例如：0:除权,1:前复权，目前仅支持0</td></tr></tbody></table>

## 返回示例

```
{
  "ret": 200,
  "msg": "ok",
  "trace": "c2a8a146-a647-4d6f-ac07-8c4805bf0b74",
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

## 返回结果

<table data-full-width="true"><thead><tr><th>状态码</th><th>状态码含义</th><th>说明</th><th>数据模型</th></tr></thead><tbody><tr><td>200</td><td>OK</td><td>OK</td><td>Inline</td></tr></tbody></table>

<table data-full-width="true"><thead><tr><th width="237">名称</th><th width="147">类型</th><th width="145">必选</th><th>说明</th></tr></thead><tbody><tr><td>» ret</td><td>integer</td><td>true</td><td></td></tr><tr><td>» msg</td><td>string</td><td>true</td><td></td></tr><tr><td>» trace</td><td>string</td><td>true</td><td></td></tr><tr><td>» data</td><td>object</td><td>true</td><td></td></tr><tr><td>»» kline_list</td><td>[array]</td><td>true</td><td></td></tr><tr><td>»»» code</td><td>string</td><td>true</td><td>产品代码</td></tr><tr><td>»»» kline_type</td><td>integer</td><td>true</td><td>k线类型<br>1、1是1分钟K，2是5分钟K，3是15分钟K，4是30分钟K，5是小时K，6是2小时K(股票不支持2小时)，7是4小时K(股票不支持4小时)，8是日K，9是周K，10是月K （注：股票不支持2小时K、4小时K）<br>2、最短的k线只支持1分钟</td></tr><tr><td>»»» kline_data</td><td>[array]</td><td>true</td><td></td></tr><tr><td>»»»» timestamp</td><td>string</td><td>true</td><td>该K线时间戳</td></tr><tr><td>»»»» open_price</td><td>string</td><td>true</td><td>该K线开盘价</td></tr><tr><td>»»»» close_price</td><td>string</td><td>true</td><td>该K线收盘价</td></tr><tr><td>»»»» high_price</td><td>string</td><td>true</td><td>该K线最高价</td></tr><tr><td>»»»» low_price</td><td>string</td><td>true</td><td>该K线最低价</td></tr><tr><td>»»»» volume</td><td>string</td><td>true</td><td>该K线成交数量</td></tr><tr><td>»»»» turnover</td><td>string</td><td>true</td><td>该K线成交金额</td></tr></tbody></table>

{% openapi src="../../.gitbook/assets/api (1).json" path="/quote-stock-b-api/batch-kline" method="post" %}
[api (1).json](<../../.gitbook/assets/api (1).json>)
{% endopenapi %}

#### AllTick网站

{% hint style="info" %}
官方网站：[https://alltick.co/](https://alltick.co/)
{% endhint %}
