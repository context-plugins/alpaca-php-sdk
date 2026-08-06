
# Client Class Documentation

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| environment | [`Environment`](../README.md#environments) | The API environment. <br> **Default: `Environment.PAPER`** |
| timeout | `int` | Timeout for API calls in seconds.<br>*Default*: `30` |
| enableRetries | `bool` | Whether to enable retries and backoff feature.<br>*Default*: `false` |
| numberOfRetries | `int` | The number of retries to make.<br>*Default*: `0` |
| retryInterval | `float` | The retry time interval between the endpoint calls.<br>*Default*: `1` |
| backOffFactor | `float` | Exponential backoff factor to increase interval between retries.<br>*Default*: `2` |
| maximumRetryWaitTime | `int` | The maximum wait time in seconds for overall retrying requests.<br>*Default*: `0` |
| retryOnTimeout | `bool` | Whether to retry on request timeout.<br>*Default*: `true` |
| httpStatusCodesToRetry | `array` | Http status codes to retry against.<br>*Default*: `408, 413, 429, 500, 502, 503, 504, 521, 522, 524, 408, 413, 429, 500, 502, 503, 504, 521, 522, 524` |
| httpMethodsToRetry | `array` | Http methods to retry against.<br>*Default*: `'GET', 'PUT', 'GET', 'PUT'` |
| loggingConfiguration | [`LoggingConfigurationBuilder`](../doc/logging-configuration-builder.md) | Represents the logging configurations for API calls |
| proxyConfiguration | [`ProxyConfigurationBuilder`](../doc/proxy-configuration-builder.md) | Represents the proxy configurations for API calls |
| apiKeyCredentials | [`ApiKeyCredentials`](auth/custom-header-signature.md) | The Credentials Setter for Custom Header Signature |
| apiSecretCredentials | [`ApiSecretCredentials`](auth/custom-header-signature-1.md) | The Credentials Setter for Custom Header Signature |

The API client can be initialized as follows:

```php
use TraderApiLib\Logging\LoggingConfigurationBuilder;
use TraderApiLib\Logging\RequestLoggingConfigurationBuilder;
use TraderApiLib\Logging\ResponseLoggingConfigurationBuilder;
use Psr\Log\LogLevel;
use TraderApiLib\Environment;
use TraderApiLib\Authentication\ApiKeyCredentialsBuilder;
use TraderApiLib\Authentication\ApiSecretCredentialsBuilder;
use TraderApiLib\TraderApiClientBuilder;

$client = TraderApiClientBuilder::init()
    ->apiKeyCredentials(
        ApiKeyCredentialsBuilder::init(
            'APCA-API-KEY-ID'
        )
    )
    ->apiSecretCredentials(
        ApiSecretCredentialsBuilder::init(
            'APCA-API-SECRET-KEY'
        )
    )
    ->environment(Environment::PAPER)
    ->loggingConfiguration(
        LoggingConfigurationBuilder::init()
            ->level(LogLevel::INFO)
            ->requestConfiguration(RequestLoggingConfigurationBuilder::init()->body(true))
            ->responseConfiguration(ResponseLoggingConfigurationBuilder::init()->headers(true))
    )
    ->build();
```

## Trader API Client

The gateway for the SDK. This class acts as a factory for the Apis and also holds the configuration of the SDK.

## Apis

| Name | Description |
|  --- | --- |
| getAccountsApi() | Gets AccountsApi |
| getOrdersApi() | Gets OrdersApi |
| getPositionsApi() | Gets PositionsApi |
| getPortfolioHistoryApi() | Gets PortfolioHistoryApi |
| getWatchlistsApi() | Gets WatchlistsApi |
| getAccountConfigurationsApi() | Gets AccountConfigurationsApi |
| getAccountActivitiesApi() | Gets AccountActivitiesApi |
| getCalendarApi() | Gets CalendarApi |
| getClockApi() | Gets ClockApi |

