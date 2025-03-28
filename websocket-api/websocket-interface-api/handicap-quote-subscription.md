# Order Book (Real-time Tick-by-Tick, Market Depth) Subscription

English / [中文](https://apis.alltick.co/websocket-api/gu-piao-websocket-jie-kou-api/pan-kou-bao-jia-ding-yue)

## Interface Description

This interface supports subscribing to the latest market depth (real-time tick-by-tick, Order Book) data for products, but does not support historical market depth or historical tick data.

**Interface Features:** For each WebSocket connection, sending this request will overwrite the previous subscription by default. For example, if you initially subscribed to products A, B, and C and want to add E, F, and G, you must resend A, B, C, E, F, and G. After successful subscription, data will be pushed.

**Note:**

1、After a successful subscription, avoid frequent requests. Send a heartbeat every 10 seconds; if no heartbeat is received in 30 seconds, the WebSocket will disconnect.

2、Implement automatic reconnection logic to handle network disconnections.

3、Maximum market depth limits for each product:

3.1  Inactive products may have less depth than listed.

3.2 One side of the depth may be empty, such as during limit up or down for stocks.

<table data-full-width="false"><thead><tr><th width="133"></th><th width="122.01171875">FX、Metals</th><th width="142.48828125">Cryptocurrency</th><th width="142.38671875">HK Stocks</th><th width="141.296875">Chinese Stocks</th></tr></thead><tbody><tr><td>Order Book Description</td><td>Maximum 1 gears</td><td>Maximum 5 gears</td><td>Maximum 10 gears</td><td>Maximum 5 gears</td></tr></tbody></table>

## Interface Limitations <a href="#interface-limitations" id="interface-limitations"></a>

1. Please be sure to read:[ \[ Websocket Interface Limitations \].](https://en.apis.alltick.co/integration-process/interface-restriction-description/websocket-interface-limitations)
2. Please be sure to read: [\[ Error Code Descriptions \].](https://en.apis.alltick.co/integration-process/interface-restriction-description/error-code-description)

### API Endpoints <a href="#api-endpoints" id="api-endpoints"></a>

**1、Stock Market Data API for US, HK, A-shares, and Index:**

Base Path: `/quote-stock-b-ws-api`&#x20;

Full URL: `wss://quote.alltick.io/quote-stock-b-ws-api`

**2、API for Forex, Precious Metals, Cryptocurrencies, and Commodities:**

Base Path: `/quote-b-ws-api`&#x20;

Full URL: `wss://quote.alltick.io/quote-b-ws-api`

## Request Examples

**1、Request Example for US, HK, A-shares, and Index Data:**

Each time you establish a connection, you must append your authentication token to the URL as follows:

`wss://quote.alltick.io/quote-stock-b-ws-api?token=your_token`

After a successful connection, you can subscribe to specific stock market data as needed. Please refer to the documentation below for detailed calling methods.

**2、Request Example for Forex, Precious Metals, Cryptocurrencies, and Commodities:**

Each time you establish a connection, you must append your authentication token to the URL as follows:

`wss://quote.alltick.io/quote-b-ws-api?token=your_token`

After a successful connection, you can subscribe to specific forex, cryptocurrency, precious metals, and commodities data as needed. Please refer to the documentation below for detailed calling methods.

## Request - Protocol Number：22002

#### Json definition

<table><thead><tr><th width="115.2265625">Field</th><th width="150.30859375">Name</th><th width="78.6796875">Type</th><th width="98.59375">Required</th><th>Description</th></tr></thead><tbody><tr><td>cmd_id</td><td>protocol number</td><td>integer</td><td>Yes</td><td>The protocol number for the order book data request is fixed: 22002</td></tr><tr><td>seq_id</td><td>response id</td><td>integer</td><td>Yes</td><td>Subscription request identifier, which will be returned in the response. (Customizable and can be repeated for each request)</td></tr><tr><td>trace</td><td>traceable id</td><td>string</td><td>Yes</td><td>Traceable ID for request log information (Customizable, and it should not be repeated for each request)</td></tr><tr><td>symbol_list</td><td>Product List</td><td>array</td><td>Yes</td><td>See the symbol definition below for the specific format.</td></tr></tbody></table>

#### Symbol definition

<table><thead><tr><th width="129.5703125">Field</th><th width="124.73828125">Name</th><th width="84.43359375">Type</th><th width="97.16796875">Required</th><th>Description</th></tr></thead><tbody><tr><td>code</td><td>Code</td><td>string</td><td>Yes</td><td>For specific content, please refer to the code list ：<a href="https://docs.google.com/spreadsheets/d/1avkeR1heZSj6gXIkDeBt8X3nv4EzJetw4yFuKjSDYtA/edit?gid=495387863#gid=495387863">[Click on the code list]</a></td></tr><tr><td>depth_level</td><td>Depth level</td><td>uint32</td><td>No</td><td>If there is no depth_level field, the background will only provide a quote for one layer, and the requested level is greater than the actual quote level, or if there is no depth_level field, the background will provide as many layers as there are actual quotes.</td></tr></tbody></table>

### Data Structure (JSON)

```
{
    "cmd_id":22002,
    "seq_id":123,
    "trace":"3baaa938-f92c-4a74-a228-fd49d5e2f8bc-1678419657806",
    "data":{
        "symbol_list": [
            {
                "code": "BTCUSDT",
                "depth_level": 5
            }
        ]
    }
}
```

## Response-protocol number：22003 <a href="#ying-da-xie-yi-hao-22001" id="ying-da-xie-yi-hao-22001"></a>

### Data Structure (JSON)

```
{
    "ret":200,
    "msg":"ok",
    "cmd_id":22003,
    "seq_id":123,
    "trace":"3baaa938-f92c-4a74-a228-fd49d5e2f8bc-1678419657806",
    "data":{
    }    
}
```

## Push - Protocol Number: 22999

#### Definition of data

<table><thead><tr><th width="130.23828125">Field</th><th width="180.63671875">Name</th><th width="103.8203125">Type</th><th>Description</th></tr></thead><tbody><tr><td>code</td><td>Code</td><td>string</td><td>Specific content, refer to the code list：<a href="https://docs.google.com/spreadsheets/d/1avkeR1heZSj6gXIkDeBt8X3nv4EzJetw4yFuKjSDYtA/edit?gid=495387863#gid=495387863">[Click on the code list]</a></td></tr><tr><td>seq</td><td>Quote Number</td><td>string</td><td></td></tr><tr><td>tick_time</td><td>Quote Timestamp</td><td>string</td><td>In milliseconds</td></tr><tr><td>bids</td><td>Bid Depth</td><td>array</td><td>See below for bids definition</td></tr><tr><td>asks</td><td>Ask Depth</td><td>array</td><td>See below for asks definition</td></tr></tbody></table>

#### bids definition

<table><thead><tr><th width="141.9921875">Field</th><th width="166.859375">Name</th><th width="142.4609375">Type</th><th>Description</th></tr></thead><tbody><tr><td>price</td><td>Bid Price</td><td>string</td><td></td></tr><tr><td>volume</td><td>Bid Volume</td><td>string</td><td><p>1、Forex, precious metals, and CFD indices do not provide volume.</p><p>2、Stocks and cryptocurrency data provide volume.</p></td></tr></tbody></table>

asks definition

<table><thead><tr><th width="147.1796875">Field</th><th width="163.4765625">Name</th><th width="143.359375">Type</th><th>Description</th></tr></thead><tbody><tr><td>price</td><td>Ask Price</td><td>string</td><td></td></tr><tr><td>volume</td><td>Ask Volume</td><td>string</td><td><p>1、Forex, precious metals, and CFD indices do not provide volume.</p><p>2、Stocks and cryptocurrency data provide volume.</p></td></tr></tbody></table>

### Data Structure (JSON)

```
{
    "cmd_id":22999,
    "data":{
	"code": "HK-1288",
        "seq": "1605509068000001",
        "tick_time": "1605509068",
        "bids": [
            {
                "price": "9.12",
                "volume": "9.12"
            }
        ],
        "asks": [
            {
                "price": "147.12",
                "volume": "147.12"
            }
        ]
    }
}
```

### Official Website

{% hint style="info" %}
Official website: [https://alltick.co/](https://alltick.co/)
{% endhint %}
