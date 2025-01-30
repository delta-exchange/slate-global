<h1 id="ApiSection" class="section-header">API V1 (Deprecated)</h1>
The REST API has endpoints for account and order management as well as public market data.

REST API Endpoint URL for Delta Exchange India

 - **Production-India** - https://api.delta.exchange/v2
 - **Testnet-India** - https://cdn-ind.testnet.deltaex.org/v2

REST API Endpoint URL for Delta Exchange Global

- **Production-Global** - https://api.delta.exchange/v2
- **Testnet-Global** - https://testnet-api.delta.exchange/v2



<h1 id="delta-exchange-api-default">Default</h1>

## deprecated__orders_bracket

> Code samples

```python
import requests

r = requests.deprecated('https://api.delta.exchange/orders/bracket', params={

)

print r.json()

```

```shell
# You can also use wget
curl -X DEPRECATED https://api.delta.exchange/orders/bracket

```

```ruby
require 'rest-client'
require 'json'

result = RestClient.deprecated 'https://api.delta.exchange/orders/bracket',
  params: {
  }

p JSON.parse(result)

```

`DEPRECATED /orders/bracket`

<h3 id="deprecated__orders_bracket-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|

<aside class="success">
This operation does not require authentication.
</aside>

<h1 id="delta-exchange-api-assets">Assets</h1>

Get Asset List

## Get list of all assets

<a id="opIddelta-exchange-api-getAssets"></a>

> Code samples

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.delta.exchange/assets', params={

}, headers = headers)

print r.json()

```

```shell
# You can also use wget
curl -X GET https://api.delta.exchange/assets \
  -H 'Accept: application/json'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.delta.exchange/assets',
  params: {
  }, headers: headers

p JSON.parse(result)

```

`GET /assets`

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "symbol": "string",
    "precision": 0
  }
]
```

<h3 id="get-list-of-all-assets-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|List of all assets|[ArrayOfAssets](#schemaarrayofassets)|

<aside class="success">
This operation does not require authentication.
</aside>

<h1 id="delta-exchange-api-products">Products</h1>

Get Product List, 24hr Ticker

## Get live products

<a id="opIddelta-exchange-api-getProducts"></a>

> Code samples

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.delta.exchange/products', params={

}, headers = headers)

print r.json()

```

```shell
# You can also use wget
curl -X GET https://api.delta.exchange/products \
  -H 'Accept: application/json'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.delta.exchange/products',
  params: {
  }, headers: headers

p JSON.parse(result)

```

`GET /products`

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "symbol": "string",
    "description": "string",
    "created_at": "string",
    "updated_at": "string",
    "settlement_time": "string",
    "product_type": "future",
    "pricing_source": "string",
    "impact_size": 0,
    "initial_margin": 0,
    "maintenance_margin": "string",
    "contract_value": "string",
    "contract_unit_currency": "string",
    "tick_size": "string",
    "trading_status": "operational",
    "max_leverage_notional": "string",
    "default_leverage": "string",
    "initial_margin_scaling_factor": "string",
    "maintenance_margin_scaling_factor": "string",
    "commission_rate": "string",
    "maker_commission_rate": "string",
    "liquidation_penalty_factor": "string",
    "contract_type": "string",
    "position_size_limit": 0,
    "basis_factor_max_limit": "string",
    "is_quanto": true,
    "funding_method": "string",
    "annualized_funding": "string",
    "price_band": "string",
    "underlying_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    },
    "quoting_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    },
    "settling_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    }
  }
]
```

<h3 id="get-live-products-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|List of live products|[ArrayOfProducts](#schemaarrayofproducts)|

<aside class="success">
This operation does not require authentication.
</aside>

## Get 24hr ticker

<a id="opIddelta-exchange-api-get24hrTicker"></a>

> Code samples

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.delta.exchange/products/ticker/24hr', params={
  'symbol': 'string'
}, headers = headers)

print r.json()

```

```shell
# You can also use wget
curl -X GET https://api.delta.exchange/products/ticker/24hr?symbol=string \
  -H 'Accept: application/json'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.delta.exchange/products/ticker/24hr',
  params: {
  'symbol' => 'string'
}, headers: headers

p JSON.parse(result)

```

`GET /products/ticker/24hr`

<h3 id="get-24hr-ticker-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|symbol|query|string|true|product symbol|

> Example responses

> 200 Response

```json
{
  "symbol": "string",
  "timestamp": 0,
  "open": 0,
  "high": 0,
  "low": 0,
  "close": 0,
  "volume": 0
}
```

<h3 id="get-24hr-ticker-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Ticker Date|[24hrTicker](#schema24hrticker)|

<aside class="success">
This operation does not require authentication.
</aside>

<h1 id="delta-exchange-api-orders">Orders</h1>

Placing Orders, Cancelling Orders, Placing batch orders, Cancelling batch orders, Get Open orders, Change Orders Leverage

## Place Order

<a id="opIddelta-exchange-api-placeOrder"></a>

> Code samples

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'api-key': '****',
  'signature': '****',
  'timestamp': '****'
}

r = requests.post('https://api.delta.exchange/orders', params={

}, headers = headers)

print r.json()

```

```shell
# You can also use wget
curl -X POST https://api.delta.exchange/orders \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'api-key: ****' \
  -H 'signature: ****' \
  -H 'timestamp: ****'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'api-key' => '****',
  'signature' => '****',
  'timestamp' => '****'
}

result = RestClient.post 'https://api.delta.exchange/orders',
  params: {
  }, headers: headers

p JSON.parse(result)

```

`POST /orders`

> Body parameter

```json
{
  "product_id": 0,
  "limit_price": "string",
  "size": 0,
  "side": "buy",
  "order_type": "limit_order",
  "time_in_force": "gtc",
  "post_only": "true",
  "reduce_only": "true",
  "bracket_order": {
    "stop_loss_price": "string",
    "take_profit_price": "string",
    "trail_amount": "string"
  }
}
```

<h3 id="place-order-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[CreateOrderRequest](#schemacreateorderrequest)|true|Order which needs to be created|

> Example responses

> 200 Response

```json
{
  "id": 0,
  "user_id": 0,
  "size": 0,
  "unfilled_size": 0,
  "side": "buy",
  "order_type": "limit_order",
  "limit_price": "string",
  "stop_order_type": "stop_loss_order",
  "stop_price": "string",
  "close_on_trigger": "false",
  "state": "open",
  "created_at": "string",
  "product": {
    "id": 0,
    "symbol": "string",
    "description": "string",
    "created_at": "string",
    "updated_at": "string",
    "settlement_time": "string",
    "product_type": "future",
    "pricing_source": "string",
    "impact_size": 0,
    "initial_margin": 0,
    "maintenance_margin": "string",
    "contract_value": "string",
    "contract_unit_currency": "string",
    "tick_size": "string",
    "trading_status": "operational",
    "max_leverage_notional": "string",
    "default_leverage": "string",
    "initial_margin_scaling_factor": "string",
    "maintenance_margin_scaling_factor": "string",
    "commission_rate": "string",
    "maker_commission_rate": "string",
    "liquidation_penalty_factor": "string",
    "contract_type": "string",
    "position_size_limit": 0,
    "basis_factor_max_limit": "string",
    "is_quanto": true,
    "funding_method": "string",
    "annualized_funding": "string",
    "price_band": "string",
    "underlying_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    },
    "quoting_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    },
    "settling_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    }
  }
}
```

<h3 id="place-order-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns back the order object with assigned id and latest state|[Order](#schemaorder)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Returns [error](#place-order-error-description) if order could not be placed|Inline|

<h3 id="place-order-responseschema">Response Schema</h3>

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» error|string|false|none|none|
|» message|string|false|none|A more verbose error message|

#### Enumerated Values

|Property|Value|
|---|---|
|error|InsufficientMargin|
|error|OrderSizeExceededAvailable|
|error|OrderExceedsSizeLimit|
|error|OrderLeverageNotSet|
|error|InvalidProduct|
|error|ImmediateLiquidationOrder|
|error|LowerthanBankruptcy|
|error|SelfMatchingPostOnlyMode|
|error|ImmediateExecutionPostOnlyOrder|
|error|BracketOrderPositionExists|
|error|InvalidBracketOrder|

<aside class="warning">
To perform this operation, you must be sign the request using your api key and secret. See Authentication section for more details.
</aside>

## Cancel Order

<a id="opIddelta-exchange-api-cancelOrder"></a>

> Code samples

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'api-key': '****',
  'signature': '****',
  'timestamp': '****'
}

r = requests.delete('https://api.delta.exchange/orders', params={

}, headers = headers)

print r.json()

```

```shell
# You can also use wget
curl -X DELETE https://api.delta.exchange/orders \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'api-key: ****' \
  -H 'signature: ****' \
  -H 'timestamp: ****'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'api-key' => '****',
  'signature' => '****',
  'timestamp' => '****'
}

result = RestClient.delete 'https://api.delta.exchange/orders',
  params: {
  }, headers: headers

p JSON.parse(result)

```

`DELETE /orders`

> Body parameter

```json
{
  "id": 0,
  "product_id": 0
}
```

<h3 id="cancel-order-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[DeleteOrderRequest](#schemadeleteorderrequest)|true|Order which needs to be cancelled|

> Example responses

> 200 Response

```json
{
  "id": 0,
  "user_id": 0,
  "size": 0,
  "unfilled_size": 0,
  "side": "buy",
  "order_type": "limit_order",
  "limit_price": "string",
  "stop_order_type": "stop_loss_order",
  "stop_price": "string",
  "close_on_trigger": "false",
  "state": "open",
  "created_at": "string",
  "product": {
    "id": 0,
    "symbol": "string",
    "description": "string",
    "created_at": "string",
    "updated_at": "string",
    "settlement_time": "string",
    "product_type": "future",
    "pricing_source": "string",
    "impact_size": 0,
    "initial_margin": 0,
    "maintenance_margin": "string",
    "contract_value": "string",
    "contract_unit_currency": "string",
    "tick_size": "string",
    "trading_status": "operational",
    "max_leverage_notional": "string",
    "default_leverage": "string",
    "initial_margin_scaling_factor": "string",
    "maintenance_margin_scaling_factor": "string",
    "commission_rate": "string",
    "maker_commission_rate": "string",
    "liquidation_penalty_factor": "string",
    "contract_type": "string",
    "position_size_limit": 0,
    "basis_factor_max_limit": "string",
    "is_quanto": true,
    "funding_method": "string",
    "annualized_funding": "string",
    "price_band": "string",
    "underlying_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    },
    "quoting_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    },
    "settling_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    }
  }
}
```

<h3 id="cancel-order-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns back the order object|[Order](#schemaorder)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Returns error if order could not be cancelled|Inline|

<h3 id="cancel-order-responseschema">Response Schema</h3>

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» error|string|false|none|none|
|» message|string|false|none|A more verbose error message|

#### Enumerated Values

|Property|Value|
|---|---|
|error|ALREADY_FILLED|
|error|InvalidOrder|
|error|InvalidProduct|

<aside class="warning">
To perform this operation, you must be sign the request using your api key and secret. See Authentication section for more details.
</aside>

## Get Orders

<a id="opIddelta-exchange-api-getOrders"></a>

> Code samples

```python
import requests
headers = {
  'Accept': 'application/json',
  'api-key': '****',
  'signature': '****',
  'timestamp': '****'
}

