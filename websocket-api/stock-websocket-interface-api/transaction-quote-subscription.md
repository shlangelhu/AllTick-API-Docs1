# 最新成交价(实时逐笔Tick数据)批量订阅

[English ](https://en.apis.alltick.co/websocket-api/stock-websocket-interface-api/transaction-quote-subscription)/ 中文

## 接口说明

该接口支持批量订阅产品的最新成交价(实时逐笔Tick数据)，不支持历史成交价格(历史逐笔tick数据)。

该接口特性为对于每一个websocket连接，每发送一次该请求，后台会默认覆盖上一次订阅请求（例如，如果您最初订阅了A、B、C这三只产品，想要追加订阅E、F、G，则需要重新发送一次A、B、C、E、F、G），订阅成功后会进行推送数据。

注意：

1、订阅一次成功后，不需要再频繁的发起订阅请求，要求每10秒发送一次心跳，接口就会实时推送数据，在30秒内如果没有收到心跳请求，就会认为超时，断开请求者的websocket连接

2、接入时，客户可增加断开自动重连的逻辑，确保因网络等原因断开可自动重连

## 接口限制

1、请务必阅读：[Websocket限制说明](../../integration-process/interface-restriction-description/websocket-interface-limitations.md)

2、请务必阅读：[错误码说明](../../integration-process/interface-restriction-description/error-code-description.md)

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

<table><thead><tr><th width="151.4140625">字段</th><th width="130.4140625">名称</th><th width="135.0859375">类型</th><th width="120.1796875">必填项</th><th>说明</th></tr></thead><tbody><tr><td>code</td><td>代码</td><td>string</td><td>是</td><td>具体内容，请查阅code列表：<a href="https://docs.google.com/spreadsheets/d/1avkeR1heZSj6gXIkDeBt8X3nv4EzJetw4yFuKjSDYtA/edit?gid=495387863#gid=495387863">[点击code列表]</a></td></tr></tbody></table>

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
            }
        ]
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

<table data-full-width="false"><thead><tr><th width="145.17578125">字段</th><th width="131.89453125">名称</th><th width="110.7265625">类型</th><th>说明</th></tr></thead><tbody><tr><td>code</td><td>代码</td><td>string</td><td>具体内容，请查阅code列表：<a href="https://docs.google.com/spreadsheets/d/1avkeR1heZSj6gXIkDeBt8X3nv4EzJetw4yFuKjSDYtA/edit?gid=495387863#gid=495387863">[点击code列表]</a></td></tr><tr><td>seq</td><td>报价序号</td><td>string</td><td></td></tr><tr><td>tick_time</td><td>报价时间戳</td><td>string</td><td>单位毫秒</td></tr><tr><td>price</td><td>成交价</td><td>string</td><td></td></tr><tr><td>volumn</td><td>成交量</td><td>string</td><td></td></tr><tr><td>turnover</td><td>成交额</td><td>string</td><td>成交额：<br>1、外汇、贵金属、能源不返回成交额，可自行根据每次推送的数据计算，计算公式：turnover = price * volume<br>2、股票、加密货币正常返回成交额。</td></tr><tr><td>trade_direction</td><td>成交方向</td><td>string</td><td>交易方向：<br>1、0为默认值，1为Buy，2为SELL<br>2、外汇、贵金属、能源默认只会返回0<br>3、股票、加密货币根据市场情况会返回0、1、2<br>4、详细说明：<br>0:表示中性盘，即以买一价与卖一价之间的价格撮合成交。<br>1:表示主动买入，即以卖一价或者更高价格成交的股票 <br>2:表示主动卖出，即以买一价或者更低价格成交的股票</td></tr></tbody></table>

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
        "trade_direction": 1
    }
}
```





#### AllTick网站

{% hint style="info" %}
官方网站：[https://alltick.co/](https://alltick.co/)
{% endhint %}
