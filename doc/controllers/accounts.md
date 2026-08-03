# Accounts

Head to https://alpaca.markets/docs/api-references/trading-api/account/ to view complete documentation on the Accounts API.

```php
$accountsApi = $client->getAccountsApi();
```

## Class Name

`AccountsApi`


# Get Account

Returns the account associated with the API key.

```php
function getAccount(): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Response Type

**200**: OK

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Account`](../../doc/models/account.md).

## Example Usage

```php
$accountsApi = $client->getAccountsApi();
$apiResponse = $accountsApi->getAccount();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Account:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

