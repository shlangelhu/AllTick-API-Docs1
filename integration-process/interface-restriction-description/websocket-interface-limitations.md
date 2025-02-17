# Websocket interface limitations

English / [中文](https://apis.alltick.co/jie-ru-liu-cheng/jie-kou-xian-zhi-shuo-ming/websocket-jie-kou-xian-zhi)

## WebSocket Interface Restrictions (Free Trial Version)

**1. IP Restrictions**

* For users utilizing the same token and IP address, the system only allows one WebSocket connection.
* This means that if you attempt to establish a connection again with the same credentials, the new connection attempt will be rejected.

**2. Connection Limit**

* To protect backend services from excessive requests, the maximum number of simultaneous connections for the stock-ws-api is limited to 100.
* If the number of attempted connections exceeds this limit, the excess connection attempts will be directly disconnected.
* This limit may be adjusted in the future based on the service's performance.

**3. Interface Call Frequency Limit**

* Within a single WebSocket connection, the interval between requests must be at least 1 second.
* For example, if User A sends a request through WebSocket at 28 minutes and 30 seconds and attempts to send another request within the same second, then the second request will be rejected by the system.

**4. Quote Subscription Limit**

* Via a single WebSocket connection, a user can subscribe to quote information for a maximum of 5 stock codes (codes) at a time.
* If an attempt is made to subscribe to more than 5 codes, the system will only process the subscription requests for the first 5 codes and ignore the rest.

#### Notes

* Please plan your WebSocket connections and request strategies according to these restrictions to avoid unnecessary service interruptions.
* These restrictions are designed to ensure that all users can access the service fairly and efficiently, while also protecting the backend service from undue load.
* If you encounter any issues or need further assistance, please contact the technical support team in a timely manner.



***

### Official Website

{% hint style="info" %}
Official website: [https://alltick.co/](https://alltick.co/)
{% endhint %}
