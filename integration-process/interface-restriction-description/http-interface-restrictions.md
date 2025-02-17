# HTTP interface restrictions

English / [中文](https://apis.alltick.co/jie-ru-liu-cheng/jie-kou-xian-zhi-shuo-ming/http-jie-kou-xian-zhi)

## HTTP Interface Restrictions (Free Trial Version)

**IP Restrictions**

* The number of requests from each IP address is subject to specific limitations based on the interface.
  * **/kline interface**: Can only be requested once every 10 seconds.
  * **/depth-tick interface**: Can only be requested once per second.
  * **/trade-tick interface**: Can only be requested once per second.
  * **/batch-kline接口**：Can only be requested once every 10 seconds.
* **Example**: If IP address A requests the /kline interface once at 14:03:01 and calls the /trade-tick interface once within the same minute, backend services will be provided normally. If IP address A makes two requests to the /kline interface within 14:03:01, the first request will be served normally, while the second request will receive an error response.

**2. Connection Limit**

* To reduce the load on backend services, the maximum number of simultaneous connections is limited to 100. This limit may be adjusted based on the actual performance of the service. Requests exceeding this limit will be directly disconnected.

**3. K-Line Query Restrictions**

* Each query request can only target one stock code (code) for K-line data.
* Each query can return a maximum of 1000 K-line data points. If a request queries for more than 1000 K-lines, the system will query and return results for only 1000 data points.

**4. Quote Query Restrictions**

* Each query can include a maximum of 5 stock codes (codes).
* If a query request includes more than 5 stock codes, the system will only query and return results for the first 5 codes.

#### Notes

* Please plan your request strategy according to the above restrictions to avoid unnecessary service interruptions.
* These restrictions are in place to ensure all users can fairly enjoy the service while protecting the backend system from excessive load.
* If you have questions or need further assistance, please contact customer support.

***

### Official Website

{% hint style="info" %}
Official website: [https://alltick.co/](https://alltick.co/)
{% endhint %}
