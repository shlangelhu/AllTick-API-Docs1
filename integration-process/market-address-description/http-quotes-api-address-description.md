# HTTP Quotes API Address Description

English / [中文](https://apis.alltick.co/jie-ru-liu-cheng/hang-qing-di-zhi-shuo-ming/http-hang-qing-api-di-zhi-shuo-ming)

## API Address Description



### Stock HTTP Interface API Address



/quote-stock-b-api Stock Query API\


The query API uses HTTPS protocol, the complete URL is:\
[https://quote.tradeswitcher.com/quote-stock-b-api](https://quote.tradeswitcher.com/quote-stock-b-api)\


Each time a query request is sent, the method name and token information need to be provided\


Single product request K-line example:\
[https://quote.tradeswitcher.com/quote-stock-b-api/kline?token=yourToken\&query=queryData](https://quote.tradeswitcher.com/quote-stock-b-api/kline?token=yourToken\&query=queryData)\


Batch product request K-line example:\
[https://quote.tradeswitcher.com/quote-stock-b-api/batch-kline?token=yourToken](https://quote.tradeswitcher.com/quote-stock-b-api/batch-kline?token=yourToken)\
Note: When making batch product requests for K-line, the request parameters should be placed in the body.\


Request for latest transaction price example:\
[https://quote.tradeswitcher.com/quote-stock-b-api/trade-tick?token=yourToken\&query=queryData](https://quote.tradeswitcher.com/quote-stock-b-api/trade-tick?token=yourToken\&query=queryData)\


Request for latest market depth example:\
[https://quote.tradeswitcher.com/quote-stock-b-api/depth-tick?token=yourToken\&query=queryData](https://quote.tradeswitcher.com/quote-stock-b-api/depth-tick?token=yourToken\&query=queryData)\


For specific calling methods, please refer to the HTTP interface list\


### Forex, Cryptocurrency (Digital Currency), Commodity (Precious Metal) HTTP Interface API Address



/quote-b-api Forex, Cryptocurrency (Digital Currency), Commodity (Precious Metal) Query API\


The query API uses HTTPS protocol, the complete URL is:\
[https://quote.tradeswitcher.com/quote-b-api](https://quote.tradeswitcher.com/quote-b-api)\


Each time a query request is sent, the method name and token information need to be provided\


Single product request K-line example: [https://quote.tradeswitcher.com/quote-b-api/kline?token=yourToken\&query=queryData](https://quote.tradeswitcher.com/quote-b-api/kline?token=yourToken\&query=queryData)

Batch product request K-line example: [https://quote.tradeswitcher.com/quote-b-api/batch-kline?token=yourToken](https://quote.tradeswitcher.com/quote-b-api/batch-kline?token=yourToken) Note: When making batch product requests for K-line, the request parameters should be placed in the body.\


Request for latest transaction price example: [https://quote.tradeswitcher.com/quote-b-api/trade-tick?token=yourToken\&query=queryData](https://quote.tradeswitcher.com/quote-b-api/trade-tick?token=yourToken\&query=queryData)

Request for latest market depth example: [https://quote.tradeswitcher.com/quote-b-api/depth-tick?token=yourToken\&query=queryData](https://quote.tradeswitcher.com/quote-b-api/depth-tick?token=yourToken\&query=queryData)

For specific calling methods, please refer to the HTTP interface list

**Interface Address**

* **Base Path**: /quote-stock-b-api
* **Complete URL**: [https://quote.tradeswitcher.com/quote-stock-b-api](https://quote.tradeswitcher.com/quote-stock-b-api)

**Request Example**

When sending a query request, it must include the method name and token information. An example of a request is as follows:

```arduino
https://quote.tradeswitcher.com/quote-stock-b-api/kline?token=yourToken&query=queryData
```

**Usage Instructions**

Through this interface, you can query various types of stock market data. For detailed calling methods, please refer to our HTTP interface list.

***

## Forex, Cryptocurrency, and Commodities Market Data Query

**Interface Address**

* **Base Path**: /quote-b-api
* **Complete URL**: [https://quote.tradeswitcher.com/quote-b-api](https://quote.tradeswitcher.com/quote-b-api)

**Request Example**

Each query must also include the method name and token information. The request format is as follows:

```arduino
https://quote.tradeswitcher.com/quote-b-api/kline?token=yourToken&query=queryData
```

**Usage Instructions**

This interface allows you to query market data for forex, cryptocurrencies (digital currencies), and commodities (precious metals). For the specific method of call, see our HTTP interface documentation list.

***

**Note:** For the security of your account, please ensure your token information is kept safe. If you need further assistance or have any questions, feel free to contact our technical support team at any time.



***

### Official Website

{% hint style="info" %}
Official website: [https://alltick.co/](https://alltick.co/)
{% endhint %}
