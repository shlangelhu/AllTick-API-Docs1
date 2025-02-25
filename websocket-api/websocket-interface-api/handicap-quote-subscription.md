# Handicap Quote Subscription

English / [中文](https://apis.alltick.co/websocket-api/gu-piao-websocket-jie-kou-api/pan-kou-bao-jia-ding-yue)

## Interface Description

The feature of this interface is that for each websocket connection, every time the request is sent, the background will overwrite the previous subscription request by default. After the subscription is successful, the data will be pushed.

## Request - Protocol Number：22002

#### Data definition

| Field        | Name         | Type  | Required | Description                                              |
| ------------ | ------------ | ----- | -------- | -------------------------------------------------------- |
| symbol\_list | Product List | array | Yes      | See the symbol definition below for the specific format. |

#### Symbol definition

| Field        | Name        | Type   | Required | Description                                                                                                                                                                                                                                                             |
| ------------ | ----------- | ------ | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| code         | Code        | string | Yes      | For specific content, please refer to the code list                                                                                                                                                                                                                     |
| depth\_level | Depth level | uint32 | No       | If there is no depth\_level field, the background will only provide a quote for one layer, and the requested level is greater than the actual quote level, or if there is no depth\_level field, the background will provide as many layers as there are actual quotes. |

### Data Structure (JSON)

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

## Response-protocol number：22003 <a href="#ying-da-xie-yi-hao-22001" id="ying-da-xie-yi-hao-22001"></a>

### Data Structure (JSON)

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

## Push - Protocol Number: 22999

#### Definition of data

| Field      | Name            | Type   | Description                              |
| ---------- | --------------- | ------ | ---------------------------------------- |
| code       | Code            | string | Specific content, refer to the code list |
| seq        | Quote Number    | string |                                          |
| tick\_time | Quote Timestamp | string | In milliseconds                          |
| bids       | Bid Depth       | array  | See below for bids definition            |
| asks       | Ask Depth       | array  | See below for asks definition            |

#### bids definition

| Field  | Name       | Type   | Description |
| ------ | ---------- | ------ | ----------- |
| price  | Bid Price  | string |             |
| volume | Bid Volume | string |             |

asks definition

<table><thead><tr><th>Field</th><th width="187">Name</th><th>Type</th><th>Description</th></tr></thead><tbody><tr><td>price</td><td>Ask Price</td><td>string</td><td></td></tr><tr><td>volume</td><td>Ask Volume</td><td>string</td><td></td></tr></tbody></table>

### Data Structure (JSON)

```
{
    "cmd_id":22999,
    "data":{
	"code": "HK-1288",
        "seq": "1605509068000001",
        "tick_time": "1605509068",
        "bids": [
            {
                "price": "9.12",
                "volume": "9.12",
            },
        ],
        "asks": [
            {
                "price": "147.12",
                "volume": "147.12",
            },
        ],
    }
}
```

### Official Website

{% hint style="info" %}
Official website: [https://alltick.co/](https://alltick.co/)
{% endhint %}
