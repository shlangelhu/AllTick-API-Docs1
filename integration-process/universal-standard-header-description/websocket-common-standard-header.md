# Websocket Common Standard Header

English / [中文](https://apis.alltick.co/jie-ru-liu-cheng/tong-yong-biao-zhun-tou-shuo-ming/websocket-tong-yong-biao-zhun-tou)

## Request Common Standard Header Introduction

| Field   | Name             | Type   | Required                                             | Description                                                                                                         |
| ------- | ---------------- | ------ | ---------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| cmd\_id | Agreement number | uint32 | For details, see each interface definition provided. |                                                                                                                     |
| seq\_id | Serial number    | uint32 | Yes                                                  | The requester generates unique information, and the response will be consistent with the request.                   |
| trace   | Tracking Number  | string | Yes                                                  | The requester generates a unique number, the response will be consistent with the request, the maximum length is 64 |
| data    | Data body        | object | Yes                                                  | For specific data format, see each interface definition.                                                            |

```
{
    "cmd_id":22000,
    "seq_id":123,
    "trace":"asdfsdfa",
    "data":{
    }
}
```

## Introduction to response common standard header

| Field   | Name             | Type   | Description                                                                                                         |
| ------- | ---------------- | ------ | ------------------------------------------------------------------------------------------------------------------- |
| ret     | Return value     | int32  | Error code description                                                                                              |
| msg     | Message          | string | A detailed description of success or failure                                                                        |
| cmd\_id | Agreement number | uint32 | For details, see each interface definition provided.                                                                |
| seq\_id | Serial number    | uint32 | The requester generates unique information, and the response will be consistent with the request.                   |
| trace   | Tracking Number  | string | The requester generates a unique number, the response will be consistent with the request, the maximum length is 64 |
| data    | Data body        | object | For specific data format, see each interface definition.                                                            |

```
{
    "ret":201,
    "msg":"request header param invalid",
    "cmd_id":0,
    "seq_id":0,
    "trace":"",
    "data":{
    }    
}
```



***

### Official Website

{% hint style="info" %}
Official website: [https://alltick.co/](https://alltick.co/)
{% endhint %}