r = requests.get('https://api.delta.exchange/orders', params={

}, headers = headers)

print r.json()

```

```shell
# You can also use wget
curl -X GET https://api.delta.exchange/orders \
  -H 'Accept: application/json' \
  -H 'api-key: ****' \
  -H 'signature: ****' \
  -H 'timestamp: ****'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'api-key' => '****',
  'signature' => '****',
  'timestamp' => '****'
}

result = RestClient.get 'https://api.delta.exchange/orders',
  params: {
  }, headers: headers

p JSON.parse(result)

```

`GET /orders`

<h3 id="get-orders-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|product_id|query|integer|false|get orders for a particular product id|
|state|query|string|false|get orders with a particular state|
|stop_order_type|query|string|false|get stop orders with stop_order_type|
|page_num|query|integer|false|page number for pagination|
|page_size|query|integer|false|page size for pagination|

#### Enumerated Values

|Parameter|Value|
|---|---|
|state|open|
|state|closed|
|state|cancelled|
|stop_order_type|stop_loss_order|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "user_id": 0,
    "size": 0,
    "unfilled_size": 0,
    "side": "buy",
    "order_type": "limit_order",
    "limit_price": "string",
    "stop_order_type": "stop_loss_order",
    "stop_price": "string",
    "close_on_trigger": "false",
    "state": "open",
    "created_at": "string",
    "product": {
      "id": 0,
      "symbol": "string",
      "description": "string",
      "created_at": "string",
      "updated_at": "string",
      "settlement_time": "string",
      "product_type": "future",
      "pricing_source": "string",
      "impact_size": 0,
      "initial_margin": 0,
      "maintenance_margin": "string",
      "contract_value": "string",
      "contract_unit_currency": "string",
      "tick_size": "string",
      "trading_status": "operational",
      "max_leverage_notional": "string",
      "default_leverage": "string",
      "initial_margin_scaling_factor": "string",
      "maintenance_margin_scaling_factor": "string",
      "commission_rate": "string",
      "maker_commission_rate": "string",
      "liquidation_penalty_factor": "string",
      "contract_type": "string",
      "position_size_limit": 0,
      "basis_factor_max_limit": "string",
      "is_quanto": true,
      "funding_method": "string",
      "annualized_funding": "string",
      "price_band": "string",
      "underlying_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "quoting_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "settling_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      }
    }
  }
]
```

<h3 id="get-orders-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|List of orders as per the query|[ArrayOfOrders](#schemaarrayoforders)|

<aside class="warning">
To perform this operation, you must be sign the request using your api key and secret. See Authentication section for more details.
</aside>

## Edit Order

<a id="opIddelta-exchange-api-editOrder"></a>

> Code samples

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'api-key': '****',
  'signature': '****',
  'timestamp': '****'
}

r = requests.put('https://api.delta.exchange/orders', params={

}, headers = headers)

print r.json()

```

```shell
# You can also use wget
curl -X PUT https://api.delta.exchange/orders \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'api-key: ****' \
  -H 'signature: ****' \
  -H 'timestamp: ****'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'api-key' => '****',
  'signature' => '****',
  'timestamp' => '****'
}

result = RestClient.put 'https://api.delta.exchange/orders',
  params: {
  }, headers: headers

p JSON.parse(result)

```

`PUT /orders`

> Body parameter

```json
{
  "id": 0,
  "product_id": 0,
  "limit_price": "string",
  "size": 0
}
```

<h3 id="edit-order-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[EditOrderRequest](#schemaeditorderrequest)|true|Order which needs to be edited|

> Example responses

> 200 Response

```json
{
  "id": 0,
  "user_id": 0,
  "size": 0,
  "unfilled_size": 0,
  "side": "buy",
  "order_type": "limit_order",
  "limit_price": "string",
  "stop_order_type": "stop_loss_order",
  "stop_price": "string",
  "close_on_trigger": "false",
  "state": "open",
  "created_at": "string",
  "product": {
    "id": 0,
    "symbol": "string",
    "description": "string",
    "created_at": "string",
    "updated_at": "string",
    "settlement_time": "string",
    "product_type": "future",
    "pricing_source": "string",
    "impact_size": 0,
    "initial_margin": 0,
    "maintenance_margin": "string",
    "contract_value": "string",
    "contract_unit_currency": "string",
    "tick_size": "string",
    "trading_status": "operational",
    "max_leverage_notional": "string",
    "default_leverage": "string",
    "initial_margin_scaling_factor": "string",
    "maintenance_margin_scaling_factor": "string",
    "commission_rate": "string",
    "maker_commission_rate": "string",
    "liquidation_penalty_factor": "string",
    "contract_type": "string",
    "position_size_limit": 0,
    "basis_factor_max_limit": "string",
    "is_quanto": true,
    "funding_method": "string",
    "annualized_funding": "string",
    "price_band": "string",
    "underlying_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    },
    "quoting_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    },
    "settling_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    }
  }
}
```

<h3 id="edit-order-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns back the order object with assigned id and latest state|[Order](#schemaorder)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Returns [error](#place-order-error-description) if order could not be placed|Inline|

<h3 id="edit-order-responseschema">Response Schema</h3>

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» error|string|false|none|none|
|» message|string|false|none|A more verbose error message|

#### Enumerated Values

|Property|Value|
|---|---|
|error|InsufficientMargin|
|error|OrderSizeExceededAvailable|
|error|OrderExceedsSizeLimit|
|error|OrderLeverageNotSet|
|error|InvalidProduct|
|error|ImmediateLiquidationOrder|
|error|LowerthanBankruptcy|
|error|SelfMatchingPostOnlyMode|
|error|ImmediateExecutionPostOnlyOrder|

<aside class="warning">
To perform this operation, you must be sign the request using your api key and secret. See Authentication section for more details.
</aside>

## Cancel all open orders

<a id="opIddelta-exchange-api-cancelAllOrders"></a>

> Code samples

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'api-key': '****',
  'signature': '****',
  'timestamp': '****'
}

r = requests.delete('https://api.delta.exchange/orders/all', params={

}, headers = headers)

print r.json()

```

```shell
# You can also use wget
curl -X DELETE https://api.delta.exchange/orders/all \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'api-key: ****' \
  -H 'signature: ****' \
  -H 'timestamp: ****'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'api-key' => '****',
  'signature' => '****',
  'timestamp' => '****'
}

result = RestClient.delete 'https://api.delta.exchange/orders/all',
  params: {
  }, headers: headers

p JSON.parse(result)

```

`DELETE /orders/all`

> Body parameter

```json
{
  "product_id": 0,
  "cancel_limit_orders": "true",
  "cancel_stop_orders": "true"
}
```

<h3 id="cancel-all-open-orders-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[CancelAllFilterObject](#schemacancelallfilterobject)|false|Filters for selecting orders that needs to be cancelled|

> Example responses

> 200 Response

```json
{}
```

<h3 id="cancel-all-open-orders-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|returns back success response|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Returns error if orders could not be cancelled|Inline|

<h3 id="cancel-all-open-orders-responseschema">Response Schema</h3>

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» error|string|false|none|none|
|» message|string|false|none|A more verbose error message|

#### Enumerated Values

|Property|Value|
|---|---|
|error|InvalidProduct|

<aside class="warning">
To perform this operation, you must be sign the request using your api key and secret. See Authentication section for more details.
</aside>

## Place Bracket Order __DEPRECATED__

<a id="opIddelta-exchange-api-placeBracketOrder"></a>

> Code samples

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'api-key': '****',
  'signature': '****',
  'timestamp': '****'
}

r = requests.post('https://api.delta.exchange/orders/bracket', params={

}, headers = headers)

print r.json()

```

```shell
# You can also use wget
curl -X POST https://api.delta.exchange/orders/bracket \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'api-key: ****' \
  -H 'signature: ****' \
  -H 'timestamp: ****'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'api-key' => '****',
  'signature' => '****',
  'timestamp' => '****'
}

result = RestClient.post 'https://api.delta.exchange/orders/bracket',
  params: {
  }, headers: headers

p JSON.parse(result)

```

`POST /orders/bracket`

> Body parameter

```json
{
  "product_id": 0,
  "stop_loss_order": {
    "order_type": "market_order",
    "stop_price": "string"
  },
  "take_profit_order": {
    "order_type": "market_order",
    "stop_price": "string"
  }
}
```

<h3 id="place-bracket-order-__deprecated__-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[CreateBracketOrderRequest](#schemacreatebracketorderrequest)|true|Bracket order which needs to be created|

> Example responses

> 200 Response

```json
{
  "stop_loss_order": {
    "id": 0,
    "user_id": 0,
    "size": 0,
    "unfilled_size": 0,
    "side": "buy",
    "order_type": "limit_order",
    "limit_price": "string",
    "stop_order_type": "stop_loss_order",
    "stop_price": "string",
    "close_on_trigger": "false",
    "state": "open",
    "created_at": "string",
    "product": {
      "id": 0,
      "symbol": "string",
      "description": "string",
      "created_at": "string",
      "updated_at": "string",
      "settlement_time": "string",
      "product_type": "future",
      "pricing_source": "string",
      "impact_size": 0,
      "initial_margin": 0,
      "maintenance_margin": "string",
      "contract_value": "string",
      "contract_unit_currency": "string",
      "tick_size": "string",
      "trading_status": "operational",
      "max_leverage_notional": "string",
      "default_leverage": "string",
      "initial_margin_scaling_factor": "string",
      "maintenance_margin_scaling_factor": "string",
      "commission_rate": "string",
      "maker_commission_rate": "string",
      "liquidation_penalty_factor": "string",
      "contract_type": "string",
      "position_size_limit": 0,
      "basis_factor_max_limit": "string",
      "is_quanto": true,
      "funding_method": "string",
      "annualized_funding": "string",
      "price_band": "string",
      "underlying_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "quoting_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "settling_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      }
    }
  },
  "take_profit_order": {
    "id": 0,
    "user_id": 0,
    "size": 0,
    "unfilled_size": 0,
    "side": "buy",
    "order_type": "limit_order",
    "limit_price": "string",
    "stop_order_type": "stop_loss_order",
    "stop_price": "string",
    "close_on_trigger": "false",
    "state": "open",
    "created_at": "string",
    "product": {
      "id": 0,
      "symbol": "string",
      "description": "string",
      "created_at": "string",
      "updated_at": "string",
      "settlement_time": "string",
      "product_type": "future",
      "pricing_source": "string",
      "impact_size": 0,
      "initial_margin": 0,
      "maintenance_margin": "string",
      "contract_value": "string",
      "contract_unit_currency": "string",
      "tick_size": "string",
      "trading_status": "operational",
      "max_leverage_notional": "string",
      "default_leverage": "string",
      "initial_margin_scaling_factor": "string",
      "maintenance_margin_scaling_factor": "string",
      "commission_rate": "string",
      "maker_commission_rate": "string",
      "liquidation_penalty_factor": "string",
      "contract_type": "string",
      "position_size_limit": 0,
      "basis_factor_max_limit": "string",
      "is_quanto": true,
      "funding_method": "string",
      "annualized_funding": "string",
      "price_band": "string",
      "underlying_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "quoting_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "settling_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      }
    }
  }
}
```

<h3 id="place-bracket-order-__deprecated__-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns back the stop loss and take profit orders with assigned ids and latest states|[BracketOrder](#schemabracketorder)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Returns error if order could not be placed|Inline|

<h3 id="place-bracket-order-__deprecated__-responseschema">Response Schema</h3>

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» error|string|false|none|none|
|» message|string|false|none|A more verbose error message|

#### Enumerated Values

|Property|Value|
|---|---|
|error|ImmediateExecutionStopOrder|
|error|CloseOnTriggerExists|
|error|NoOpenPosition|

<aside class="warning">
To perform this operation, you must be sign the request using your api key and secret. See Authentication section for more details.
</aside>

## Create batch orders

<a id="opIddelta-exchange-api-batchCreate"></a>

> Code samples

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'api-key': '****',
  'signature': '****',
  'timestamp': '****'
}

r = requests.post('https://api.delta.exchange/orders/batch', params={

}, headers = headers)

print r.json()

```

