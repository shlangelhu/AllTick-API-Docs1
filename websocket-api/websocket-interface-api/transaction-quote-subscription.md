# Latest Trade Price (Real-time Tick Data) Batch Subscription

English / [中文](https://apis.alltick.co/websocket-api/gu-piao-websocket-jie-kou-api/cheng-jiao-bao-jia-ding-yue)

## Interface Description

This API supports batch subscription to real-time trade prices (tick-by-tick data) but does not provide historical trade prices.

Each WebSocket connection allows one active subscription at a time.\
Sending a new subscription request overwrites the previous one.\
Example: If you initially subscribe to A, B, C and want to add E, F, G, you must resend A, B, C, E, F, G in a single request. Once subscribed, real-time data will be pushed automatically.

**Important Notes：**\
1、Do not repeatedly send subscription requests.\
After a successful subscription, send a heartbeat every 10 seconds.\
If no heartbeat is received for 30 seconds, the server will assume a timeout and disconnect the WebSocket.\
2、Implement automatic reconnection.\
To handle network disconnections, clients should implement an auto-reconnect mechanism.

### Interface Limitations <a href="#interface-limitations" id="interface-limitations"></a>

1. Please be sure to read:[ \[ Websocket Interface Limitations \].](../../integration-process/interface-restriction-description/websocket-interface-limitations.md)
2. Please be sure to read: [\[ Error Code Descriptions \].](https://en.apis.alltick.co/integration-process/interface-restriction-description/error-code-description)

## API Endpoints

**1、Stock Market Data API for US, HK, A-shares, and Index:**

Base Path: `/quote-stock-b-ws-api`\
Full URL: `wss://quote.alltick.io/quote-stock-b-ws-api`&#x20;

**2、API for Forex, Precious Metals, Cryptocurrencies, and Commodities:**

Base Path: `/quote-b-ws-api`\
Full URL: `wss://quote.alltick.io/quote-b-ws-api`

## Request Examples <a href="#request-examples" id="request-examples"></a>

**1、Request Example for US, HK, A-shares, and Index Data:**

Each time you establish a connection, you must append your authentication token to the URL as follows:

`wss://quote.alltick.io/quote-stock-b-ws-api?token=your_token`

After a successful connection, you can subscribe to specific stock market data as needed. Please refer to the documentation below for detailed calling methods.

**2、Request Example for Forex, Precious Metals, Cryptocurrencies, and Commodities:**

Each time you establish a connection, you must append your authentication token to the URL as follows:

`wss://quote.alltick.io/quote-b-ws-api?token=your_token`

After a successful connection, you can subscribe to specific forex, cryptocurrency, precious metals, and commodities data as needed. Please refer to the documentation below for detailed calling methods.

## Request - Protocol Number：22004

Json definition

<table><thead><tr><th width="119.00390625">Field</th><th width="147.81640625">Name</th><th width="88.484375">Type</th><th width="106.0546875">Required</th><th>Description</th></tr></thead><tbody><tr><td>cmd_id</td><td>protocol number</td><td>integer</td><td>Yes</td><td>The protocol number for the latest trade price data request is fixed: 22004</td></tr><tr><td>seq_id</td><td>response id</td><td>integer</td><td>Yes</td><td>Subscription request identifier, which will be returned in the response. (Customizable and can be repeated for each request)</td></tr><tr><td>trace</td><td>traceable id</td><td>string</td><td>Yes</td><td>Traceable ID for request log information (Customizable, and it should not be repeated for each request)</td></tr><tr><td>symbol_list</td><td>Symbol List</td><td>array</td><td>Yes</td><td>See the symbol definition below for the specific format.</td></tr></tbody></table>

symbol definition

<table><thead><tr><th width="85.5859375">Field</th><th width="85.5234375">Name</th><th width="96.38671875">Type</th><th width="126.8984375">Required</th><th>Description</th></tr></thead><tbody><tr><td>code</td><td>Code</td><td>string</td><td>Yes</td><td>For specific content, please refer to the code list：<a href="https://docs.google.com/spreadsheets/d/1avkeR1heZSj6gXIkDeBt8X3nv4EzJetw4yFuKjSDYtA/edit?gid=495387863#gid=495387863">[Click on the code list]</a></td></tr></tbody></table>

### Data Structure (JSON))

```
{
    "cmd_id":22004,
    "seq_id":123,
    "trace":"3baaa938-f92c-4a74-a228-fd49d5e2f8bc-1678419657806",
    "data":{
        "symbol_list": [
            {
                "code": "BTCUSDT"
            }
        ]
    }
}
```

## Response-protocol number：22005 <a href="#ying-da-xie-yi-hao-22001" id="ying-da-xie-yi-hao-22001"></a>

### Data Structure (JSON)

```
{
    "ret":200,
    "msg":"ok",
    "cmd_id":22005,
    "seq_id":123,
    "trace":"3baaa938-f92c-4a74-a228-fd49d5e2f8bc-1678419657806",
    "data":{
    }    
}
```

## Push - Protocol Number: 22998

#### Definition of data

<table><thead><tr><th width="137.61328125">Field</th><th width="176.65625">Name</th><th width="73.16796875">Type</th><th>Description</th></tr></thead><tbody><tr><td>code</td><td>Code</td><td>string</td><td>Specific content, refer to the code list：<a href="https://docs.google.com/spreadsheets/d/1avkeR1heZSj6gXIkDeBt8X3nv4EzJetw4yFuKjSDYtA/edit?gid=495387863#gid=495387863">[Click on the code list]</a></td></tr><tr><td>seq</td><td>Quote Number</td><td>string</td><td></td></tr><tr><td>tick_time</td><td>Quote Timestamp</td><td>string</td><td>In milliseconds</td></tr><tr><td>price</td><td>Transaction Price</td><td>string</td><td></td></tr><tr><td>volumn</td><td>Transaction Volume</td><td>string</td><td></td></tr><tr><td>turnover</td><td>Transaction Turnover</td><td>string</td><td><p>Turnover:</p><ol><li>For forex, precious metals, and energy, turnover is not provided. You can calculate it using the formula: <code>turnover = price * volume</code>.</li><li>For stocks and cryptocurrencies, turnover is returned normally.</li></ol></td></tr><tr><td>trade_direction</td><td>Transaction Direction</td><td>string</td><td><p>Trade Direction:</p><ol><li>0 is the default value, 1 is Buy, and 2 is Sell.</li><li>For forex, precious metals, and energy, the default return is only 0.</li><li>For stocks and cryptocurrencies, it can return 0, 1, or 2 based on market conditions.</li><li><p>Detailed Explanation:</p><ul><li>0: Neutral, indicating a trade executed at a price between the best bid and best ask.</li><li>1: Aggressive Buy, indicating a trade executed at the ask price or higher.</li><li>2: Aggressive Sell, indicating a trade executed at the bid price or lower.</li></ul></li></ol></td></tr></tbody></table>

### Data Structure (JSON)

```
{
    "cmd_id":22998,
    "data":{
	"code": "1288.HK",
        "seq": "1605509068000001",
        "tick_time": "1605509068",
        "price": "651.12",
        "volume": "300",
        "turnover": "12345.6",
        "trade_direction": 1
    }
}
```

### Official Website

{% hint style="info" %}
Official website: [https://alltick.co/](https://alltick.co/)
{% endhint %}
