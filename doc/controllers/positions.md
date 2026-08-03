# Positions

Head to https://alpaca.markets/docs/api-documentation/api-v2/positions/ to view complete documentation on the Positions API.

```php
$positionsApi = $client->getPositionsApi();
```

## Class Name

`PositionsApi`

## Methods

* [Get All Open Positions](../../doc/controllers/positions.md#get-all-open-positions)
* [Delete All Open Positions](../../doc/controllers/positions.md#delete-all-open-positions)
* [Get Open Position](../../doc/controllers/positions.md#get-open-position)
* [Delete Open Position](../../doc/controllers/positions.md#delete-open-position)


# Get All Open Positions

The positions API provides information about an account’s current open positions. The response will include information such as cost basis, shares traded, and market value, which will be updated live as price information is updated. Once a position is closed, it will no longer be queryable through this API

Retrieves a list of the account’s open positions

```php
function getAllOpenPositions(): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Response Type

**200**: Successful response

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Position[]`](../../doc/models/position.md).

## Example Usage

```php
$positionsApi = $client->getPositionsApi();
$apiResponse = $positionsApi->getAllOpenPositions();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Position[]:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Delete All Open Positions

Closes (liquidates) all of the account’s open long and short positions. A response will be provided for each order that is attempted to be cancelled. If an order is no longer cancelable, the server will respond with status 500 and reject the request.

```php
function deleteAllOpenPositions(?bool $cancelOrders = null): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `cancelOrders` | `?bool` | Query, Optional | If true is specified, cancel all open orders before liquidating all positions. |

## Response Type

**207**: Multi-Status with body.

an array of PositionClosed responses

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`PositionClosedReponse[]`](../../doc/models/position-closed-reponse.md).

## Example Usage

```php
$positionsApi = $client->getPositionsApi();
$apiResponse = $positionsApi->deleteAllOpenPositions();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'PositionClosedReponse[]:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Errors

| HTTP Status Code | Error Description | Exception Class |
|  --- | --- | --- |
| 500 | Failed to liquidate | `ApiException` |


# Get Open Position

Retrieves the account’s open position for the given symbol or assetId.

```php
function getOpenPosition(string $symbolOrAssetId): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `symbolOrAssetId` | `string` | Template, Required | symbol or assetId |

## Response Type

**200**: Successful response

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Position`](../../doc/models/position.md).

## Example Usage

```php
$symbolOrAssetId = 'symbol_or_asset_id8';

$positionsApi = $client->getPositionsApi();
$apiResponse = $positionsApi->getOpenPosition($symbolOrAssetId);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Position:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Delete Open Position

Closes (liquidates) the account’s open position for the given symbol. Works for both long and short positions.

```php
function deleteOpenPosition(string $symbolOrAssetId, ?float $qty = null, ?float $percentage = null): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `symbolOrAssetId` | `string` | Template, Required | symbol or assetId |
| `qty` | `?float` | Query, Optional | the number of shares to liquidate. Can accept up to 9 decimal points. Cannot work with percentage |
| `percentage` | `?float` | Query, Optional | percentage of position to liquidate. Must be between 0 and 100. Would only sell fractional if position is originally fractional. Can accept up to 9 decimal points. Cannot work with qty |

## Response Type

**200**: Successful response

Returns the order created to close out this position

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Order`](../../doc/models/order.md).

## Example Usage

```php
$symbolOrAssetId = 'symbol_or_asset_id8';

$positionsApi = $client->getPositionsApi();
$apiResponse = $positionsApi->deleteOpenPosition($symbolOrAssetId);

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