```shell
# You can also use wget
curl -X POST https://api.delta.exchange/orders/batch \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'api-key: ****' \
  -H 'signature: ****' \
  -H 'timestamp: ****'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'api-key' => '****',
  'signature' => '****',
  'timestamp' => '****'
}

result = RestClient.post 'https://api.delta.exchange/orders/batch',
  params: {
  }, headers: headers

p JSON.parse(result)

```

`POST /orders/batch`

> Body parameter

```json
[
  {
    "product_id": 0,
    "limit_price": "string",
    "size": 0,
    "side": "buy",
    "order_type": "limit_order",
    "time_in_force": "gtc",
    "post_only": "true",
    "reduce_only": "true",
    "bracket_order": {
      "stop_loss_price": "string",
      "take_profit_price": "string",
      "trail_amount": "string"
    }
  }
]
```

<h3 id="create-batch-orders-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[ArrayOfCreateOrderRequest](#schemaarrayofcreateorderrequest)|true|Does not support time_in_force flag for orders, All orders in batch create are assumed to be gtc orders. batch create does not support stop orders, it support only limit orders|

> Example responses

> 200 Response

```json
{
  "id": 0,
  "user_id": 0,
  "size": 0,
  "unfilled_size": 0,
  "side": "buy",
  "order_type": "limit_order",
  "limit_price": "string",
  "stop_order_type": "stop_loss_order",
  "stop_price": "string",
  "close_on_trigger": "false",
  "state": "open",
  "created_at": "string",
  "product": {
    "id": 0,
    "symbol": "string",
    "description": "string",
    "created_at": "string",
    "updated_at": "string",
    "settlement_time": "string",
    "product_type": "future",
    "pricing_source": "string",
    "impact_size": 0,
    "initial_margin": 0,
    "maintenance_margin": "string",
    "contract_value": "string",
    "contract_unit_currency": "string",
    "tick_size": "string",
    "trading_status": "operational",
    "max_leverage_notional": "string",
    "default_leverage": "string",
    "initial_margin_scaling_factor": "string",
    "maintenance_margin_scaling_factor": "string",
    "commission_rate": "string",
    "maker_commission_rate": "string",
    "liquidation_penalty_factor": "string",
    "contract_type": "string",
    "position_size_limit": 0,
    "basis_factor_max_limit": "string",
    "is_quanto": true,
    "funding_method": "string",
    "annualized_funding": "string",
    "price_band": "string",
    "underlying_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    },
    "quoting_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    },
    "settling_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    }
  }
}
```

<h3 id="create-batch-orders-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|returns the orders placed|[Order](#schemaorder)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|returns error if orders couldnt be placed|Inline|

<h3 id="create-batch-orders-responseschema">Response Schema</h3>

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» error|string|false|none|none|
|» message|string|false|none|A more verbose error message|

#### Enumerated Values

|Property|Value|
|---|---|
|error|InsufficientMargin|
|error|OrderSizeExceededAvailable|
|error|OrderExceedsSizeLimit|
|error|OrderLeverageNotSet|
|error|InvalidProduct|
|error|ImmediateLiquidationOrder|
|error|LowerthanBankruptcy|

<aside class="warning">
To perform this operation, you must be sign the request using your api key and secret. See Authentication section for more details.
</aside>

## Edit batch orders

<a id="opIddelta-exchange-api-batchEdit"></a>

> Code samples

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'api-key': '****',
  'signature': '****',
  'timestamp': '****'
}

r = requests.put('https://api.delta.exchange/orders/batch', params={

}, headers = headers)

print r.json()

```

```shell
# You can also use wget
curl -X PUT https://api.delta.exchange/orders/batch \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'api-key: ****' \
  -H 'signature: ****' \
  -H 'timestamp: ****'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'api-key' => '****',
  'signature' => '****',
  'timestamp' => '****'
}

result = RestClient.put 'https://api.delta.exchange/orders/batch',
  params: {
  }, headers: headers

p JSON.parse(result)

```

`PUT /orders/batch`

batch order edit 

> Body parameter

```json
{
  "product_id": 0,
  "orders": [
    {
      "id": 0,
      "size": 0,
      "limit_price": "string",
      "product_id": 0
    }
  ]
}
```

<h3 id="edit-batch-orders-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[EditBatchOrders](#schemaeditbatchorders)|true|none|

> Example responses

> 400 Response

```json
{
  "error": "InsufficientMargin",
  "message": "string"
}
```

<h3 id="edit-batch-orders-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OK|None|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|returns error if orders couldnt be edited|Inline|

<h3 id="edit-batch-orders-responseschema">Response Schema</h3>

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» error|string|false|none|none|
|» message|string|false|none|A more verbose error message|

#### Enumerated Values

|Property|Value|
|---|---|
|error|InsufficientMargin|
|error|OrderSizeExceededAvailable|
|error|OrderExceedsSizeLimit|
|error|OrderLeverageNotSet|
|error|InvalidProduct|
|error|ImmediateLiquidationOrder|
|error|LowerthanBankruptcy|

<aside class="warning">
To perform this operation, you must be sign the request using your api key and secret. See Authentication section for more details.
</aside>

## Delele batch orders

<a id="opIddelta-exchange-api-batchDelete"></a>

> Code samples

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'api-key': '****',
  'signature': '****',
  'timestamp': '****'
}

r = requests.delete('https://api.delta.exchange/orders/batch', params={

}, headers = headers)

print r.json()

```

```shell
# You can also use wget
curl -X DELETE https://api.delta.exchange/orders/batch \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'api-key: ****' \
  -H 'signature: ****' \
  -H 'timestamp: ****'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'api-key' => '****',
  'signature' => '****',
  'timestamp' => '****'
}

result = RestClient.delete 'https://api.delta.exchange/orders/batch',
  params: {
  }, headers: headers

p JSON.parse(result)

```

`DELETE /orders/batch`

> Body parameter

```json
[
  {
    "id": 0,
    "product_id": 0
  }
]
```

<h3 id="delele-batch-orders-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[ArrayOfDeleteOrderRequest](#schemaarrayofdeleteorderrequest)|true|none|

> Example responses

> 200 Response

```json
{
  "id": 0,
  "user_id": 0,
  "size": 0,
  "unfilled_size": 0,
  "side": "buy",
  "order_type": "limit_order",
  "limit_price": "string",
  "stop_order_type": "stop_loss_order",
  "stop_price": "string",
  "close_on_trigger": "false",
  "state": "open",
  "created_at": "string",
  "product": {
    "id": 0,
    "symbol": "string",
    "description": "string",
    "created_at": "string",
    "updated_at": "string",
    "settlement_time": "string",
    "product_type": "future",
    "pricing_source": "string",
    "impact_size": 0,
    "initial_margin": 0,
    "maintenance_margin": "string",
    "contract_value": "string",
    "contract_unit_currency": "string",
    "tick_size": "string",
    "trading_status": "operational",
    "max_leverage_notional": "string",
    "default_leverage": "string",
    "initial_margin_scaling_factor": "string",
    "maintenance_margin_scaling_factor": "string",
    "commission_rate": "string",
    "maker_commission_rate": "string",
    "liquidation_penalty_factor": "string",
    "contract_type": "string",
    "position_size_limit": 0,
    "basis_factor_max_limit": "string",
    "is_quanto": true,
    "funding_method": "string",
    "annualized_funding": "string",
    "price_band": "string",
    "underlying_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    },
    "quoting_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    },
    "settling_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    }
  }
}
```

<h3 id="delele-batch-orders-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|returns the orders deleted|[Order](#schemaorder)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|returns error if orders couldnt be deleted|Inline|

<h3 id="delele-batch-orders-responseschema">Response Schema</h3>

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» error|string|false|none|none|
|» message|string|false|none|A more verbose error message|

#### Enumerated Values

|Property|Value|
|---|---|
|error|ALREADY_FILLED|
|error|InvalidOrder|
|error|InvalidProduct|

<aside class="warning">
To perform this operation, you must be sign the request using your api key and secret. See Authentication section for more details.
</aside>

## Change order leverage

<a id="opIddelta-exchange-api-changeOrderLeverage"></a>

> Code samples

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': '*/*',
  'api-key': '****',
  'signature': '****',
  'timestamp': '****'
}

r = requests.post('https://api.delta.exchange/orders/leverage', params={

}, headers = headers)

print r.json()

```

```shell
# You can also use wget
curl -X POST https://api.delta.exchange/orders/leverage \
  -H 'Content-Type: application/json' \
  -H 'Accept: */*' \
  -H 'api-key: ****' \
  -H 'signature: ****' \
  -H 'timestamp: ****'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => '*/*',
  'api-key' => '****',
  'signature' => '****',
  'timestamp' => '****'
}

result = RestClient.post 'https://api.delta.exchange/orders/leverage',
  params: {
  }, headers: headers

p JSON.parse(result)

```

`POST /orders/leverage`

> Body parameter

```json
{
  "product_id": 0,
  "leverage": "string"
}
```

<h3 id="change-order-leverage-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» product_id|body|integer|true|none|
|» leverage|body|string|true|none|

> Example responses

> 200 Response

<h3 id="change-order-leverage-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|returns the OrderLeverage object|[OrderLeverage](#schemaorderleverage)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Returns error if leverage couldnt be changed|Inline|

<h3 id="change-order-leverage-responseschema">Response Schema</h3>

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» error|string|false|none|none|
|» message|string|false|none|A more verbose error message|

#### Enumerated Values

|Property|Value|
|---|---|
|error|InsufficientMargin|
|error|LeverageLimitExceeded|

<aside class="warning">
To perform this operation, you must be sign the request using your api key and secret. See Authentication section for more details.
</aside>

## Get order leverage

<a id="opIddelta-exchange-api-getOrderLeverage"></a>

> Code samples

```python
import requests
headers = {
  'Accept': '*/*',
  'api-key': '****',
  'signature': '****',
  'timestamp': '****'
}

r = requests.get('https://api.delta.exchange/orders/leverage', params={
  'product_id': '0'
}, headers = headers)

print r.json()

```

```shell
# You can also use wget
curl -X GET https://api.delta.exchange/orders/leverage?product_id=0 \
  -H 'Accept: */*' \
  -H 'api-key: ****' \
  -H 'signature: ****' \
  -H 'timestamp: ****'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => '*/*',
  'api-key' => '****',
  'signature' => '****',
  'timestamp' => '****'
}

result = RestClient.get 'https://api.delta.exchange/orders/leverage',
  params: {
  'product_id' => 'integer'
}, headers: headers

