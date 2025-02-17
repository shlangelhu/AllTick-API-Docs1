# 心跳

[English ](https://en.apis.alltick.co/websocket-api/stock-websocket-interface-api/ping-pang)/ 中文

## 接口说明

要求请求者每10秒发送一次，在30秒内如果没有收到心跳请求，就会认为超时，断开请求者的websocket连接

## 请求-协议号：22000

### 数据结构(json)

```
{
    "cmd_id":22000,
    "seq_id":123,
    "trace":"3baaa938-f92c-4a74-a228-fd49d5e2f8bc-1678419657806",
    "data":{
    }
}
```

## 应答-协议号：22001 <a href="#ying-da-xie-yi-hao-22001" id="ying-da-xie-yi-hao-22001"></a>

### 数据结构(json)

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

#### AllTick网站

{% hint style="info" %}
官方网站：[https://alltick.co/](https://alltick.co/)
{% endhint %}
