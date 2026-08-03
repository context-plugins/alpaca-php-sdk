# Account Activities

```php
$accountActivitiesApi = $client->getAccountActivitiesApi();
```

## Class Name

`AccountActivitiesApi`

## Methods

* [Get Account Activities](../../doc/controllers/account-activities.md#get-account-activities)
* [Get Account Activities by Activity Type](../../doc/controllers/account-activities.md#get-account-activities-by-activity-type)


# Get Account Activities

Returns account activity entries for many types of activities.

```php
function getAccountActivities(
    ?\DateTime $date = null,
    ?\DateTime $until = null,
    ?\DateTime $after = null,
    ?string $direction = null,
    ?int $pageSize = null,
    ?string $pageToken = null,
    ?string $activityTypes = null
): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `date` | `?DateTime` | Query, Optional | The date for which you want to see activities. |
| `until` | `?DateTime` | Query, Optional | The response will contain only activities submitted before this date. (Cannot be used with date.) |
| `after` | `?DateTime` | Query, Optional | The response will contain only activities submitted after this date. (Cannot be used with date.) |
| `direction` | [`?string(Direction)`](../../doc/models/direction.md) | Query, Optional | asc or desc (default desc if unspecified.) |
| `pageSize` | `?int` | Query, Optional | The maximum number of entries to return in the response. (See the section on paging above.) |
| `pageToken` | `?string` | Query, Optional | The ID of the end of your current page of results. |
| `activityTypes` | `?string` | Query, Optional | A comma-separated list of the activity types to include in the response. If unspecified, activities of all types will be returned. See ActivityType model for values |

## Response Type

**200**: returns an array of Account activities

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type `array<AccountTradingActivities|AccountNonTradeActivities>`.

## Example Usage

```php
$direction = Direction::DESC;

$activityTypes = 'FILL';

$accountActivitiesApi = $client->getAccountActivitiesApi();
$apiResponse = $accountActivitiesApi->getAccountActivities(
    null,
    null,
    null,
    $direction,
    null,
    null,
    $activityTypes
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'array<AccountTradingActivities|AccountNonTradeActivities>:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Get Account Activities by Activity Type

Returns account activity entries for a specific type of activity.

```php
function getAccountActivitiesByActivityType(
    string $activityType,
    ?\DateTime $date = null,
    ?\DateTime $until = null,
    ?\DateTime $after = null,
    ?string $direction = null,
    ?int $pageSize = null,
    ?string $pageToken = null
): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `activityType` | `string` | Template, Required | The activity type you want to view entries for. A list of valid activity types can be found at the bottom of this page. |
| `date` | `?DateTime` | Query, Optional | The date for which you want to see activities. |
| `until` | `?DateTime` | Query, Optional | The response will contain only activities submitted before this date. (Cannot be used with date.) |
| `after` | `?DateTime` | Query, Optional | The response will contain only activities submitted after this date. (Cannot be used with date.) |
| `direction` | [`?string(Direction)`](../../doc/models/direction.md) | Query, Optional | asc or desc (default desc if unspecified.) |
| `pageSize` | `?int` | Query, Optional | The maximum number of entries to return in the response. (See the section on paging above.) |
| `pageToken` | `?string` | Query, Optional | The ID of the end of your current page of results. |

## Response Type

**200**: returns an array of Account activities

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type `array<AccountTradingActivities|AccountNonTradeActivities>`.

## Example Usage

```php
$activityType = 'activity_type2';

$direction = Direction::DESC;

$accountActivitiesApi = $client->getAccountActivitiesApi();
$apiResponse = $accountActivitiesApi->getAccountActivitiesByActivityType(
    $activityType,
    null,
    null,
    null,
    $direction
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'array<AccountTradingActivities|AccountNonTradeActivities>:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

