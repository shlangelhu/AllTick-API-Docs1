# Transaction quote subscription

English / [中文](https://apis.alltick.co/websocket-api/gu-piao-websocket-jie-kou-api/cheng-jiao-bao-jia-ding-yue)

## Interface Description

The feature of this interface is that for each websocket connection, every time the request is sent, the background will overwrite the previous subscription request by default. After the subscription is successful, the data will be pushed.

## Request - Protocol Number：22004

#### data定义 <a href="#data-ding-yi" id="data-ding-yi"></a>

| Field        | Name        | Type  | Required | Description                                              |
| ------------ | ----------- | ----- | -------- | -------------------------------------------------------- |
| symbol\_list | Symbol List | array | Yes      | See the symbol definition below for the specific format. |

#### symbol定义 <a href="#symbol-ding-yi" id="symbol-ding-yi"></a>

| Field | Name | Type   | Required | Description                                         |
| ----- | ---- | ------ | -------- | --------------------------------------------------- |
| code  | Code | string | Yes      | For specific content, please refer to the code list |

### Data Structure (JSON))

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

## Response-protocol number：22005 <a href="#ying-da-xie-yi-hao-22001" id="ying-da-xie-yi-hao-22001"></a>

### Data Structure (JSON)

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

### Official Website

{% hint style="info" %}
Official website: [https://alltick.co/](https://alltick.co/)
{% endhint %}
