# Account Configurations

```php
$accountConfigurationsApi = $client->getAccountConfigurationsApi();
```

## Class Name

`AccountConfigurationsApi`

## Methods

* [Get Account Config](../../doc/controllers/account-configurations.md#get-account-config)
* [Patch Account Config](../../doc/controllers/account-configurations.md#patch-account-config)


# Get Account Config

gets the current account configuration values

```php
function getAccountConfig(): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Response Type

**200**: Successful response

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`AccountConfigurations`](../../doc/models/account-configurations.md).

## Example Usage

```php
$accountConfigurationsApi = $client->getAccountConfigurationsApi();
$apiResponse = $accountConfigurationsApi->getAccountConfig();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'AccountConfigurations:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Patch Account Config

Updates and returns the current account configuration values

```php
function patchAccountConfig(?AccountConfigurations $body = null): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`?AccountConfigurations`](../../doc/models/account-configurations.md) | Body, Optional | - |

## Response Type

**200**: Successful response

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`AccountConfigurations`](../../doc/models/account-configurations.md).

## Example Usage

```php
$body = AccountConfigurationsBuilder::init()
    ->pdtCheck('entry')
    ->build();

$accountConfigurationsApi = $client->getAccountConfigurationsApi();
$apiResponse = $accountConfigurationsApi->patchAccountConfig($body);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'AccountConfigurations:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

