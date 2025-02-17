# HTTP Common Standard Headers

English / [中文](https://apis.alltick.co/jie-ru-liu-cheng/tong-yong-biao-zhun-tou-shuo-ming/http-tong-yong-biao-zhun-tou)

## Request Common Standard Header

| Field | Name            | Type   | Required | Description                                                                                                         |
| ----- | --------------- | ------ | -------- | ------------------------------------------------------------------------------------------------------------------- |
| trace | Tracking Number | string | Yes      | The requester generates a unique number, the response will be consistent with the request, the maximum length is 64 |
| data  | Data body       | object | Yes      | For specific data format, see each interface definition.                                                            |

```
{
    "trace":"c2a8a146-a647-4d6f-ac07-8c4805bf0b74",
    "data":{
    }
}
```

## Introduction to response common standard header

| Field | Name            | Type   | Description                                                                                                         |
| ----- | --------------- | ------ | ------------------------------------------------------------------------------------------------------------------- |
| ret   | Return value    | int32  | Error code description                                                                                              |
| msg   | Message         | string | A detailed description of success or failure                                                                        |
| trace | Tracking Number | string | The requester generates a unique number, the response will be consistent with the request, the maximum length is 64 |
| data  | Data body       | object | For specific data format, see each interface definition.                                                            |

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

### Official Website

{% hint style="info" %}
Official website: [https://alltick.co/](https://alltick.co/)
{% endhint %}
