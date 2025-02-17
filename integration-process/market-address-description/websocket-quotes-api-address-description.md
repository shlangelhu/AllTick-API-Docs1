# Websocket Quotes API Address Description

English / [中文](https://apis.alltick.co/jie-ru-liu-cheng/hang-qing-di-zhi-shuo-ming/websocket-hang-qing-api-di-zhi-shuo-ming)

## Stock Market Data WebSocket Subscription

**Interface Address**

* **Base Path**: /quote-stock-b-ws-api
* **Complete URL**: wss://quote.tradeswitcher.com/quote-stock-b-ws-api

**Authentication Information**

Each time a connection is established, you must append your authentication token to the URL as shown below:

```arduino
wss://quote.tradeswitcher.com/quote-stock-b-ws-api?token=yourToken
```

**Subscription Instructions**

Once the connection is successful, you can subscribe to specific stock market data as needed. For detailed calling methods, please refer to our WebSocket interface list.

***

## Forex, Cryptocurrency, and Commodities Market Data WebSocket Subscription

**Interface Address**

* **Base Path**: /quote-b-ws-api
* **Complete URL**: wss://quote.tradeswitcher.com/quote-b-ws-api

**Authentication Information**

When establishing a connection, you also need to append your authentication token to the URL to ensure the security of data transmission. The correct format should be as follows:

```arduino
wss://quote.tradeswitcher.com/quote-b-ws-api?token=yourToken
```

**Subscription Instructions**

Once the connection is established, you can subscribe to market data for forex, cryptocurrencies (digital currencies), and commodities (precious metals) according to your needs. For the specific method of call, please check our WebSocket interface list.

***

**Note:** For the security of your account, please ensure your token information is kept safe. If you need further assistance or have any questions, feel free to contact our technical support team at any time.



***

### Official Website

{% hint style="info" %}
Official website: [https://alltick.co/](https://alltick.co/)
{% endhint %}
