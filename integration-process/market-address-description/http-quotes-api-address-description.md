---
description: >-
  API地址说明 股票HTTP接口API地址 /quote-stock-b-api 股票查询API 查询API为https协议，完整的url为：
  https://quote.alltick.io/quote-stock-b-api 每发送一次查询请求时，需要带上方法名和token信息\
  单产品请求K线示例：
---

# HTTP 行情 API 地址说明

[English ](https://en.apis.alltick.co/integration-process/market-address-description/http-quotes-api-address-description)/ 中文

## API地址说明

### 股票HTTP接口API地址

/quote-stock-b-api 股票查询API

查询API为https协议，完整的url为：\
[https://quote.alltick.io/quote-stock-b-api](https://quote.alltick.co/quote-stock-b-api)

每发送一次查询请求时，需要带上方法名和token信息\\

单产品请求K线示例：\
[https://quote.alltick.io/quote-stock-b-api/kline?token=你的token\&query=queryData](https://quote.alltick.io/quote-stock-b-api/kline?token=%E4%BD%A0%E7%9A%84token\&query=queryData)\\

批产品请求K线示例：\
[https://quote.alltick.io/quote-stock-b-api/batch-kline?token=你的token](https://quote.alltick.io/quote-stock-b-api/batch-kline?token=%E4%BD%A0%E7%9A%84token)\
注意：批产品请求K线时，请求参数放在body中

请求最新成交价示例：\
[https://quote.alltick.io/quote-stock-b-api/trade-tick?token=你的token\&query=queryData](https://quote.alltick.io/quote-stock-b-api/trade-tick?token=%E4%BD%A0%E7%9A%84token\&query=queryData)\\

请求最新盘口示例：\
[https://quote.alltick.io/quote-stock-b-api/depth-tick?token=你的token\&query=queryData](https://quote.alltick.io/quote-stock-b-api/depth-tick?token=%E4%BD%A0%E7%9A%84token\&query=queryData)\\

具体调用方式，请查看http接口列表

### 外汇,加密货币(数字币),商品(贵金属) HTTP接口API地址

/quote-b-api 外汇,加密货币(数字币),商品(贵金属)查询API\\

查询API为https协议，完整的url为：\
[https://quote.alltick.io/quote-b-api](https://quote.alltick.io/quote-b-api)\\

每发送一次查询请求时，需要带上方法名和token信息\\

单产品请求K线示例：\
[https://quote.alltick.io/quote-b-api/kline?token=你的token\&query=queryData](https://quote.alltick.io/quote-b-api/kline?token=%E4%BD%A0%E7%9A%84token\&query=queryData)\\

批产品请求K线示例：\
[https://quote.alltick.io/quote-b-api/batch-kline?token=你的token](https://quote.alltick.io/quote-b-api/batch-kline?token=%E4%BD%A0%E7%9A%84token)\
注意：批产品请求K线时，请求参数放在body中

请求最新成交价示例：\
[https://quote.alltick.io/quote-b-api/trade-tick?token=你的token\&query=queryData](https://quote.alltick.io/quote-b-api/trade-tick?token=%E4%BD%A0%E7%9A%84token\&query=queryData)\\

请求最新盘口示例：\
[https://quote.alltick.io/quote-b-api/depth-tick?token=你的token\&query=queryData](https://quote.alltick.io/quote-b-api/depth-tick?token=%E4%BD%A0%E7%9A%84token\&query=queryData)\\

具体调用方式，请查看http接口列表

***

#### 官方网站

{% hint style="info" %}
官方网站：[https://alltick.co/](https://alltick.co/)
{% endhint %}
