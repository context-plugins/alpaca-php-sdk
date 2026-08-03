# Clock

Head to https://alpaca.markets/docs/api-references/trading-api/clock/ to view complete documentation on the Market Clock API.

```php
$clockApi = $client->getClockApi();
```

## Class Name

`ClockApi`


# Get Clock

The clock API serves the current market timestamp, whether or not the market is currently open, as well as the times of the next market open and close.

Returns the market clock.

```php
function getClock(): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Clock`](../../doc/models/clock.md).

## Example Usage

```php
$clockApi = $client->getClockApi();
$apiResponse = $clockApi->getClock();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Clock:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

