# Websocket Feed
​
Websocket api can be used for the following use cases
​
- Get real time feed of market data, this includes L2 orderbook and recent trades.
- Get price feeds - Mark prices of different contracts, price feed of underlying indexes etc.
- Get account specific notifications like fills, liquidations, [ADL](https://guides.faida.trade/) and PnL updates.
- Get account specific updates on orders, positions and wallets.
​
Access url for [Faida Trade](https://www.faida.trade)
​
<ul>
<li><strong>Production private channel endpoint</strong> - wss://socket.faida.trade</li>
<li><strong>Production public channel endpoint</strong> - wss://public-socket.faida.trade</li>
<br>
<li><strong>Testnet(Demo Account) private channel endpoint</strong> - wss://testnet-socket.faida.trade</li>
<li><strong>Testnet(Demo Account) public channel endpoint</strong> - wss://testnet-socket-pub.faida.trade</li>
</ul>
​
There is a limit of 150 connections every 5 minutes per IP address. A connection attempt that goes beyond the limit will be disconnected with 429 HTTP status error. On receiving this error, wait for 5 to 10 minutes before making new connection requests.
​
You will be disconnected, if there is no activity within 60 seconds after making connection.
​
# Subscribing to Channels
​
## Subscribe
​
To begin receiving feed messages, you must first send a subscribe message to the server indicating which channels and contracts to subscribe for.
​
To specify contracts within each channel, just pass a list of symbols inside the channel payload. Mention ***["all"]*** in symbols if you want to receive updates across all the contracts. Please note that snapshots are sent only for specified symbols,meaning no snapshots are sent for symbol: ***"all"***.
​
Once a subscribe message is received the server will respond with a subscriptions message that lists all channels you are subscribed to. Subsequent subscribe messages will add to the list of subscriptions. 
​
> Subscription Sample
​
```json
// Request
// Subscribe to BTCUSD_28Dec and ETHBTC_28Dec with the ticker and orderbookL2 channels,
{
    "type": "subscribe",
    "payload": {
        "channels": [
            {
                "name": "v2/ticker",
                "symbols": [
                    "BTCUSDT",
                    "ETHUSDT"
                ]
            },
            {
                "name": "l2_orderbook",
                "symbols": [
                    "BTCUSDT"
                ]
            },
            {
                "name": "funding_rate",
                "symbols": [
                    "all"
                ]
            }
        ]
    }
}
​
// Response
{
    "type": "subscriptions",
    "channels": [
        {
            "name": "l2_orderbook",
            "symbols": [
                "BTCUSDT"
            ],
        },
        {
            "name": "v2/ticker",
            "symbols": [
                "BTCUSDT",
                "ETHUSDT"
            ]
        },
        {
            "name": "funding_rate",
            "symbols": [
                "all"
            ]
        }
    ]
}
​
// Error Response 
{
    "type": "subscriptions",
    "channels": [
        {
            "name": "l2_orderbook",
            "symbols": [
                "BTCUSDT"
            ],
        },
        {
            "name": "trading_notifications",
            "error": "subscription forbidden on trading_notifications. Unauthorized user"
        }
    ]
}
```
​
​
## Unsubscribe
​
If you want to unsubscribe from channel/contracts pairs, send an "unsubscribe" message. The structure is equivalent to subscribe messages. If you want to unsubscribe for specific symbols in a channel, you can pass it in the symbol list. As a shorthand you can also provide no symbols for a channel, which will unsubscribe you from the channel entirely.
​
> Unsubscribe Sample
​
```json
// Request
{
    "type": "unsubscribe",
    "payload": {
        "channels": [
            {
                "name": "v2/ticker",          // unsubscribe from ticker channel only for BTCUSD_28Dec
                "symbols": [
                    "BTCUSDT"
                ]
            },
            {
                "name": "l2_orderbook"      // unsubscribe from all symbols for l2_orderbook channel
            }
        ]
    }
}
```
​
# Authenticating
​
## Current method
​
Authentication allows clients to subscribe to user account related trading notifications using private channels like positions, orders, etc. This allows users to get real-time updates related to their orders, fills, liquidations, [adl](/#trading-notitifications) and pnl updates.
​
```python
# auth message with signed request
import websocket
import hashlib
import hmac
import time
​
api_key = 'a207900b7693435a8fa9230a38195d'
api_secret = '7b6f39dcf660ec1c7c664f612c60410a2bd0c258416b498bf0311f94228f'
​
def generate_signature(secret, message):
    message = bytes(message, 'utf-8')
    secret = bytes(secret, 'utf-8')
    hash = hmac.new(secret, message, hashlib.sha256)
    return hash.hexdigest()
​
# Get open orders
method = 'GET'
timestamp = str(int(time.time()))
path = '/live'
signature_data = method + timestamp + path
signature = generate_signature(api_secret, signature_data)
​
ws = websocket.WebSocketApp('wss://socket.faida.trade')
​
ws.send(json.dumps({
    "type": "key-auth",
    "payload": {
        "api-key": api_key,
        "signature": signature,
        "timestamp": timestamp
    }
}))
​
ws.send(json.dumps({
    "type": 'unauth',
    "payload": {}
}))
```
​
**Note**: For users migrating from older authentication method, the change is: "type" in request payload must be changed from "auth" to "key-auth". Rest of the request payload will remain the same. The response payloads have major changes. Check below for the response payloads.  
​
​
To authenticate, you must send a request of type **'key-auth'** on your socket connection. Authentication request is a json of the format:  
`{"type":"key-auth","payload":{"api-key":"#KEY#","timestamp":#TIMESTAMP#,"signature":"#SIGNATURE#"}}`  
**KEY** here is your API-key string.  
**TIMESTAMP** is current epoch Unix timestamp in seconds as a number.  
**SIGNATURE** is hash string of HMAC created using `'GET' + string(TIMESTAMP) + '/live'` and your API-secret.  
Note: Same timestamp must be used for TIMESTAMP and in generating SIGNATURE. 
​
Refer to the right side for a sample code.
​
<br><br><br>
​
**Authentication Responses**  
All authentication responses will be json containing following keys:  
**"type"** will always be "key-auth"  
**"success"** is a boolean indicating whether the authentication was a success or failure.  
**"status_code"** is number just like HTTP response status.  
**"status"** is a string describing the response status.  
**"message"** is a string which may be present describing authentication failure reason.
​
​
Success response:  
`{"type":"key-auth", "success":true, "status_code":200, "status":"authenticated"}`
​
​
Error responses:  
​
1. Lacking 'api-key' or 'sign' or 'timestamp' in the payload:  
`{"type":"key-auth", "success":false, "status_code":400, "status":"incomplete_payload", "message":"Incomplete payload"}`  
​
2. Request received after 5 secs:   
`{"type":"key-auth", "success":false, "status_code":408, "status":"request_expired", "message":"Timestamp header outside of allowed time window"}}`  
​
3. ApiKey does not exist:  
`{"type":"key-auth", "success":false, "status_code":404, "status":"api_key_not_found", "message":"ApiKey not found"}}`  
​
4. Invalid/wrong Signature:  
`{"type":"key-auth", "success":false, "status_code":401, "status":"invalid_signature", "message":"Invalid Signature"}`  
​
5. IP address not whitelisted for the API-key:  
`{"type":"key-auth", "success":false, "status_code":401, "status":"ip_not_whitelisted", "message":"IP address not whitelisted. Your IP: 172.16.19.91"}`  
​
6. Some internal server error:  
`{"type":"key-auth", "success":false, "status_code":500, "status":"internal_server_error", "message": "Internal Server Error. Code: 1001"`
​
# Sample Python Code
​
## Public Channels
​
**Summary:** 
The python script(right panel) connects to the Faida Trade WebSocket to receive real-time market data.
​
- It opens a connection.
- Subscribes to `v2/ticker`(tickers data) and `candlestick_1m`(1 minute ohlc candlesticks) channels. (**MARK:BTCUSDT** - mark price ohlc in candlesticks channel)
- When data arrives, it processes and prints it.
- If an error occurs, it prints an error message.
- If the connection closes, it notifies the user.
- The connection remains open indefinitely to keep receiving updates.
​
```python
import websocket
import json
​
# production websocket base url
WEBSOCKET_URL = "wss://socket.faida.trade"
​
def on_error(ws, error):
    print(f"Socket Error: {error}")
​
def on_close(ws, close_status_code, close_msg):
    print(f"Socket closed with status: {close_status_code} and message: {close_msg}")
​
def on_open(ws):
  print(f"Socket opened")
  # subscribe tickers of perpetual futures - BTCUSD & ETHUSD, call option C-BTC-95200-200225 and put option - P-BTC-95200-200225
  subscribe(ws, "v2/ticker", ["BTCUSDT", "ETHUSDT", "C-BTC-95200-200225", "P-BTC-95200-200225"])
  # subscribe 1 minute ohlc candlestick of perpetual futures - MARK:BTCUSD(mark price) & ETHUSD(ltp), call option C-BTC-95200-200225(ltp) and put option - P-BTC-95200-200225(ltp).
  subscribe(ws, "candlestick_1m", ["MARK:BTCUSDT", "ETHUSDT", "C-BTC-95200-200225", "P-BTC-95200-200225"])
​
def subscribe(ws, channel, symbols):
    payload = {
        "type": "subscribe",
        "payload": {
            "channels": [
                {
                    "name": channel,
                    "symbols": symbols
                }
            ]
        }
    }
    ws.send(json.dumps(payload))
​
def on_message(ws, message):
    # print json response
    message_json = json.loads(message)
    print(message_json)
​
if __name__ == "__main__":
  ws = websocket.WebSocketApp(WEBSOCKET_URL, on_message=on_message, on_error=on_error, on_close=on_close)
  ws.on_open = on_open
  ws.run_forever() # runs indefinitely
```
​
## Private Channels
​
**Summary:** 
The python script(right panel) connects to the Faida Trade WebSocket to receive real-time market data.
​
- It opens a connection.
- Sends authentication payload over socket with api_key, signature & timestamp.
- When authentication update arrives, it checks for success and then sends subscription for `orders` and `positions` channels for all contracts.
- Prints all other updates in json format.
- If an error occurs, it prints an error message.
- If the connection closes, it notifies the user.
- The connection remains open indefinitel...
