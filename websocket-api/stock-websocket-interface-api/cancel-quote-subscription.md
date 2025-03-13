# 取消报价订阅

[English ](https://en.apis.alltick.co/websocket-api/stock-websocket-interface-api/cancel-quote-subscription)/ 中文

## 接口说明

取消报价订阅

## 请求-协议号：22006

#### data定义 <a href="#data-ding-yi" id="data-ding-yi"></a>

| 字段           | 名称   | 类型     | 必填项 | 说明                                        |
| ------------ | ---- | ------ | --- | ----------------------------------------- |
| cancel\_type | 取消类型 | uint32 | 是   | 0：取消所有报价订阅，1：取消盘口报价订阅，2：取消成交报价订阅，3：取消汇率订阅 |

### 数据结构(json)

```
{
    "cmd_id":22006,
    "seq_id":123,
    "trace":"3baaa938-f92c-4a74-a228-fd49d5e2f8bc-1678419657806",
    "data":{
        "cancel_type": 1
    }
}
```

## 应答-协议号：22007 <a href="#ying-da-xie-yi-hao-22001" id="ying-da-xie-yi-hao-22001"></a>

### 数据结构(json)

```
{
    "ret":200,
    "msg":"ok",
    "cmd_id":22007,
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
