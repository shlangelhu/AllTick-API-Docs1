# 最新成交价(Tick数据)批量订阅

[English ](https://en.apis.alltick.co/websocket-api/stock-websocket-interface-api/transaction-quote-subscription)/ 中文

## 接口说明

该接口支持批量订阅产品的最新成交价(Tick数据)，该接口特性为对于每一个websocket连接，每发送一次该请求，后台会默认覆盖上一次订阅请求。订阅成功后会进行推送数据。

注意：

1、订阅一次成功后，不需要再频繁的发起订阅请求，要求每10秒发送一次心跳，接口就会实时推送数据，在30秒内如果没有收到心跳请求，就会认为超时，断开请求者的websocket连接

2、接入时，客户可增加断开自动重连的逻辑，确保因网络等原因断开可自动重连

## 接口地址

**1、美股、港股、A股、大盘数据接口地址：**

* 基本路径: /quote-stock-b-ws-api
* 完整URL: wss://quote.alltick.io/quote-stock-b-ws-api

**2、外汇、贵金属、加密货币、商品接口地址：**

* 基本路径: /quote-b-ws-api
* 完整URL: wss://quote.alltick.io/quote-b-ws-api

## 请求示例

**1、美股、港股、A股、大盘数据请求示例：**

每次建立连接时，必须在URL中附加您的认证token，如下所示：

wss://quote.alltick.io/quote-stock-b-ws-api?token=您的token

连接成功后，您可以根据需要订阅特定的股票市场数据。详细的调用方法请参考下面的文档说明。

**2、外汇、贵金属、加密货币、商品请求示例：**

每次建立连接时，必须在URL中附加您的认证token，如下所示：

wss://quote.alltick.io/quote-b-ws-api?token=您的token

连接成功后，您可以根据需要订阅特定的外汇、加密货币、贵金属、商品数据。详细的调用方法请参考下面的文档说明。

## 请求-协议号：22004

#### data定义 <a href="#data-ding-yi" id="data-ding-yi"></a>

| 字段           | 名称   | 类型    | 必填项 | 说明              |
| ------------ | ---- | ----- | --- | --------------- |
| symbol\_list | 产品列表 | array | 是   | 具体格式见下面symbol定义 |

#### symbol定义 <a href="#symbol-ding-yi" id="symbol-ding-yi"></a>

| 字段   | 名称 | 类型     | 必填项 | 说明             |
| ---- | -- | ------ | --- | -------------- |
| code | 代码 | string | 是   | 具体内容，请查阅code列表 |

### 数据结构(json)

```
{
    "cmd_id":22004,
    "seq_id":123,
    "trace":"3baaa938-f92c-4a74-a228-fd49d5e2f8bc-1678419657806",
    "data":{
        "symbol_list": [
            {
        "code": "BTCUSDT"
            },
    ],
    }
}
```

## 应答-协议号：22005 <a href="#ying-da-xie-yi-hao-22001" id="ying-da-xie-yi-hao-22001"></a>

### 数据结构(json)

```
{
    "ret":200,
    "msg":"ok",
    "cmd_id":22005,
    "seq_id":123,
    "trace":"3baaa938-f92c-4a74-a228-fd49d5e2f8bc-1678419657806",
    "data":{
    }    
}
```

## 推送-协议号：22998

#### data定义

<table data-full-width="false"><thead><tr><th>字段</th><th>名称</th><th>类型</th><th>说明</th></tr></thead><tbody><tr><td>code</td><td>代码</td><td>string</td><td>具体内容，请查阅code列表</td></tr><tr><td>seq</td><td>报价序号</td><td>string</td><td></td></tr><tr><td>tick_time</td><td>报价时间错</td><td>string</td><td>单位毫秒</td></tr><tr><td>price</td><td>成交价</td><td>string</td><td></td></tr><tr><td>volumn</td><td>成交量</td><td>string</td><td></td></tr><tr><td>turnover</td><td>成交额</td><td>string</td><td></td></tr><tr><td>trade_direction</td><td>成交方向</td><td>string</td><td>0为默认值，1为Buy，2为SELL</td></tr></tbody></table>

### 数据结构（json）

```
{
    "cmd_id":22998,
    "data":{
	"code": "1288.HK",
        "seq": "1605509068000001",
        "tick_time": "1605509068",
        "price": "651.12",
        "volume": "300",
        "turnover": "12345.6",
        "trade_direction": 1,
    }
}
```





#### AllTick网站

{% hint style="info" %}
官方网站：[https://alltick.co/](https://alltick.co/)
{% endhint %}