p JSON.parse(result)

```

`GET /orders/leverage`

<h3 id="get-order-leverage-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|product_id|query|integer|true|none|

> Example responses

> 200 Response

<h3 id="get-order-leverage-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|returns the OrderLeverage object|[OrderLeverage](#schemaorderleverage)|

<aside class="warning">
To perform this operation, you must be sign the request using your api key and secret. See Authentication section for more details.
</aside>

<h1 id="delta-exchange-api-positions">Positions</h1>

Get Open positions, Change Position Margin, Close Position

## Get open positions

<a id="opIddelta-exchange-api-getPositions"></a>

> Code samples

```python
import requests
headers = {
  'Accept': 'application/json',
  'api-key': '****',
  'signature': '****',
  'timestamp': '****'
}

r = requests.get('https://api.delta.exchange/positions', params={

}, headers = headers)

print r.json()

```

```shell
# You can also use wget
curl -X GET https://api.delta.exchange/positions \
  -H 'Accept: application/json' \
  -H 'api-key: ****' \
  -H 'signature: ****' \
  -H 'timestamp: ****'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'api-key' => '****',
  'signature' => '****',
  'timestamp' => '****'
}

result = RestClient.get 'https://api.delta.exchange/positions',
  params: {
  }, headers: headers

p JSON.parse(result)

```

`GET /positions`

> Example responses

> 200 Response

```json
[
  {
    "user_id": 0,
    "size": 0,
    "entry_price": "string",
    "margin": "string",
    "liquidation_price": "string",
    "bankruptcy_price": "string",
    "adl_level": 0,
    "product": {
      "id": 0,
      "symbol": "string",
      "description": "string",
      "created_at": "string",
      "updated_at": "string",
      "settlement_time": "string",
      "product_type": "future",
      "pricing_source": "string",
      "impact_size": 0,
      "initial_margin": 0,
      "maintenance_margin": "string",
      "contract_value": "string",
      "contract_unit_currency": "string",
      "tick_size": "string",
      "trading_status": "operational",
      "max_leverage_notional": "string",
      "default_leverage": "string",
      "initial_margin_scaling_factor": "string",
      "maintenance_margin_scaling_factor": "string",
      "commission_rate": "string",
      "maker_commission_rate": "string",
      "liquidation_penalty_factor": "string",
      "contract_type": "string",
      "position_size_limit": 0,
      "basis_factor_max_limit": "string",
      "is_quanto": true,
      "funding_method": "string",
      "annualized_funding": "string",
      "price_band": "string",
      "underlying_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "quoting_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "settling_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      }
    }
  }
]
```

<h3 id="get-open-positions-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|List of all open positions|[ArrayOfPositions](#schemaarrayofpositions)|

<aside class="warning">
To perform this operation, you must be sign the request using your api key and secret. See Authentication section for more details.
</aside>

## Add/Remove position margin

<a id="opIddelta-exchange-api-changePositionMargin"></a>

> Code samples

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'api-key': '****',
  'signature': '****',
  'timestamp': '****'
}

r = requests.post('https://api.delta.exchange/positions/change_margin', params={

}, headers = headers)

print r.json()

```

```shell
# You can also use wget
curl -X POST https://api.delta.exchange/positions/change_margin \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'api-key: ****' \
  -H 'signature: ****' \
  -H 'timestamp: ****'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'api-key' => '****',
  'signature' => '****',
  'timestamp' => '****'
}

result = RestClient.post 'https://api.delta.exchange/positions/change_margin',
  params: {
  }, headers: headers

p JSON.parse(result)

```

`POST /positions/change_margin`

> Body parameter

```json
{
  "product_id": 0,
  "delta_margin": "string"
}
```

<h3 id="add/remove-position-margin-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» product_id|body|integer|true|none|
|» delta_margin|body|string|true|Delta in the position margin, positive in case of adding margin & negative in case of removing margin|

> Example responses

> 200 Response

```json
{
  "user_id": 0,
  "size": 0,
  "entry_price": "string",
  "margin": "string",
  "liquidation_price": "string",
  "bankruptcy_price": "string",
  "adl_level": 0,
  "product": {
    "id": 0,
    "symbol": "string",
    "description": "string",
    "created_at": "string",
    "updated_at": "string",
    "settlement_time": "string",
    "product_type": "future",
    "pricing_source": "string",
    "impact_size": 0,
    "initial_margin": 0,
    "maintenance_margin": "string",
    "contract_value": "string",
    "contract_unit_currency": "string",
    "tick_size": "string",
    "trading_status": "operational",
    "max_leverage_notional": "string",
    "default_leverage": "string",
    "initial_margin_scaling_factor": "string",
    "maintenance_margin_scaling_factor": "string",
    "commission_rate": "string",
    "maker_commission_rate": "string",
    "liquidation_penalty_factor": "string",
    "contract_type": "string",
    "position_size_limit": 0,
    "basis_factor_max_limit": "string",
    "is_quanto": true,
    "funding_method": "string",
    "annualized_funding": "string",
    "price_band": "string",
    "underlying_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    },
    "quoting_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    },
    "settling_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    }
  }
}
```

<h3 id="add/remove-position-margin-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|returns the position object|[Position](#schemaposition)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Returns error if position margin could not be changed|Inline|

<h3 id="add/remove-position-margin-responseschema">Response Schema</h3>

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» error|string|false|none|none|
|» message|string|false|none|A more verbose error message|

#### Enumerated Values

|Property|Value|
|---|---|
|error|PositionNotSet|
|error|LeverageLimitExceeded|
|error|InsufficientMargin|
|error|ExistingOrderWithLowerThanBankruptcy|

<aside class="warning">
To perform this operation, you must be sign the request using your api key and secret. See Authentication section for more details.
</aside>

<h1 id="delta-exchange-api-trade-history">Trade History</h1>

Get Orders History, Get Fill History

## Get order history (cancelled and closed)

<a id="opIddelta-exchange-api-getOrderHistory"></a>

> Code samples

```python
import requests
headers = {
  'Accept': 'application/json',
  'api-key': '****',
  'signature': '****',
  'timestamp': '****'
}

r = requests.get('https://api.delta.exchange/orders/history', params={

}, headers = headers)

print r.json()

```

```shell
# You can also use wget
curl -X GET https://api.delta.exchange/orders/history \
  -H 'Accept: application/json' \
  -H 'api-key: ****' \
  -H 'signature: ****' \
  -H 'timestamp: ****'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'api-key' => '****',
  'signature' => '****',
  'timestamp' => '****'
}

result = RestClient.get 'https://api.delta.exchange/orders/history',
  params: {
  }, headers: headers

p JSON.parse(result)

```

`GET /orders/history`

<h3 id="get-order-history-(cancelled-and-closed)-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|page_num|query|integer|false|page number for pagination|
|page_size|query|integer|false|page size for pagination|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "user_id": 0,
    "size": 0,
    "unfilled_size": 0,
    "side": "buy",
    "order_type": "limit_order",
    "limit_price": "string",
    "stop_order_type": "stop_loss_order",
    "stop_price": "string",
    "close_on_trigger": "false",
    "state": "open",
    "created_at": "string",
    "product": {
      "id": 0,
      "symbol": "string",
      "description": "string",
      "created_at": "string",
      "updated_at": "string",
      "settlement_time": "string",
      "product_type": "future",
      "pricing_source": "string",
      "impact_size": 0,
      "initial_margin": 0,
      "maintenance_margin": "string",
      "contract_value": "string",
      "contract_unit_currency": "string",
      "tick_size": "string",
      "trading_status": "operational",
      "max_leverage_notional": "string",
      "default_leverage": "string",
      "initial_margin_scaling_factor": "string",
      "maintenance_margin_scaling_factor": "string",
      "commission_rate": "string",
      "maker_commission_rate": "string",
      "liquidation_penalty_factor": "string",
      "contract_type": "string",
      "position_size_limit": 0,
      "basis_factor_max_limit": "string",
      "is_quanto": true,
      "funding_method": "string",
      "annualized_funding": "string",
      "price_band": "string",
      "underlying_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "quoting_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "settling_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      }
    }
  }
]
```

<h3 id="get-order-history-(cancelled-and-closed)-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|List of orders|[ArrayOfOrders](#schemaarrayoforders)|

<aside class="warning">
To perform this operation, you must be sign the request using your api key and secret. See Authentication section for more details.
</aside>

## Get fills

<a id="opIddelta-exchange-api-getFills"></a>

> Code samples

```python
import requests
headers = {
  'Accept': 'application/json',
  'api-key': '****',
  'signature': '****',
  'timestamp': '****'
}

r = requests.get('https://api.delta.exchange/fills', params={

}, headers = headers)

print r.json()

```

```shell
# You can also use wget
curl -X GET https://api.delta.exchange/fills \
  -H 'Accept: application/json' \
  -H 'api-key: ****' \
  -H 'signature: ****' \
  -H 'timestamp: ****'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'api-key' => '****',
  'signature' => '****',
  'timestamp' => '****'
}

result = RestClient.get 'https://api.delta.exchange/fills',
  params: {
  }, headers: headers

p JSON.parse(result)

```

`GET /fills`

<h3 id="get-fills-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|product_id|query|integer|false|product id for fill query|
|start_time|query|integer|false|Start time for the fill query|
|end_time|query|integer|false|End time for the fill query|
|page_num|query|integer|false|page number for pagination|
|page_size|query|integer|false|page size for pagination|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "size": 0,
    "side": "buy",
    "price": "string",
    "role": "taker",
    "commission": "string",
    "created_at": "string",
    "product": {
      "id": 0,
      "symbol": "string",
      "description": "string",
      "created_at": "string",
      "updated_at": "string",
      "settlement_time": "string",
      "product_type": "future",
      "pricing_source": "string",
      "impact_size": 0,
      "initial_margin": 0,
      "maintenance_margin": "string",
      "contract_value": "string",
      "contract_unit_currency": "string",
      "tick_size": "string",
      "trading_status": "operational",
      "max_leverage_notional": "string",
      "default_leverage": "string",
      "initial_margin_scaling_factor": "string",
      "maintenance_margin_scaling_factor": "string",
      "commission_rate": "string",
      "maker_commission_rate": "string",
      "liquidation_penalty_factor": "string",
      "contract_type": "string",
      "position_size_limit": 0,
      "basis_factor_max_limit": "string",
      "is_quanto": true,
      "funding_method": "string",
      "annualized_funding": "string",
      "price_band": "string",
      "underlying_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "quoting_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "settling_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      }
    }
  }
]
```

<h3 id="get-fills-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|List of Fills|[ArrayOfFills](#schemaarrayoffills)|

<aside class="warning">
To perform this operation, you must be sign the request using your api key and secret. See Authentication section for more details.
</aside>

<h1 id="delta-exchange-api-orderbook">Orderbook</h1>

L2Orderbook

## Get L2 orderbook

<a id="opIddelta-exchange-api-getL2Orderbook"></a>

> Code samples

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.delta.exchange/orderbook/{product_id}/l2', params={

}, headers = headers)

print r.json()

```

```shell
# You can also use wget
curl -X GET https://api.delta.exchange/orderbook/{product_id}/l2 \
  -H 'Accept: application/json'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.delta.exchange/orderbook/{product_id}/l2',
  params: {
  }, headers: headers

p JSON.parse(result)

