# 错误码说明

[English ](https://en.apis.alltick.co/integration-process/interface-restriction-description/error-code-description)/ 中文

<table><thead><tr><th width="174">错误码</th><th width="273">错误内容</th><th>含义</th></tr></thead><tbody><tr><td>200</td><td>ok</td><td>成功</td></tr><tr><td>400</td><td>request header param invalid</td><td>请求JSON第一层参数错误</td></tr><tr><td>400</td><td>request data param invalid</td><td>请求JSON中data字段参数错误</td></tr><tr><td>401</td><td>token invalid</td><td>token无效</td></tr><tr><td>402</td><td>query invalid</td><td>请求的query参数错误</td></tr><tr><td>429</td><td>rate limit</td><td>请求频率限制</td></tr><tr><td>600</td><td>code invalid</td><td>请求code产品无效</td></tr><tr><td>601</td><td>body empty</td><td>请求消息体数据为空</td></tr><tr><td>603 </td><td>token level not enough </td><td>请求产品个数或者K线根数大于token权限</td></tr><tr><td>604</td><td>code unauthorized</td><td>token没有请求产品的权限</td></tr><tr><td>605</td><td>too many requests</td><td>一般是Http接口请求频率限制</td></tr><tr><td>606</td><td>too many requests and connection will be closed</td><td>一般是Websocket接口请求频率限制</td></tr></tbody></table>

***

#### AllTick网站

{% hint style="info" %}
官方网站：[https://alltick.co/](https://alltick.co/)
{% endhint %}
