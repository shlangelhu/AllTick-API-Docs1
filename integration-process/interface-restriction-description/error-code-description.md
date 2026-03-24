---
description: 错误码说明
---

# 错误码说明

[English ](https://en.apis.alltick.co/integration-process/interface-restriction-description/error-code-description)/ 中文

<table><thead><tr><th width="120.97265625">错误码</th><th width="218.69921875">错误内容</th><th>含义</th></tr></thead><tbody><tr><td>200</td><td>ok</td><td>成功</td></tr><tr><td>400</td><td>request header param invalid</td><td><p>请求JSON第一层参数错误</p><p>排查建议：</p><p>1、检查JSON结构是否完整。</p><p>2、确认所有必需字段已正确包含。</p><p>3、验证data字段是否为有效的对象类型。</p><p>4、核实trace等关键字段是否存在。</p></td></tr><tr><td>400</td><td>request data param invalid</td><td><p>请求JSON中data字段参数错误</p><p>排查建议：</p><p>1、检查data字段是否为有效对象。</p><p>2、确认data中所有必需字段已正确填写。</p><p>3、对照具体接口文档，核实data字段内容。</p><p>4、特别注意POST请求中，确保body体中JSON参数完整且正确。</p></td></tr><tr><td>401</td><td>token invalid</td><td><p>token无效</p><p>可能由以下情况导致：</p><p>1、Token格式不正确。</p><p>2、Token账号过期了。</p></td></tr><tr><td>402</td><td>query invalid</td><td><p>请求的query参数错误</p><p>排查建议：</p><p>1、检查GET请求的query参数。</p><p>2、对query参数进行URL编码。</p><p>3、确保参数格式符合接口要求。</p><p>4、验证特殊字符是否正确转义。</p></td></tr><tr><td>429</td><td>Too Many Requests</td><td><p>超过套餐规定的请求频率</p><p>建议：</p><p>1、优化请求频率和逻辑。</p><p>2、考虑升级套餐，获取更高的请求频率。<br><br>点击查看接口限制说明：<br><a href="http-interface-restrictions.md">HTTP接口限制</a><br><a href="websocket-interface-limitations.md">Websocket接口限制</a><br><br><mark style="color:$danger;">常见场景：</mark><br>例如基础套餐：请求 <strong>/kline接口，</strong>1秒发起了至少2次请求，那么返回情况如下：<br>第一个请求成功，第二个请求返回429，Too Many Requests，因为基础套餐<strong>/kline接口：</strong>每1秒，只能1次请求，所以会返回429，Too Many Requests </p></td></tr><tr><td>600</td><td>code invalid</td><td><p>请求code产品无效</p><p>排查建议：</p><p>1、检查请求URL：<br>仔细核对接口文档，股票类和外汇类贵金属类数据的请求URL是不同。<br>2、检查产品code：</p><p>对照产品列表，确保代码有效且准确：<a href="https://docs.google.com/spreadsheets/d/1avkeR1heZSj6gXIkDeBt8X3nv4EzJetw4yFuKjSDYtA/edit?gid=495387863#gid=495387863">[产品列表]</a></p></td></tr><tr><td>601</td><td>body empty</td><td><p>请求消息体数据为空</p><p><br>排查建议：</p><p>1、检查POST请求的消息体。</p><p>2、确保body中包含完整的JSON参数。</p><p>3、特别注意批量获取/batch-kline等接口。</p><p>4、验证所有必需字段均已正确填写。</p></td></tr><tr><td>603 </td><td>token level not enough </td><td><p>请求产品个数或者K线根数超过接口文档规定的限制</p><p><br>排查建议：</p><p>1、检查产品数量：<br>K线接口，确认同时请求的【产品数】加上【K线类型】的总和，是否超过套餐限制。<br>非K线接口，确认请求的产品数，是否超过套餐限制。</p><p>2、验证K线请求：<br>核实K线根数是否符合接口规定。<br>注意批量产品K线接口每次仅允许2根。<br><br>点击查看接口限制说明：<a href="http-interface-restrictions.md">HTTP接口限制</a></p></td></tr><tr><td>604</td><td>code unauthorized</td><td>您的token没有请求该code的权限</td></tr><tr><td>605</td><td>too many requests</td><td><p>请求频率限制</p><p><br>建议：</p><p>1、优化请求频率和逻辑。</p><p>2、考虑升级套餐，获取更高的请求频率。<br><br>点击查看接口限制说明：<br><a href="http-interface-restrictions.md">HTTP接口限制</a><br><a href="websocket-interface-limitations.md">Websocket接口限制</a></p></td></tr><tr><td>606</td><td>too many requests and connection will be closed</td><td><p>一般是Websocket接口请求频率限制</p><p><br>排查建议：</p><p>1、检查Websocket连接数。<br>确认是否超过套餐规定的最大连接数。</p><p>2、控制请求频率<br>确保多个Websocket请求时间隔至少3秒。<br><br>点击查看接口限制说明：<br><a href="websocket-interface-limitations.md">Websocket接口限制</a></p></td></tr></tbody></table>

***

#### AllTick网站

{% hint style="info" %}
官方网站：[https://alltick.co/](https://alltick.co/)
{% endhint %}