```

`GET /orderbook/{product_id}/l2`

<h3 id="get-l2-orderbook-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|product_id|path|integer|true|none|
|depth|query|integer|false|number of levels on each side|

> Example responses

> 200 Response

```json
{
  "buy_book": [
    {
      "price": "string",
      "size": 0
    }
  ],
  "sell_book": [
    {
      "price": "string",
      "size": 0
    }
  ],
  "recent_trades": [
    {
      "side": "buy",
      "size": 0,
      "price": "string",
      "timestamp": 0
    }
  ],
  "spot_price": "string",
  "mark_price": "string",
  "product_id": 0
}
```

<h3 id="get-l2-orderbook-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|L2 orderbook for the product|[L2Orderbook](#schemal2orderbook)|

<aside class="success">
This operation does not require authentication.
</aside>

<h1 id="delta-exchange-api-wallet">Wallet</h1>

Get balances, Get transaction history

## Get Wallet Balances

<a id="opIddelta-exchange-api-getWalletBalances"></a>

> Code samples

```python
import requests
headers = {
  'Accept': 'application/json',
  'api-key': '****',
  'signature': '****',
  'timestamp': '****'
}

r = requests.get('https://api.delta.exchange/wallet/balances', params={

}, headers = headers)

print r.json()

```

```shell
# You can also use wget
curl -X GET https://api.delta.exchange/wallet/balances \
  -H 'Accept: application/json' \
  -H 'api-key: ****' \
  -H 'signature: ****' \
  -H 'timestamp: ****'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'api-key' => '****',
  'signature' => '****',
  'timestamp' => '****'
}

result = RestClient.get 'https://api.delta.exchange/wallet/balances',
  params: {
  }, headers: headers

p JSON.parse(result)

```

`GET /wallet/balances`

> Example responses

> 200 Response

```json
[
  {
    "balance": "string",
    "order_margin": "string",
    "position_margin": "string",
    "commission": "string",
    "available_balance": "string",
    "asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    }
  }
]
```

<h3 id="get-wallet-balances-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|List of wallets attached to the user account|[ArrayOfWallets](#schemaarrayofwallets)|

<aside class="warning">
To perform this operation, you must be sign the request using your api key and secret. See Authentication section for more details.
</aside>

## Get Wallet transactions

<a id="opIddelta-exchange-api-getWalletTransactions"></a>

> Code samples

```python
import requests
headers = {
  'Accept': 'application/json',
  'api-key': '****',
  'signature': '****',
  'timestamp': '****'
}

r = requests.get('https://api.delta.exchange/wallet/transactions', params={
  'asset_id': '0'
}, headers = headers)

print r.json()

```

```shell
# You can also use wget
curl -X GET https://api.delta.exchange/wallet/transactions?asset_id=0 \
  -H 'Accept: application/json' \
  -H 'api-key: ****' \
  -H 'signature: ****' \
  -H 'timestamp: ****'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'api-key' => '****',
  'signature' => '****',
  'timestamp' => '****'
}

result = RestClient.get 'https://api.delta.exchange/wallet/transactions',
  params: {
  'asset_id' => 'integer'
}, headers: headers

p JSON.parse(result)

```

`GET /wallet/transactions`

<h3 id="get-wallet-transactions-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|asset_id|query|integer|true|asset_id for that particular Wallet|
|product_id|query|integer|false|product_id filter for the transaction query|
|transaction_type|query|integer|false|transaction_type filter for the transaction query|
|start_time|query|integer|false|Start time for the transaction query|
|end_time|query|integer|false|End time for the transaction query|
|page_num|query|integer|false|page number for pagination|
|page_size|query|integer|false|page size for pagination|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "amount": "string",
    "balance": "string",
    "transaction_type": "pnl",
    "meta_data": {},
    "product": {
      "id": 0,
      "symbol": "string",
      "description": "string",
      "created_at": "string",
      "updated_at": "string",
      "settlement_time": "string",
      "product_type": "future",
      "pricing_source": "string",
      "impact_size": 0,
      "initial_margin": 0,
      "maintenance_margin": "string",
      "contract_value": "string",
      "contract_unit_currency": "string",
      "tick_size": "string",
      "trading_status": "operational",
      "max_leverage_notional": "string",
      "default_leverage": "string",
      "initial_margin_scaling_factor": "string",
      "maintenance_margin_scaling_factor": "string",
      "commission_rate": "string",
      "maker_commission_rate": "string",
      "liquidation_penalty_factor": "string",
      "contract_type": "string",
      "position_size_limit": 0,
      "basis_factor_max_limit": "string",
      "is_quanto": true,
      "funding_method": "string",
      "annualized_funding": "string",
      "price_band": "string",
      "underlying_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "quoting_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "settling_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      }
    },
    "created_at": "string"
  }
]
```

<h3 id="get-wallet-transactions-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|list of transactions for that wallet|[ArrayOfTransactions](#schemaarrayoftransactions)|

<aside class="warning">
To perform this operation, you must be sign the request using your api key and secret. See Authentication section for more details.
</aside>

## Download Wallet transactions

<a id="opIddelta-exchange-api-downloadWalletTransactions"></a>

> Code samples

```python
import requests
headers = {
  'Accept': 'application/json',
  'api-key': '****',
  'signature': '****',
  'timestamp': '****'
}

r = requests.get('https://api.delta.exchange/wallet/download/transactions', params={
  'asset_id': '0'
}, headers = headers)

print r.json()

```

```shell
# You can also use wget
curl -X GET https://api.delta.exchange/wallet/download/transactions?asset_id=0 \
  -H 'Accept: application/json' \
  -H 'api-key: ****' \
  -H 'signature: ****' \
  -H 'timestamp: ****'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'api-key' => '****',
  'signature' => '****',
  'timestamp' => '****'
}

result = RestClient.get 'https://api.delta.exchange/wallet/download/transactions',
  params: {
  'asset_id' => 'integer'
}, headers: headers

p JSON.parse(result)

```

`GET /wallet/download/transactions`

<h3 id="download-wallet-transactions-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|asset_id|query|integer|true|asset_id for that particular Wallet|
|product_id|query|integer|false|product_id filter for the transaction query|
|transaction_type|query|integer|false|transaction_type filter for the transaction query|
|start_time|query|integer|false|Start time for the transaction query|
|end_time|query|integer|false|End time for the transaction query|

> Example responses

> 200 Response

```json
[
  {
    "id": 0,
    "amount": "string",
    "balance": "string",
    "transaction_type": "pnl",
    "meta_data": {},
    "product": {
      "id": 0,
      "symbol": "string",
      "description": "string",
      "created_at": "string",
      "updated_at": "string",
      "settlement_time": "string",
      "product_type": "future",
      "pricing_source": "string",
      "impact_size": 0,
      "initial_margin": 0,
      "maintenance_margin": "string",
      "contract_value": "string",
      "contract_unit_currency": "string",
      "tick_size": "string",
      "trading_status": "operational",
      "max_leverage_notional": "string",
      "default_leverage": "string",
      "initial_margin_scaling_factor": "string",
      "maintenance_margin_scaling_factor": "string",
      "commission_rate": "string",
      "maker_commission_rate": "string",
      "liquidation_penalty_factor": "string",
      "contract_type": "string",
      "position_size_limit": 0,
      "basis_factor_max_limit": "string",
      "is_quanto": true,
      "funding_method": "string",
      "annualized_funding": "string",
      "price_band": "string",
      "underlying_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "quoting_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "settling_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      }
    },
    "created_at": "string"
  }
]
```

<h3 id="download-wallet-transactions-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|csv of transactions for that wallet|[ArrayOfTransactions](#schemaarrayoftransactions)|

<aside class="warning">
To perform this operation, you must be sign the request using your api key and secret. See Authentication section for more details.
</aside>

## Raise withdrawals request

<a id="opIddelta-exchange-api-raiseWithdrawalRequest"></a>

> Code samples

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'api-key': '****',
  'signature': '****',
  'timestamp': '****'
}

r = requests.post('https://api.delta.exchange/wallet/withdrawals', params={

}, headers = headers)

print r.json()

```

```shell
# You can also use wget
curl -X POST https://api.delta.exchange/wallet/withdrawals \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'api-key: ****' \
  -H 'signature: ****' \
  -H 'timestamp: ****'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'api-key' => '****',
  'signature' => '****',
  'timestamp' => '****'
}

result = RestClient.post 'https://api.delta.exchange/wallet/withdrawals',
  params: {
  }, headers: headers

p JSON.parse(result)

```

`POST /wallet/withdrawals`

> Body parameter

```json
{
  "release_promo_credit": "string",
  "amount": "string",
  "address": "string"
}
```

<h3 id="raise-withdrawals-request-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» release_promo_credit|body|string|false|none|
|» amount|body|string|true|none|
|» address|body|string|true|none|

> Example responses

> 200 Response

```json
{
  "address": "string",
  "amount": "string",
  "fee": "string",
  "id": 0,
  "state": "string",
  "transaction_meta": "string",
  "user_id": 0
}
```

<h3 id="raise-withdrawals-request-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|returns the WithdrawalsResponse object|[WithdrawalsResponse](#schemawithdrawalsresponse)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Returns error if Withdrawal limit exceeded, ammount or address is missing or invalid|Inline|

<h3 id="raise-withdrawals-request-responseschema">Response Schema</h3>

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» error|string|false|none|none|
|» message|string|false|none|A more verbose error message|

#### Enumerated Values

|Property|Value|
|---|---|
|error|WithdrawalLimitExceeded|

<aside class="warning">
To perform this operation, you must be sign the request using your api key and secret. See Authentication section for more details.
</aside>

## Cancel withdrawals request

<a id="opIddelta-exchange-api-cancelWithdrawalRequest"></a>

> Code samples

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'api-key': '****',
  'signature': '****',
  'timestamp': '****'
}

r = requests.post('https://api.delta.exchange/wallet/withdrawals/cancel', params={

}, headers = headers)

print r.json()

```

```shell
# You can also use wget
curl -X POST https://api.delta.exchange/wallet/withdrawals/cancel \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'api-key: ****' \
  -H 'signature: ****' \
  -H 'timestamp: ****'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'api-key' => '****',
  'signature' => '****',
  'timestamp' => '****'
}

result = RestClient.post 'https://api.delta.exchange/wallet/withdrawals/cancel',
  params: {
  }, headers: headers

p JSON.parse(result)

```

`POST /wallet/withdrawals/cancel`

> Body parameter

```json
{
  "withdrawal_id": 0
}
```

<h3 id="cancel-withdrawals-request-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|none|
|» withdrawal_id|body|integer|true|none|

> Example responses

> 200 Response

```json
{
  "success": true
}
```

<h3 id="cancel-withdrawals-request-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|returns success true or false|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|Returns error if Withdrawal Withdrawal Already Processed|Inline|

<h3 id="cancel-withdrawals-request-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» success|boolean|false|none|none|

Status Code **400**

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|» error|string|false|none|none|
|» message|string|false|none|A more verbose error message|

#### Enumerated Values

|Property|Value|
|---|---|
|error|WithdrawalAlreadyProcessed|

<aside class="warning">
To perform this operation, you must be sign the request using your api key and secret. See Authentication section for more details.
</aside>

<h1 id="delta-exchange-api-ohlc-candles">OHLC Candles</h1>

## Get OHLC candles

<a id="opIddelta-exchange-api-getCandles"></a>

