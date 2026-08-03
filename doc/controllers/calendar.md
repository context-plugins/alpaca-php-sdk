# Calendar

Head to https://alpaca.markets/docs/api-references/trading-api/calendar/ to view complete documentation on the Market Calendar API.

```php
$calendarApi = $client->getCalendarApi();
```

## Class Name

`CalendarApi`


# Get Calendar

Returns the market calendar.

```php
function getCalendar(?\DateTime $start = null, ?\DateTime $end = null): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `start` | `?DateTime` | Query, Optional | The first date to retrieve data for (inclusive) |
| `end` | `?DateTime` | Query, Optional | The last date to retrieve data for (inclusive) |

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Calendar[]`](../../doc/models/calendar.md).

## Example Usage

```php
$calendarApi = $client->getCalendarApi();
$apiResponse = $calendarApi->getCalendar();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Calendar[]:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

