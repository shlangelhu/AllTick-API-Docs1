---
description: >-
  Cancel quote subscription Request - Protocol Number：22006 Data definition Data
  Structure (JSON)
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Cancel quote subscription

English / [中文](https://apis.alltick.co/websocket-api/gu-piao-websocket-jie-kou-api/qu-xiao-bao-jia-ding-yue)

## Interface Description

Cancel quote subscription

## Request - Protocol Number：22006

#### Data definition

<table><thead><tr><th>Field</th><th>Name</th><th>Type</th><th width="135">Required</th><th>Description</th></tr></thead><tbody><tr><td>cancel_type</td><td>Cancellation type</td><td>uint32</td><td>Yes</td><td>0: Cancel all quotation subscriptions, 1: Cancel handicap quotation subscription, 2: Cancel transaction quotation subscription, 3: Cancel exchange rate subscription</td></tr></tbody></table>

### Data Structure (JSON)

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

## Response-protocol number：22007 <a href="#ying-da-xie-yi-hao-22001" id="ying-da-xie-yi-hao-22001"></a>

### Data Structure (JSON)

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

### Official Website

{% hint style="info" %}
Official website: [https://alltick.co/](https://alltick.co/)
{% endhint %}