> Code samples

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.delta.exchange/chart/history', params={
  'symbol': 'string',  'from': '0',  'to': '0',  'resolution': '1'
}, headers = headers)

print r.json()

```

```shell
# You can also use wget
curl -X GET https://api.delta.exchange/chart/history?symbol=string&from=0&to=0&resolution=1 \
  -H 'Accept: application/json'

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.delta.exchange/chart/history',
  params: {
  'symbol' => 'string',
'from' => 'integer',
'to' => 'integer',
'resolution' => 'string'
}, headers: headers

p JSON.parse(result)

```

`GET /chart/history`

<h3 id="get-ohlc-candles-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|symbol|query|string|true|symbol should be anyone of following  1. product symbol to get OHLC for given product e.g **BTCUSD** 2. Spot index symbol to get spot index price. e.g. **.DEXBTUSD** 3. Mark and symbol to get mark price OHLC data e.g. **MARK:BTCUSD** 4. Funding and product symbol to get Funding data for given product e.g. **FUNDING:BTCUSD**|
|from|query|integer|true|start time for the interval ( in seconds )|
|to|query|integer|true|end time for the interval ( in seconds )|
|resolution|query|string|true|resolution for the candles|

#### Enumerated Values

|Parameter|Value|
|---|---|
|resolution|1|
|resolution|3|
|resolution|5|
|resolution|15|
|resolution|30|
|resolution|60|
|resolution|120|
|resolution|240|
|resolution|360|
|resolution|D|
|resolution|7D|
|resolution|30D|
|resolution|1W|
|resolution|2W|

> Example responses

> 200 Response

```json
{
  "t": [
    0
  ],
  "o": [
    "string"
  ],
  "h": [
    "string"
  ],
  "l": [
    "string"
  ],
  "c": [
    "string"
  ],
  "v": [
    0
  ]
}
```

<h3 id="get-ohlc-candles-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|OHLC candles|[OHLCData](#schemaohlcdata)|

<aside class="success">
This operation does not require authentication.
</aside>

# Schemas

<h2 id="tocSasset">Asset</h2>

<a id="schemaasset"></a>

```json
{
  "id": 0,
  "symbol": "string",
  "precision": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer(int64)|false|none|none|
|symbol|string|false|none|none|
|precision|integer|false|none|none|

<h2 id="tocSarrayofassets">ArrayOfAssets</h2>

<a id="schemaarrayofassets"></a>

```json
[
  {
    "id": 0,
    "symbol": "string",
    "precision": 0
  }
]

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Asset](#schemaasset)]|false|none|none|

<h2 id="tocSproduct">Product</h2>

<a id="schemaproduct"></a>

```json
{
  "id": 0,
  "symbol": "string",
  "description": "string",
  "created_at": "string",
  "updated_at": "string",
  "settlement_time": "string",
  "product_type": "future",
  "pricing_source": "string",
  "impact_size": 0,
  "initial_margin": 0,
  "maintenance_margin": "string",
  "contract_value": "string",
  "contract_unit_currency": "string",
  "tick_size": "string",
  "trading_status": "operational",
  "max_leverage_notional": "string",
  "default_leverage": "string",
  "initial_margin_scaling_factor": "string",
  "maintenance_margin_scaling_factor": "string",
  "commission_rate": "string",
  "maker_commission_rate": "string",
  "liquidation_penalty_factor": "string",
  "contract_type": "string",
  "position_size_limit": 0,
  "basis_factor_max_limit": "string",
  "is_quanto": true,
  "funding_method": "string",
  "annualized_funding": "string",
  "price_band": "string",
  "underlying_asset": {
    "id": 0,
    "symbol": "string",
    "precision": 0
  },
  "quoting_asset": {
    "id": 0,
    "symbol": "string",
    "precision": 0
  },
  "settling_asset": {
    "id": 0,
    "symbol": "string",
    "precision": 0
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer(int64)|false|none|id of a product or a contract|
|symbol|string|false|none|symbol of a product or a contract e.g. LINKBTC, XRPUSDQ|
|description|string|false|none|description of a product or a contract|
|created_at|string|false|none|product/contract creation date and time|
|updated_at|string|false|none|product/contract update date and time|
|settlement_time|string|false|none|settlement Timestamp of futures contract|
|product_type|string|false|none|contract type 'future' or 'inverse_future'|
|pricing_source|string|false|none|source and method of contract pricing|
|impact_size|integer|false|none|size of a typical trade. Used in the computation of mark price|
|initial_margin|integer|false|none|The amount required to enter into a new position|
|maintenance_margin|string|false|none|The amount necessary when a loss on a futures position requires you to allocate more funds to return the margin to the initial margin level.|
|contract_value|string|false|none|The notional value of a futures contract is simply the spot price of the asset multiplied by the amount of the asset specified in the contract|
|contract_unit_currency|string|false|none|This is the unit of  1 contract, for vanilla futures, its underlying asset. for inverse, it is settling asset. for quanto, its settling asset / quoting asset|
|tick_size|string|false|none|The minimum gap between 2 consecutive prices.|
|trading_status|string|false|none|trading status of the contract e.g. 'operational','disrupted_cancel_only' or 'disrupted_post_only'|
|max_leverage_notional|string|false|none|maximum notional position size (in settling asset terms) that can be acquired at highest allowed leverage for a given contract.|
|default_leverage|string|false|none|default leverage|
|initial_margin_scaling_factor|string|false|none|none|
|maintenance_margin_scaling_factor|string|false|none|none|
|commission_rate|string|false|none|rate at which commission fee will be calculated for a trade in given contract|
|maker_commission_rate|string|false|none|rate at which maker rebate will be calculated|
|liquidation_penalty_factor|string|false|none|Determines liquidation charge as per the following formula: liquidation_penalty_factor * minimum maintenance margin|
|contract_type|string|false|none|Type of contracts e.g. futures, perpetual futures,|
|position_size_limit|integer|false|none|Maximum size of contracts in a single order can be placed|
|basis_factor_max_limit|string|false|none|Maximum allowed value of annualized basis|
|is_quanto|boolean|false|none|Flag which denotes whether future contract is quanto or not|
|funding_method|string|false|none|Method used to calculate funding for given contract. e.g. Fixed or mark price|
|annualized_funding|string|false|none|Maximum allowed value of funding, expressed as annual rate.|
|price_band|string|false|none|he range around mark price in which trading is allowed. This number is in percentage.|
|underlying_asset|[Asset](#schemaasset)|false|none|none|
|quoting_asset|[Asset](#schemaasset)|false|none|none|
|settling_asset|[Asset](#schemaasset)|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|product_type|future|
|product_type|inverse_future|
|trading_status|operational|
|trading_status|disrupted_cancel_only|
|trading_status|disrupted_post_only|

<h2 id="tocSarrayofproducts">ArrayOfProducts</h2>

<a id="schemaarrayofproducts"></a>

```json
[
  {
    "id": 0,
    "symbol": "string",
    "description": "string",
    "created_at": "string",
    "updated_at": "string",
    "settlement_time": "string",
    "product_type": "future",
    "pricing_source": "string",
    "impact_size": 0,
    "initial_margin": 0,
    "maintenance_margin": "string",
    "contract_value": "string",
    "contract_unit_currency": "string",
    "tick_size": "string",
    "trading_status": "operational",
    "max_leverage_notional": "string",
    "default_leverage": "string",
    "initial_margin_scaling_factor": "string",
    "maintenance_margin_scaling_factor": "string",
    "commission_rate": "string",
    "maker_commission_rate": "string",
    "liquidation_penalty_factor": "string",
    "contract_type": "string",
    "position_size_limit": 0,
    "basis_factor_max_limit": "string",
    "is_quanto": true,
    "funding_method": "string",
    "annualized_funding": "string",
    "price_band": "string",
    "underlying_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    },
    "quoting_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    },
    "settling_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    }
  }
]

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Product](#schemaproduct)]|false|none|none|

<h2 id="tocSorder">Order</h2>

<a id="schemaorder"></a>

```json
{
  "id": 0,
  "user_id": 0,
  "size": 0,
  "unfilled_size": 0,
  "side": "buy",
  "order_type": "limit_order",
  "limit_price": "string",
  "stop_order_type": "stop_loss_order",
  "stop_price": "string",
  "close_on_trigger": "false",
  "state": "open",
  "created_at": "string",
  "product": {
    "id": 0,
    "symbol": "string",
    "description": "string",
    "created_at": "string",
    "updated_at": "string",
    "settlement_time": "string",
    "product_type": "future",
    "pricing_source": "string",
    "impact_size": 0,
    "initial_margin": 0,
    "maintenance_margin": "string",
    "contract_value": "string",
    "contract_unit_currency": "string",
    "tick_size": "string",
    "trading_status": "operational",
    "max_leverage_notional": "string",
    "default_leverage": "string",
    "initial_margin_scaling_factor": "string",
    "maintenance_margin_scaling_factor": "string",
    "commission_rate": "string",
    "maker_commission_rate": "string",
    "liquidation_penalty_factor": "string",
    "contract_type": "string",
    "position_size_limit": 0,
    "basis_factor_max_limit": "string",
    "is_quanto": true,
    "funding_method": "string",
    "annualized_funding": "string",
    "price_band": "string",
    "underlying_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    },
    "quoting_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    },
    "settling_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    }
  }
}

```

*An Order object*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|none|
|user_id|integer|false|none|none|
|size|integer|false|none|none|
|unfilled_size|integer|false|none|none|
|side|string|false|none|side for which to place order|
|order_type|string|false|none|none|
|limit_price|string|false|none|none|
|stop_order_type|string|false|none|none|
|stop_price|string|false|none|none|
|close_on_trigger|string|false|none|none|
|state|string|false|none|Order Status|
|created_at|string|false|none|none|
|product|[Product](#schemaproduct)|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|side|buy|
|side|sell|
|order_type|limit_order|
|order_type|market_order|
|stop_order_type|stop_loss_order|
|close_on_trigger|false|
|close_on_trigger|true|
|state|open|
|state|pending|
|state|closed|
|state|cancelled|

<h2 id="tocSarrayoforders">ArrayOfOrders</h2>

<a id="schemaarrayoforders"></a>

```json
[
  {
    "id": 0,
    "user_id": 0,
    "size": 0,
    "unfilled_size": 0,
    "side": "buy",
    "order_type": "limit_order",
    "limit_price": "string",
    "stop_order_type": "stop_loss_order",
    "stop_price": "string",
    "close_on_trigger": "false",
    "state": "open",
    "created_at": "string",
    "product": {
      "id": 0,
      "symbol": "string",
      "description": "string",
      "created_at": "string",
      "updated_at": "string",
      "settlement_time": "string",
      "product_type": "future",
      "pricing_source": "string",
      "impact_size": 0,
      "initial_margin": 0,
      "maintenance_margin": "string",
      "contract_value": "string",
      "contract_unit_currency": "string",
      "tick_size": "string",
      "trading_status": "operational",
      "max_leverage_notional": "string",
      "default_leverage": "string",
      "initial_margin_scaling_factor": "string",
      "maintenance_margin_scaling_factor": "string",
      "commission_rate": "string",
      "maker_commission_rate": "string",
      "liquidation_penalty_factor": "string",
      "contract_type": "string",
      "position_size_limit": 0,
      "basis_factor_max_limit": "string",
      "is_quanto": true,
      "funding_method": "string",
      "annualized_funding": "string",
      "price_band": "string",
      "underlying_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "quoting_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "settling_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      }
    }
  }
]

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Order](#schemaorder)]|false|none|[An Order object]|

<h2 id="tocSbracketorder">BracketOrder</h2>

<a id="schemabracketorder"></a>

```json
{
  "stop_loss_order": {
    "id": 0,
    "user_id": 0,
    "size": 0,
    "unfilled_size": 0,
    "side": "buy",
    "order_type": "limit_order",
    "limit_price": "string",
    "stop_order_type": "stop_loss_order",
    "stop_price": "string",
    "close_on_trigger": "false",
    "state": "open",
    "created_at": "string",
    "product": {
      "id": 0,
      "symbol": "string",
      "description": "string",
      "created_at": "string",
      "updated_at": "string",
      "settlement_time": "string",
      "product_type": "future",
      "pricing_source": "string",
      "impact_size": 0,
      "initial_margin": 0,
      "maintenance_margin": "string",
      "contract_value": "string",
      "contract_unit_currency": "string",
      "tick_size": "string",
      "trading_status": "operational",
      "max_leverage_notional": "string",
      "default_leverage": "string",
      "initial_margin_scaling_factor": "string",
      "maintenance_margin_scaling_factor": "string",
      "commission_rate": "string",
      "maker_commission_rate": "string",
      "liquidation_penalty_factor": "string",
      "contract_type": "string",
      "position_size_limit": 0,
      "basis_factor_max_limit": "string",
      "is_quanto": true,
      "funding_method": "string",
      "annualized_funding": "string",
      "price_band": "string",
      "underlying_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "quoting_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "settling_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      }
    }
  },
  "take_profit_order": {
    "id": 0,
    "user_id": 0,
    "size": 0,
    "unfilled_size": 0,
    "side": "buy",
    "order_type": "limit_order",
    "limit_price": "string",
    "stop_order_type": "stop_loss_order",
    "stop_price": "string",
    "close_on_trigger": "false",
    "state": "open",
    "created_at": "string",
    "product": {
      "id": 0,
      "symbol": "string",
      "description": "string",
      "created_at": "string",
      "updated_at": "string",
      "settlement_time": "string",
      "product_type": "future",
      "pricing_source": "string",
      "impact_size": 0,
      "initial_margin": 0,
      "maintenance_margin": "string",
      "contract_value": "string",
      "contract_unit_currency": "string",
      "tick_size": "string",
      "trading_status": "operational",
      "max_leverage_notional": "string",
      "default_leverage": "string",
      "initial_margin_scaling_factor": "string",
      "maintenance_margin_scaling_factor": "string",
      "commission_rate": "string",
      "maker_commission_rate": "string",
      "liquidation_penalty_factor": "string",
      "contract_type": "string",
      "position_size_limit": 0,
      "basis_factor_max_limit": "string",
      "is_quanto": true,
      "funding_method": "string",
      "annualized_funding": "string",
      "price_band": "string",
      "underlying_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "quoting_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "settling_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      }
    }
  }
}

```

*__DEPRECATED__*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|stop_loss_order|[Order](#schemaorder)|false|none|An Order object|
|take_profit_order|[Order](#schemaorder)|false|none|An Order object|

<h2 id="tocScreateorderrequest">CreateOrderRequest</h2>

<a id="schemacreateorderrequest"></a>

```json
{
  "product_id": 0,
  "limit_price": "string",
  "size": 0,
  "side": "buy",
  "order_type": "limit_order",
  "time_in_force": "gtc",
  "post_only": "true",
  "reduce_only": "true",
  "bracket_order": {
    "stop_loss_price": "string",
    "take_profit_price": "string",
    "trail_amount": "string"
  }
}

```

*A create order object*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|product_id|integer|false|none|none|
|limit_price|string|false|none|none|
|size|integer|false|none|none|
|side|string|false|none|side for which to place order|
|order_type|string|false|none|none|
|time_in_force|string|false|none|none|
|post_only|string|false|none|none|
|reduce_only|string|false|none|none|
|bracket_order|object|false|none|_DEPRECATED_|
|» stop_loss_price|string|false|none|none|
|» take_profit_price|string|false|none|none|
|» trail_amount|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|side|buy|
|side|sell|
|order_type|limit_order|
|order_type|market_order|
|time_in_force|gtc|
|time_in_force|ioc|
|time_in_force|fok|
|post_only|true|
|post_only|false|
|reduce_only|true|
|reduce_only|false|

<h2 id="tocScreatebracketorderrequest">CreateBracketOrderRequest</h2>

<a id="schemacreatebracketorderrequest"></a>

```json
{
  "product_id": 0,
  "stop_loss_order": {
    "order_type": "market_order",
    "stop_price": "string"
  },
  "take_profit_order": {
    "order_type": "market_order",
    "stop_price": "string"
  }
}

```

*__DEPRECATED__  bracket order object*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|product_id|integer|false|none|none|
|stop_loss_order|object|false|none|none|
|» order_type|string|false|none|none|
|» stop_price|string|false|none|none|
|take_profit_order|object|false|none|none|
|» order_type|string|false|none|none|
|» stop_price|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|order_type|market_order|
|order_type|market_order|

<h2 id="tocSarrayofcreateorderrequest">ArrayOfCreateOrderRequest</h2>

<a id="schemaarrayofcreateorderrequest"></a>

```json
[
  {
    "product_id": 0,
    "limit_price": "string",
    "size": 0,
    "side": "buy",
    "order_type": "limit_order",
    "time_in_force": "gtc",
    "post_only": "true",
    "reduce_only": "true",
    "bracket_order": {
      "stop_loss_price": "string",
      "take_profit_price": "string",
      "trail_amount": "string"
    }
  }
]

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[CreateOrderRequest](#schemacreateorderrequest)]|false|none|[A create order object]|

<h2 id="tocSeditorderrequest">EditOrderRequest</h2>

<a id="schemaeditorderrequest"></a>

```json
{
  "id": 0,
  "product_id": 0,
  "limit_price": "string",
  "size": 0
}

```

*edit order object*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|none|
|product_id|integer|false|none|none|
|limit_price|string|false|none|none|
|size|integer|false|none|total size after editing order|

<h2 id="tocSarrayofeditorderrequest">ArrayOfEditOrderRequest</h2>

<a id="schemaarrayofeditorderrequest"></a>

```json
[
  {
    "id": 0,
    "product_id": 0,
    "limit_price": "string",
    "size": 0
  }
]

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[EditOrderRequest](#schemaeditorderrequest)]|false|none|[edit order object]|

<h2 id="tocSdeleteorderrequest">DeleteOrderRequest</h2>

<a id="schemadeleteorderrequest"></a>

```json
{
  "id": 0,
  "product_id": 0
}

```

*A delete order object*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|none|
|product_id|integer|false|none|none|

<h2 id="tocScancelallfilterobject">CancelAllFilterObject</h2>

<a id="schemacancelallfilterobject"></a>

```json
{
  "product_id": 0,
  "cancel_limit_orders": "true",
  "cancel_stop_orders": "true"
}

```

*Cancel all request filter object*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|product_id|integer|false|none|cancel all orders for particular product, cancels orders for all products if not provided|
|cancel_limit_orders|string|false|none|set as true to cancel open limit orders|
|cancel_stop_orders|string|false|none|set as true to cancel stop orders|

#### Enumerated Values

|Property|Value|
|---|---|
|cancel_limit_orders|true|
|cancel_limit_orders|false|
|cancel_stop_orders|true|
|cancel_stop_orders|false|

<h2 id="tocSarrayofdeleteorderrequest">ArrayOfDeleteOrderRequest</h2>

<a id="schemaarrayofdeleteorderrequest"></a>

```json
[
  {
    "id": 0,
    "product_id": 0
  }
]

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[DeleteOrderRequest](#schemadeleteorderrequest)]|false|none|[A delete order object]|

<h2 id="tocSposition">Position</h2>

<a id="schemaposition"></a>

```json
{
  "user_id": 0,
  "size": 0,
  "entry_price": "string",
  "margin": "string",
  "liquidation_price": "string",
  "bankruptcy_price": "string",
  "adl_level": 0,
  "product": {
    "id": 0,
    "symbol": "string",
    "description": "string",
    "created_at": "string",
    "updated_at": "string",
    "settlement_time": "string",
    "product_type": "future",
    "pricing_source": "string",
    "impact_size": 0,
    "initial_margin": 0,
    "maintenance_margin": "string",
    "contract_value": "string",
    "contract_unit_currency": "string",
    "tick_size": "string",
    "trading_status": "operational",
    "max_leverage_notional": "string",
    "default_leverage": "string",
    "initial_margin_scaling_factor": "string",
    "maintenance_margin_scaling_factor": "string",
    "commission_rate": "string",
    "maker_commission_rate": "string",
    "liquidation_penalty_factor": "string",
    "contract_type": "string",
    "position_size_limit": 0,
    "basis_factor_max_limit": "string",
    "is_quanto": true,
    "funding_method": "string",
    "annualized_funding": "string",
    "price_band": "string",
    "underlying_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    },
    "quoting_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    },
    "settling_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    }
  }
}

```

*A position object*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|user_id|integer|false|none|none|
|size|integer|false|none|Position size, negative for short and positive for long|
|entry_price|string|false|none|none|
|margin|string|false|none|none|
|liquidation_price|string|false|none|none|
|bankruptcy_price|string|false|none|none|
|adl_level|integer|false|none|none|
|product|[Product](#schemaproduct)|false|none|none|

<h2 id="tocSarrayofpositions">ArrayOfPositions</h2>

<a id="schemaarrayofpositions"></a>

```json
[
  {
    "user_id": 0,
    "size": 0,
    "entry_price": "string",
    "margin": "string",
    "liquidation_price": "string",
    "bankruptcy_price": "string",
    "adl_level": 0,
    "product": {
      "id": 0,
      "symbol": "string",
      "description": "string",
      "created_at": "string",
      "updated_at": "string",
      "settlement_time": "string",
      "product_type": "future",
      "pricing_source": "string",
      "impact_size": 0,
      "initial_margin": 0,
      "maintenance_margin": "string",
      "contract_value": "string",
      "contract_unit_currency": "string",
      "tick_size": "string",
      "trading_status": "operational",
      "max_leverage_notional": "string",
      "default_leverage": "string",
      "initial_margin_scaling_factor": "string",
      "maintenance_margin_scaling_factor": "string",
      "commission_rate": "string",
      "maker_commission_rate": "string",
      "liquidation_penalty_factor": "string",
      "contract_type": "string",
      "position_size_limit": 0,
      "basis_factor_max_limit": "string",
      "is_quanto": true,
      "funding_method": "string",
      "annualized_funding": "string",
      "price_band": "string",
      "underlying_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "quoting_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "settling_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      }
    }
  }
]

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Position](#schemaposition)]|false|none|[A position object]|

<h2 id="tocSfill">Fill</h2>

<a id="schemafill"></a>

```json
{
  "id": 0,
  "size": 0,
  "side": "buy",
  "price": "string",
  "role": "taker",
  "commission": "string",
  "created_at": "string",
  "product": {
    "id": 0,
    "symbol": "string",
    "description": "string",
    "created_at": "string",
    "updated_at": "string",
    "settlement_time": "string",
    "product_type": "future",
    "pricing_source": "string",
    "impact_size": 0,
    "initial_margin": 0,
    "maintenance_margin": "string",
    "contract_value": "string",
    "contract_unit_currency": "string",
    "tick_size": "string",
    "trading_status": "operational",
    "max_leverage_notional": "string",
    "default_leverage": "string",
    "initial_margin_scaling_factor": "string",
    "maintenance_margin_scaling_factor": "string",
    "commission_rate": "string",
    "maker_commission_rate": "string",
    "liquidation_penalty_factor": "string",
    "contract_type": "string",
    "position_size_limit": 0,
    "basis_factor_max_limit": "string",
    "is_quanto": true,
    "funding_method": "string",
    "annualized_funding": "string",
    "price_band": "string",
    "underlying_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    },
    "quoting_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    },
    "settling_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    }
  }
}

```

*A fill object*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|none|
|size|integer|false|none|none|
|side|integer|false|none|none|
|price|string|false|none|Price at which the fill happened, BigDecimal sent as string|
|role|string|false|none|none|
|commission|string|false|none|Commission paid on this fill, negative value means commission was earned because of maker role|
|created_at|string|false|none|none|
|product|[Product](#schemaproduct)|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|side|buy|
|side|sell|
|role|taker|
|role|maker|

<h2 id="tocSarrayoffills">ArrayOfFills</h2>

<a id="schemaarrayoffills"></a>

```json
[
  {
    "id": 0,
    "size": 0,
    "side": "buy",
    "price": "string",
    "role": "taker",
    "commission": "string",
    "created_at": "string",
    "product": {
      "id": 0,
      "symbol": "string",
      "description": "string",
      "created_at": "string",
      "updated_at": "string",
      "settlement_time": "string",
      "product_type": "future",
      "pricing_source": "string",
      "impact_size": 0,
      "initial_margin": 0,
      "maintenance_margin": "string",
      "contract_value": "string",
      "contract_unit_currency": "string",
      "tick_size": "string",
      "trading_status": "operational",
      "max_leverage_notional": "string",
      "default_leverage": "string",
      "initial_margin_scaling_factor": "string",
      "maintenance_margin_scaling_factor": "string",
      "commission_rate": "string",
      "maker_commission_rate": "string",
      "liquidation_penalty_factor": "string",
      "contract_type": "string",
      "position_size_limit": 0,
      "basis_factor_max_limit": "string",
      "is_quanto": true,
      "funding_method": "string",
      "annualized_funding": "string",
      "price_band": "string",
      "underlying_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "quoting_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "settling_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      }
    }
  }
]

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Fill](#schemafill)]|false|none|[A fill object]|

<h2 id="tocSorderleverage">OrderLeverage</h2>

<a id="schemaorderleverage"></a>

```json
{
  "leverage": "string",
  "order_margin": "string",
  "product_id": 0
}

```

*Order Leverage for a product*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|leverage|string|false|none|Leverage of all open orders for this product|
|order_margin|string|false|none|Margin blocked in open orders for this product|
|product_id|integer|false|none|none|

<h2 id="tocSl2orderbook">L2Orderbook</h2>

<a id="schemal2orderbook"></a>

```json
{
  "buy_book": [
    {
      "price": "string",
      "size": 0
    }
  ],
  "sell_book": [
    {
      "price": "string",
      "size": 0
    }
  ],
  "recent_trades": [
    {
      "side": "buy",
      "size": 0,
      "price": "string",
      "timestamp": 0
    }
  ],
  "spot_price": "string",
  "mark_price": "string",
  "product_id": 0
}

```

*L2 orderbook*

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|buy_book|[object]|false|none|none|
|» price|string|false|none|none|
|» size|integer|false|none|none|
|sell_book|[object]|false|none|none|
|» price|string|false|none|none|
|» size|integer|false|none|none|
|recent_trades|[object]|false|none|none|
|» side|string|false|none|none|
|» size|integer|false|none|none|
|» price|string|false|none|none|
|» timestamp|integer|false|none|none|
|spot_price|string|false|none|none|
|mark_price|string|false|none|none|
|product_id|integer|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|side|buy|
|side|sell|

<h2 id="tocSwallet">Wallet</h2>

<a id="schemawallet"></a>

```json
{
  "balance": "string",
  "order_margin": "string",
  "position_margin": "string",
  "commission": "string",
  "available_balance": "string",
  "asset": {
    "id": 0,
    "symbol": "string",
    "precision": 0
  }
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|balance|string|false|none|Total wallet balance|
|order_margin|string|false|none|Margin blocked in open orders|
|position_margin|string|false|none|Margin blocked in open positions|
|commission|string|false|none|Commissions blocked in open orders and open positions|
|available_balance|string|false|none|Amount available for withdrawals|
|asset|[Asset](#schemaasset)|false|none|none|

<h2 id="tocSarrayofwallets">ArrayOfWallets</h2>

<a id="schemaarrayofwallets"></a>

```json
[
  {
    "balance": "string",
    "order_margin": "string",
    "position_margin": "string",
    "commission": "string",
    "available_balance": "string",
    "asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    }
  }
]

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Wallet](#schemawallet)]|false|none|none|

<h2 id="tocStransaction">Transaction</h2>

<a id="schematransaction"></a>

```json
{
  "id": 0,
  "amount": "string",
  "balance": "string",
  "transaction_type": "pnl",
  "meta_data": {},
  "product": {
    "id": 0,
    "symbol": "string",
    "description": "string",
    "created_at": "string",
    "updated_at": "string",
    "settlement_time": "string",
    "product_type": "future",
    "pricing_source": "string",
    "impact_size": 0,
    "initial_margin": 0,
    "maintenance_margin": "string",
    "contract_value": "string",
    "contract_unit_currency": "string",
    "tick_size": "string",
    "trading_status": "operational",
    "max_leverage_notional": "string",
    "default_leverage": "string",
    "initial_margin_scaling_factor": "string",
    "maintenance_margin_scaling_factor": "string",
    "commission_rate": "string",
    "maker_commission_rate": "string",
    "liquidation_penalty_factor": "string",
    "contract_type": "string",
    "position_size_limit": 0,
    "basis_factor_max_limit": "string",
    "is_quanto": true,
    "funding_method": "string",
    "annualized_funding": "string",
    "price_band": "string",
    "underlying_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    },
    "quoting_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    },
    "settling_asset": {
      "id": 0,
      "symbol": "string",
      "precision": 0
    }
  },
  "created_at": "string"
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer|false|none|none|
|amount|string|false|none|amount credited/debited in this transaction (+ for credited, - for debited)|
|balance|string|false|none|net wallet balance after this transaction|
|transaction_type|string|false|none|none|
|meta_data|object|false|none|none|
|product|[Product](#schemaproduct)|false|none|none|
|created_at|string|false|none|none|

#### Enumerated Values

|Property|Value|
|---|---|
|transaction_type|pnl|
|transaction_type|deposit|
|transaction_type|withdrawal|
|transaction_type|commission|
|transaction_type|conversion|
|transaction_type|perpetual_futures_funding|
|transaction_type|withdrawal_cancellation|
|transaction_type|referral_bonus|
|transaction_type|commission_rebate|
|transaction_type|promo_credit|

<h2 id="tocSarrayoftransactions">ArrayOfTransactions</h2>

<a id="schemaarrayoftransactions"></a>

```json
[
  {
    "id": 0,
    "amount": "string",
    "balance": "string",
    "transaction_type": "pnl",
    "meta_data": {},
    "product": {
      "id": 0,
      "symbol": "string",
      "description": "string",
      "created_at": "string",
      "updated_at": "string",
      "settlement_time": "string",
      "product_type": "future",
      "pricing_source": "string",
      "impact_size": 0,
      "initial_margin": 0,
      "maintenance_margin": "string",
      "contract_value": "string",
      "contract_unit_currency": "string",
      "tick_size": "string",
      "trading_status": "operational",
      "max_leverage_notional": "string",
      "default_leverage": "string",
      "initial_margin_scaling_factor": "string",
      "maintenance_margin_scaling_factor": "string",
      "commission_rate": "string",
      "maker_commission_rate": "string",
      "liquidation_penalty_factor": "string",
      "contract_type": "string",
      "position_size_limit": 0,
      "basis_factor_max_limit": "string",
      "is_quanto": true,
      "funding_method": "string",
      "annualized_funding": "string",
      "price_band": "string",
      "underlying_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "quoting_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      },
      "settling_asset": {
        "id": 0,
        "symbol": "string",
        "precision": 0
      }
    },
    "created_at": "string"
  }
]

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|*anonymous*|[[Transaction](#schematransaction)]|false|none|none|

<h2 id="tocS24hrticker">24hrTicker</h2>

<a id="schema24hrticker"></a>

```json
{
  "symbol": "string",
  "timestamp": 0,
  "open": 0,
  "high": 0,
  "low": 0,
  "close": 0,
  "volume": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|symbol|string|false|none|none|
|timestamp|integer|false|none|none|
|open|number|false|none|none|
|high|number|false|none|none|
|low|number|false|none|none|
|close|number|false|none|none|
|volume|integer|false|none|none|

<h2 id="tocSohlcdata">OHLCData</h2>

<a id="schemaohlcdata"></a>

```json
{
  "t": [
    0
  ],
  "o": [
    "string"
  ],
  "h": [
    "string"
  ],
  "l": [
    "string"
  ],
  "c": [
    "string"
  ],
  "v": [
    0
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|t|[integer]|false|none|array of timestamps for which candles are returned|
|o|[string]|false|none|open prices for candles|
|h|[string]|false|none|high prices for candles|
|l|[string]|false|none|low prices for candles|
|c|[string]|false|none|close prices for candles|
|v|[integer]|false|none|volumes for candles|

<h2 id="tocSwithdrawalsresponse">WithdrawalsResponse</h2>

<a id="schemawithdrawalsresponse"></a>

```json
{
  "address": "string",
  "amount": "string",
  "fee": "string",
  "id": 0,
  "state": "string",
  "transaction_meta": "string",
  "user_id": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|address|string|false|none|BTC Destination Address|
|amount|string|false|none|Amount to be Withdrawn|
|fee|string|false|none|Withdrawal Fee|
|id|integer(int64)|false|none|Trasaction id|
|state|string|false|none|state of withdrawal request|
|transaction_meta|string|false|none|Amount to be Withdrawn|
|user_id|integer(int64)|false|none|User id|

<h2 id="tocSeditbatchorders">EditBatchOrders</h2>

<a id="schemaeditbatchorders"></a>

```json
{
  "product_id": 0,
  "orders": [
    {
      "id": 0,
      "size": 0,
      "limit_price": "string",
      "product_id": 0
    }
  ]
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|product_id|integer(int32)|true|none|none|
|orders|[[BatchEditOrders](#schemabatcheditorders)]|true|none|none|

<h2 id="tocSbatcheditorders">BatchEditOrders</h2>

<a id="schemabatcheditorders"></a>

```json
{
  "id": 0,
  "size": 0,
  "limit_price": "string",
  "product_id": 0
}

```

### Properties

|Name|Type|Required|Restrictions|Description|
|---|---|---|---|---|
|id|integer(int32)|true|none|Order id to be edited|
|size|integer(int32)|true|none|none|
|limit_price|string|true|none|none|
|product_id|integer(int32)|true|none|none|

