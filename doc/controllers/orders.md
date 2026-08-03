# Orders

Head to https://alpaca.markets/docs/api-documentation/api-v2/orders/ to view complete documentation on the Orders API.

```php
$ordersApi = $client->getOrdersApi();
```

## Class Name

`OrdersApi`

## Methods

* [Post Order](../../doc/controllers/orders.md#post-order)
* [Get All Orders](../../doc/controllers/orders.md#get-all-orders)
* [Delete All Orders](../../doc/controllers/orders.md#delete-all-orders)
* [Get Order by Order ID](../../doc/controllers/orders.md#get-order-by-order-id)
* [Patch Order by Order Id](../../doc/controllers/orders.md#patch-order-by-order-id)
* [Delete Order by Order ID](../../doc/controllers/orders.md#delete-order-by-order-id)


# Post Order

Places a new order for the given account. An order request may be rejected if the account is not authorized for trading, or if the tradable balance is insufficient to fill the order..

```php
function postOrder(Order $body): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`Order`](../../doc/models/order.md) | Body, Required | - |

## Response Type

**200**: Successful response

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Order`](../../doc/models/order.md).

## Example Usage

```php
$body = OrderBuilder::init(
    'symbol2',
    OrderType::STOP,
    OrderSide::BUY,
    TimeInForce::DAY
)
    ->assetClass(AssetClass::US_EQUITY)
    ->notional('notional2')
    ->qty('qty2')
    ->orderClass(OrderClass::BRACKET)
    ->status(OrderStatus::NEW_)
    ->build();

$ordersApi = $client->getOrdersApi();
$apiResponse = $ordersApi->postOrder($body);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Order:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 403 | Forbidden<br><br>Buying power or shares is not sufficient. | `ApiException` |
| 422 | Unprocessable<br><br>Input parameters are not recognized. | `ApiException` |


# Get All Orders

Retrieves a list of orders for the account, filtered by the supplied query parameters.

```php
function getAllOrders(
    ?string $status = null,
    ?int $limit = null,
    ?string $after = null,
    ?string $until = null,
    ?string $direction = null,
    ?bool $nested = null,
    ?string $symbols = null
): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `status` | [`?string(Status1)`](../../doc/models/status-1.md) | Query, Optional | Order status to be queried. open, closed or all. Defaults to open. |
| `limit` | `?int` | Query, Optional | The maximum number of orders in response. Defaults to 50 and max is 500. |
| `after` | `?string` | Query, Optional | The response will include only ones submitted after this timestamp (exclusive.) |
| `until` | `?string` | Query, Optional | The response will include only ones submitted until this timestamp (exclusive.) |
| `direction` | [`?string(Direction)`](../../doc/models/direction.md) | Query, Optional | The chronological order of response based on the submission time. asc or desc. Defaults to desc. |
| `nested` | `?bool` | Query, Optional | If true, the result will roll up multi-leg orders under the legs field of primary order. |
| `symbols` | `?string` | Query, Optional | A comma-separated list of symbols to filter by (ex. “AAPL,TSLA,MSFT”). A currency pair is required for crypto orders (ex. “BTCUSD,BCHUSD,LTCUSD,ETCUSD”). |

## Response Type

**200**: Successful response

An array of Order objects

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Order[]`](../../doc/models/order.md).

## Example Usage

```php
$status = Status1::OPEN;

$ordersApi = $client->getOrdersApi();
$apiResponse = $ordersApi->getAllOrders($status);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Order[]:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Delete All Orders

Attempts to cancel all open orders. A response will be provided for each order that is attempted to be cancelled. If an order is no longer cancelable, the server will respond with status 500 and reject the request.

```php
function deleteAllOrders(): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Response Type

**207**: Multi-Status with body.

an array of objects that include the order id and http status code for each status request.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`CanceledOrderResponse[]`](../../doc/models/canceled-order-response.md).

## Example Usage

```php
$ordersApi = $client->getOrdersApi();
$apiResponse = $ordersApi->deleteAllOrders();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'CanceledOrderResponse[]:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 500 | Failed to cancel order. | `ApiException` |


# Get Order by Order ID

Retrieves a single order for the given order_id.

```php
function getOrderByOrderId(string $orderId, ?bool $nested = null): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `orderId` | `string` | Template, Required | order id |
| `nested` | `?bool` | Query, Optional | If true, the result will roll up multi-leg orders under the legs field of primary order. |

## Response Type

**200**: Successful response

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Order`](../../doc/models/order.md).

## Example Usage

```php
$orderId = '00001a1e-0000-0000-0000-000000000000';

$ordersApi = $client->getOrdersApi();
$apiResponse = $ordersApi->getOrderByOrderId($orderId);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Order:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Patch Order by Order Id

Replaces a single order with updated parameters. Each parameter overrides the corresponding attribute of the existing order. The other attributes remain the same as the existing order.

A success return code from a replaced order does NOT guarantee the existing open order has been replaced. If the existing open order is filled before the replacing (new) order reaches the execution venue, the replacing (new) order is rejected, and these events are sent in the trade_updates stream channel.

While an order is being replaced, buying power is reduced by the larger of the two orders that have been placed (the old order being replaced, and the newly placed order to replace it). If you are replacing a buy entry order with a higher limit price than the original order, the buying power is calculated based on the newly placed order. If you are replacing it with a lower limit price, the buying power is calculated based on the old order.

```php
function patchOrderByOrderId(string $orderId, PatchOrderRequest $body): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `orderId` | `string` | Template, Required | order id |
| `body` | [`PatchOrderRequest`](../../doc/models/patch-order-request.md) | Body, Required | - |

## Response Type

**200**: Successful response

The new Order object with the new order ID.

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Order`](../../doc/models/order.md).

## Example Usage

```php
$orderId = '00001a1e-0000-0000-0000-000000000000';

$body = PatchOrderRequestBuilder::init()
    ->timeInForce(TimeInForce::DAY)
    ->build();

$ordersApi = $client->getOrdersApi();
$apiResponse = $ordersApi->patchOrderByOrderId(
    $orderId,
    $body
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Order:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Delete Order by Order ID

Attempts to cancel an Open Order. If the order is no longer cancelable, the request will be rejected with status 422; otherwise accepted with return status 204.

```php
function deleteOrderByOrderId(string $orderId): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `orderId` | `string` | Template, Required | order id |

## Response Type

**204**: No Content

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$orderId = '00001a1e-0000-0000-0000-000000000000';

$ordersApi = $client->getOrdersApi();
$apiResponse = $ordersApi->deleteOrderByOrderId($orderId);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'void:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 422 | The order status is not cancelable. | `ApiException` |

