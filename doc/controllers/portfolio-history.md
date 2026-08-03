# Portfolio History

```php
$portfolioHistoryApi = $client->getPortfolioHistoryApi();
```

## Class Name

`PortfolioHistoryApi`


# Get Account Portfolio History

Returns timeseries data about equity and profit/loss (P/L) of the account in requested timespan.

```php
function getAccountPortfolioHistory(
    ?string $period = null,
    ?string $timeframe = null,
    ?\DateTime $dateEnd = null,
    ?string $extendedHours = null
): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `period` | `?string` | Query, Optional | The duration of the data in <number> + <unit>, such as 1D, where <unit> can be D for day, W for week, M for month and A for year. Defaults to 1M. |
| `timeframe` | `?string` | Query, Optional | The resolution of time window. 1Min, 5Min, 15Min, 1H, or 1D. If omitted, 1Min for less than 7 days period, 15Min for less than 30 days, or otherwise 1D. |
| `dateEnd` | `?DateTime` | Query, Optional | The date the data is returned up to, in “YYYY-MM-DD” format. Defaults to the current market date (rolls over at the market open if extended_hours is false, otherwise at 7am ET) |
| `extendedHours` | `?string` | Query, Optional | If true, include extended hours in the result. This is effective only for timeframe less than 1D. |

## Response Type

**200**: Successful response

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`PortfolioHistory`](../../doc/models/portfolio-history.md).

## Example Usage

```php
$dateEnd = DateTimeHelper::fromSimpleDate('2022-05-15');

$portfolioHistoryApi = $client->getPortfolioHistoryApi();
$apiResponse = $portfolioHistoryApi->getAccountPortfolioHistory(
    null,
    null,
    $dateEnd
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'PortfolioHistory:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

