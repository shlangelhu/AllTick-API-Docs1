# Websocket interface limitations

English / [中文](https://apis.alltick.co/jie-ru-liu-cheng/jie-kou-xian-zhi-shuo-ming/websocket-jie-kou-xian-zhi)

## Websocket interface limitations

### **1.** IP Limits

* WebSocket connection limits are based on the allowed connections per Token, not on IP address restrictions. For example, in the Basic plan, one Token allows only one WebSocket connection. If an IP address (A) has already initiated a WebSocket connection, attempting a second connection from the same IP address (A) will be rejected. Similarly, attempting a second connection from a different IP address (B) will also be rejected because the Basic plan permits only one WebSocket connection.
* In the Advanced plan, one Token allows up to three WebSocket connections. You can have three WebSocket connections simultaneously from IP address (A), or one each from IP address (A), IP address (B), and IP address (C), as long as the total connections do not exceed three.
* For "Stock Market Data" and "Forex, Precious Metals, and Crude Oil Data," the request URLs are different. Both types of data count as one WebSocket connection. For instance, in the Basic plan with one Token allowing only one WebSocket connection, if IP address (A) has initiated a WebSocket connection for stock data, you can still initiate a WebSocket connection for Forex, Precious Metals, or Crude Oil data using IP address (A) or IP address (B).

### **2.** API Call Rate Limits

* **Latest Trade Price (Tick by Tick) API**：1 request per second
* **Order Book API:** 1 request per second\
  When making multiple API requests within the same WebSocket connection, the interval between requests must be at least 1 second. For example, if User A sends a request via WebSocket at 28 minutes and 30 seconds and tries to send another request within the same second, the second request will be rejected by the system.
* When initiating multiple WebSocket requests across different WebSocket connections, users should ensure a 2-second interval between each WebSocket request. For instance, if User A has purchased the Advanced plan, which supports connecting to 3 WebSockets simultaneously, and initiates the first WebSocket at 28 minutes and 30 seconds, they should wait for 2 seconds before subscribing to the second WebSocket at 28 minutes and 33 seconds. Once both WebSocket subscriptions are successful, maintain a 10-second interval for sending heartbeats to receive real-time data push from the API.

### **3.** Connection Limits

* Different plans have varying connection limits as shown in the chart. If the attempted number of connections exceeds the specified limit, any excess connection attempts will be immediately disconnected.

| Plan          | WebSocket connections                                |
| ------------- | ---------------------------------------------------- |
| Free          | Only one WebSocket connection can be established.    |
| Basic         | Only one WebSocket connection can be established.    |
| Premium       | Only three WebSocket connections can be established. |
| Professional  | Only ten WebSocket connections can be established.   |
| All HK Stocks | Only ten WebSocket connections can be established.   |
| All CN Stocks | Only ten WebSocket connections can be established.   |

### **4.** Product Code Subscription Limits

* There is a limit to the maximum number of product codes that a user can subscribe to at once through a single WebSocket connection, as detailed in the chart below.
* If attempting to subscribe to more than the specified subscription limit, the system will only process data from the limited number of initial requests and ignore any additional data.

<table><thead><tr><th width="263">Plan</th><th>Code Subscription Limit</th></tr></thead><tbody><tr><td>Free</td><td><strong>Latest Transaction Price (Tick-by-Tick) Interface:</strong> Maximum of 5 products can be requested Simultaneously. <br><strong>Order Book Interface:</strong> Maximum of 5 products can be requested simultaneously.</td></tr><tr><td>Basic</td><td><strong>Latest Transaction Price (Tick-by-Tick) Interface:</strong> Maximum of 100 products can be requested Simultaneously. <br><strong>Order Book Interface:</strong> Maximum of 100 products can be requested simultaneously.</td></tr><tr><td>Premium</td><td><strong>Latest Transaction Price (Tick-by-Tick) Interface:</strong> Maximum of 200 products can be requested Simultaneously. <br><strong>Order Book Interface:</strong> Maximum of 200 products can be requested simultaneously.</td></tr><tr><td>Professional</td><td><strong>Latest Transaction Price (Tick-by-Tick) Interface:</strong> Maximum of 3000 products can be requested Simultaneously. <br><strong>Order Book Interface:</strong> Maximum of 3000 products can be requested simultaneously.</td></tr><tr><td>All HK Stocks</td><td><strong>Latest Transaction Price (Tick-by-Tick) Interface:</strong> Maximum of 3000 products can be requested Simultaneously. <br><strong>Order Book Interface:</strong> Maximum of 3000 products can be requested simultaneously.</td></tr><tr><td>All CN Stocks</td><td><strong>Latest Transaction Price (Tick-by-Tick) Interface:</strong> Maximum of 3000 products can be requested Simultaneously. <br><strong>Order Book Interface:</strong> Maximum of 3000 products can be requested simultaneously.</td></tr></tbody></table>

#### Notice

* Please plan your WebSocket connections and request strategies accordingly based on these limitations to avoid unnecessary service interruptions.
* These limitations are designed to ensure fair and efficient access to services for all users while protecting backend services from undue loads.
* If you encounter any issues or need further assistance, please contact the technical support team promptly.



***

### Official Website

{% hint style="info" %}
Official website: [https://alltick.co/](https://alltick.co/)
{% endhint %}
