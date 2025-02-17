# Ping Pong

English / [中文](https://apis.alltick.co/websocket-api/gu-piao-websocket-jie-kou-api/xin-tiao)

## Interface Description

The requester is required to send a heartbeat request every 10 seconds. If no heartbeat request is received within 30 seconds, it will be considered a timeout, and the requester's WebSocket connection will be disconnected.

## Request - Protocol Number: 22000

### Data Structure (JSON)

```
{
    "cmd_id":22000,
    "seq_id":123,
    "trace":"3baaa938-f92c-4a74-a228-fd49d5e2f8bc-1678419657806",
    "data":{
    }
}
```

## Response-protocol number：22001 <a href="#ying-da-xie-yi-hao-22001" id="ying-da-xie-yi-hao-22001"></a>

### Data Structure (JSON)

```
{
    "ret":200,
    "msg":"ok",
    "cmd_id":22001,
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
