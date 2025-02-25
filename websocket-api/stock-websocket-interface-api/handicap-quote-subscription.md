# 最新盘口(Order Book)订阅

[English ](https://en.apis.alltick.co/websocket-api/stock-websocket-interface-api/handicap-quote-subscription)/ 中文

## 接口说明

该接口支持订阅产品的最新盘口(Order Book)，该接口特性：对于每一个websocket连接，每发送一次该请求，后台会默认覆盖上一次订阅请求。订阅成功后会进行推送数据。

注意：

1、订阅一次成功后，不需要再频繁的发起订阅请求，要求每10秒发送一次心跳，接口就会实时推送数据，在30秒内如果没有收到心跳请求，就会认为超时，断开请求者的websocket连接

2、接入时，客户可增加断开自动重连的逻辑，确保因网络等原因断开可自动重连

3、以下是每类产品最大的盘口深度：

3.1 不活跃的产品存在小于下面列的最大档的情况，属于正常情况

3.2 存在单边深度是空的情况，例如股票涨停跌停时，单边盘口可能是空的

<table><thead><tr><th width="82"></th><th width="181">外汇、贵金属、原油</th><th width="97">加密货币</th><th width="100">港股</th><th width="92">美股</th><th>沪深A股</th></tr></thead><tbody><tr><td>深度说明</td><td>最大5档</td><td>最大5档</td><td>最大10档</td><td>最大1档</td><td>最大5档</td></tr></tbody></table>

## 接口地址

**1、美股、港股、A股、大盘数据接口地址：**

* 基本路径: /quote-stock-b-ws-api
* 完整URL: wss://quote.alltick.io/quote-stock-b-ws-api

**2、外汇、贵金属、加密货币、商品接口地址：**

* 基本路径: /quote-b-ws-api
* 完整URL: wss://quote.alltick.io/quote-b-ws-api

## 请求示例 <a href="#qing-qiu-shi-li" id="qing-qiu-shi-li"></a>

**1、美股、港股、A股、大盘数据请求示例：**

每次建立连接时，必须在URL中附加您的认证token，如下所示：

wss://quote.alltick.io/quote-stock-b-ws-api?token=您的token

连接成功后，您可以根据需要订阅特定的股票市场数据。详细的调用方法请参考下面的文档说明。

**2、外汇、贵金属、加密货币、商品请求示例：**

每次建立连接时，必须在URL中附加您的认证token，如下所示：

wss://quote.alltick.io/quote-b-ws-api?token=您的token

连接成功后，您可以根据需要订阅特定的外汇、加密货币、贵金属、商品数据。详细的调用方法请参考下面的文档说明。\\

## 请求-协议号：22002

#### data定义 <a href="#data-ding-yi" id="data-ding-yi"></a>

| 字段           | 名称   | 类型    | 必填项 | 说明              |
| ------------ | ---- | ----- | --- | --------------- |
| symbol\_list | 产品列表 | array | 是   | 具体格式见下面symbol定义 |

#### symbol定义 <a href="#symbol-ding-yi" id="symbol-ding-yi"></a>

| 字段           | 名称   | 类型     | 必填项 | 说明                                                                                   |
| ------------ | ---- | ------ | --- | ------------------------------------------------------------------------------------ |
| code         | 代码   | string | 是   | 具体内容，请查阅code列表                                                                       |
| depth\_level | 深度层级 | uint32 | 否   | 如果没有depth\_level字段时，后台只会提供一层的报价，请求的层级大于实际报价层级，或者如果没有depth\_level字段时，则后台按实际报价有多少层给多少层 |

### 数据结构(json)

```
{
    "cmd_id":22002,
    "seq_id":123,
    "trace":"3baaa938-f92c-4a74-a228-fd49d5e2f8bc-1678419657806",
    "data":{
        "symbol_list": [
            {
        "code": "BTCUSDT",
                "depth_level": 5,
            }
    ]
    }
}
```

## 应答-协议号：22003 <a href="#ying-da-xie-yi-hao-22001" id="ying-da-xie-yi-hao-22001"></a>

### 数据结构(json)

```
{
    "ret":200,
    "msg":"ok",
    "cmd_id":22003,
    "seq_id":123,
    "trace":"3baaa938-f92c-4a74-a228-fd49d5e2f8bc-1678419657806",
    "data":{
    }    
}
```

## 推送-协议号：22999

#### data定义

|     字段     |   名称  |   类型   |       说明       |
| :--------: | :---: | :----: | :------------: |
|    code    |   代码  | string | 具体内容，请查阅code列表 |
|     seq    |  报价序号 | string |                |
| tick\_time | 报价时间戳 | string |      单位毫秒      |
|    bids    | bid深度 | string |    见下面bids定义   |
|    asks    | ask深度 | string |    见下面asks定义   |

#### bids定义

|   字段   |    名称    |   类型   |  说明 |
| :----: | :------: | :----: | :-: |
|  price | 买一价，买盘价格 | string |     |
| volume |  买一量，买盘量 | string |     |

#### asks定义

|   字段   |    名称    |   类型   |  说明 |
| :----: | :------: | :----: | :-: |
|  price | 卖一价，卖盘价格 | string |     |
| volume |  卖一量，卖盘量 | string |     |

#### AllTick网站

{% hint style="info" %}
官方网站：[https://alltick.co/](https://alltick.co/)
{% endhint %}
