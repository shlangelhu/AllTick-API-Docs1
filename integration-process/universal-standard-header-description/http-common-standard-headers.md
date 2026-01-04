---
description: HTTP 通用标准头 请求通用标准头介绍 应答通用标准头介绍
---

# HTTP 通用标准头

[English ](https://en.apis.alltick.co/integration-process/universal-standard-header-description/http-common-standard-headers)/ 中文

## 请求通用标准头介绍

| 字段    | 名称  | 类型     | 必填项 | 说明                        |
| ----- | --- | ------ | --- | ------------------------- |
| trace | 跟踪号 | string | 是   | 请求者生成唯一，响应与请求将保持一致,最大长度64 |
| data  | 数据体 | object | 是   | 具体数据格式见各个接口定义             |

```
{
    "trace":"c2a8a146-a647-4d6f-ac07-8c4805bf0b74",
    "data":{
    }
}
```

## 应答通用标准头介绍

| 字段    | 名称  | 类型     | 说明                                                                                                                                |
| ----- | --- | ------ | --------------------------------------------------------------------------------------------------------------------------------- |
| ret   | 返回值 | int32  | [错误码说明](https://github.com/alltick/realtime-forex-crypto-stock-tick-finance-websocket-api/blob/main/error_code_description_cn.md) |
| msg   | 消息  | string | 对成功或者失败具体的描述                                                                                                                      |
| trace | 跟踪号 | string | 请求者生成唯一，响应与请求将保持一致,最大长度64                                                                                                         |
| data  | 数据体 | object | 具体数据格式见各个接口定义                                                                                                                     |

```
{
    "ret":202,
    "msg":"request data param invalid",
    "trace":"c2a8a146-a647-4d6f-ac07-8c4805bf0b74",
    "data":{
    }    
}
```



***

#### AllTick网站

{% hint style="info" %}
官方网站：[https://alltick.co/](https://alltick.co/)
{% endhint %}
