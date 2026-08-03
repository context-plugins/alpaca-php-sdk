# Watchlists

Head to https://alpaca.markets/docs/api-documentation/api-v2/watchlist/ to view complete documentation on the Watchlist API.

```php
$watchlistsApi = $client->getWatchlistsApi();
```

## Class Name

`WatchlistsApi`

## Methods

* [Get Watchlists](../../doc/controllers/watchlists.md#get-watchlists)
* [Post Watchlist](../../doc/controllers/watchlists.md#post-watchlist)
* [Get Watchlist by Id](../../doc/controllers/watchlists.md#get-watchlist-by-id)
* [Update Watchlist by Id](../../doc/controllers/watchlists.md#update-watchlist-by-id)
* [Add Asset to Watchlist](../../doc/controllers/watchlists.md#add-asset-to-watchlist)
* [Delete Watchlist by Id](../../doc/controllers/watchlists.md#delete-watchlist-by-id)
* [Get Watchlist by Name](../../doc/controllers/watchlists.md#get-watchlist-by-name)
* [Update Watchlist by Name](../../doc/controllers/watchlists.md#update-watchlist-by-name)
* [Add Asset to Watchlist by Name](../../doc/controllers/watchlists.md#add-asset-to-watchlist-by-name)
* [Delete Watchlist by Name](../../doc/controllers/watchlists.md#delete-watchlist-by-name)
* [Remove Asset from Watchlist](../../doc/controllers/watchlists.md#remove-asset-from-watchlist)


# Get Watchlists

Returns the list of watchlists registered under the account.

```php
function getWatchlists(): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Response Type

**200**: Successful response

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Watchlist[]`](../../doc/models/watchlist.md).

## Example Usage

```php
$watchlistsApi = $client->getWatchlistsApi();
$apiResponse = $watchlistsApi->getWatchlists();

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Watchlist[]:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

## Example Response *(as JSON)*

```json
[
  {
    "id": "3174d6df-7726-44b4-a5bd-7fda5ae6e009",
    "account_id": "abe25343-a7ba-4255-bdeb-f7e013e9ee5d",
    "created_at": "2022-01-31T21:49:05.14628Z",
    "updated_at": "2022-01-31T21:49:05.14628Z",
    "name": "Primary Watchlist"
  }
]
```


# Post Watchlist

Create a new watchlist with initial set of assets.

```php
function postWatchlist(PostWatchlistRequest $body): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `body` | [`PostWatchlistRequest`](../../doc/models/post-watchlist-request.md) | Body, Required | - |

## Response Type

**200**: Successful response

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Watchlist`](../../doc/models/watchlist.md).

## Example Usage

```php
$body = PostWatchlistRequestBuilder::init(
    'name6'
)->build();

$watchlistsApi = $client->getWatchlistsApi();
$apiResponse = $watchlistsApi->postWatchlist($body);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Watchlist:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Get Watchlist by Id

Returns a watchlist identified by the ID.

```php
function getWatchlistById(string $watchlistId): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `watchlistId` | `string` | Template, Required | watchlist id |

## Response Type

**200**: Successful response

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Watchlist`](../../doc/models/watchlist.md).

## Example Usage

```php
$watchlistId = '00000a1c-0000-0000-0000-000000000000';

$watchlistsApi = $client->getWatchlistsApi();
$apiResponse = $watchlistsApi->getWatchlistById($watchlistId);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Watchlist:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Update Watchlist by Id

Update the name and/or content of watchlist

```php
function updateWatchlistById(string $watchlistId, ?PostWatchlistRequest $body = null): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `watchlistId` | `string` | Template, Required | watchlist id |
| `body` | [`?PostWatchlistRequest`](../../doc/models/post-watchlist-request.md) | Body, Optional | - |

## Response Type

**200**: Successful response

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Watchlist`](../../doc/models/watchlist.md).

## Example Usage

```php
$watchlistId = '00000a1c-0000-0000-0000-000000000000';

$watchlistsApi = $client->getWatchlistsApi();
$apiResponse = $watchlistsApi->updateWatchlistById($watchlistId);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Watchlist:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Add Asset to Watchlist

Append an asset for the symbol to the end of watchlist asset list

```php
function addAssetToWatchlist(string $watchlistId, ?AddAssetToWatchlistRequest $body = null): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `watchlistId` | `string` | Template, Required | watchlist id |
| `body` | [`?AddAssetToWatchlistRequest`](../../doc/models/add-asset-to-watchlist-request.md) | Body, Optional | - |

## Response Type

**200**: Successful response

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Watchlist`](../../doc/models/watchlist.md).

## Example Usage

```php
$watchlistId = '00000a1c-0000-0000-0000-000000000000';

$body = AddAssetToWatchlistRequestBuilder::init()
    ->symbol('AAPL')
    ->build();

$watchlistsApi = $client->getWatchlistsApi();
$apiResponse = $watchlistsApi->addAssetToWatchlist(
    $watchlistId,
    $body
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Watchlist:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Delete Watchlist by Id

Delete a watchlist. This is a permanent deletion.

```php
function deleteWatchlistById(string $watchlistId): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `watchlistId` | `string` | Template, Required | watchlist id |

## Response Type

**204**: No Content

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$watchlistId = '00000a1c-0000-0000-0000-000000000000';

$watchlistsApi = $client->getWatchlistsApi();
$apiResponse = $watchlistsApi->deleteWatchlistById($watchlistId);

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


# Get Watchlist by Name

Returns a watchlist by name

```php
function getWatchlistByName(string $name): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `name` | `string` | Query, Required | name of the watchlist |

## Response Type

**200**: Successful response

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Watchlist`](../../doc/models/watchlist.md).

## Example Usage

```php
$name = 'name0';

$watchlistsApi = $client->getWatchlistsApi();
$apiResponse = $watchlistsApi->getWatchlistByName($name);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Watchlist:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Update Watchlist by Name

Update the name and/or content of watchlist

```php
function updateWatchlistByName(string $name, ?PostWatchlistRequest $body = null): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `name` | `string` | Query, Required | name of the watchlist |
| `body` | [`?PostWatchlistRequest`](../../doc/models/post-watchlist-request.md) | Body, Optional | - |

## Response Type

**200**: Successful response

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Watchlist`](../../doc/models/watchlist.md).

## Example Usage

```php
$name = 'name0';

$watchlistsApi = $client->getWatchlistsApi();
$apiResponse = $watchlistsApi->updateWatchlistByName($name);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Watchlist:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Add Asset to Watchlist by Name

Append an asset for the symbol to the end of watchlist asset list

```php
function addAssetToWatchlistByName(string $name, ?AddAssetToWatchlistRequest $body = null): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `name` | `string` | Query, Required | name of the watchlist |
| `body` | [`?AddAssetToWatchlistRequest`](../../doc/models/add-asset-to-watchlist-request.md) | Body, Optional | - |

## Response Type

**200**: Successful response

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Watchlist`](../../doc/models/watchlist.md).

## Example Usage

```php
$name = 'name0';

$body = AddAssetToWatchlistRequestBuilder::init()
    ->symbol('AAPL')
    ->build();

$watchlistsApi = $client->getWatchlistsApi();
$apiResponse = $watchlistsApi->addAssetToWatchlistByName(
    $name,
    $body
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Watchlist:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```


# Delete Watchlist by Name

Delete a watchlist. This is a permanent deletion.

```php
function deleteWatchlistByName(string $name): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `name` | `string` | Query, Required | name of the watchlist |

## Response Type

**204**: No Content

This method returns an [`ApiResponse`](../../doc/api-response.md) instance.

## Example Usage

```php
$name = 'name0';

$watchlistsApi = $client->getWatchlistsApi();
$apiResponse = $watchlistsApi->deleteWatchlistByName($name);

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


# Remove Asset from Watchlist

Delete one entry for an asset by symbol name

```php
function removeAssetFromWatchlist(string $watchlistId, string $symbol): ApiResponse
```

## Authentication

This endpoint requires [API_Key](../../doc/auth/custom-header-signature.md) **AND** [API_Secret](../../doc/auth/custom-header-signature-1.md)

## Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `watchlistId` | `string` | Template, Required | Watchlist ID |
| `symbol` | `string` | Template, Required | symbol name to remove from the watchlist content |

## Response Type

**200**: Returns the updated watchlist

This method returns an [`ApiResponse`](../../doc/api-response.md) instance. The `getResult()` method on this instance returns the response data which is of type [`Watchlist`](../../doc/models/watchlist.md).

## Example Usage

```php
$watchlistId = '00000a1c-0000-0000-0000-000000000000';

$symbol = 'symbol8';

$watchlistsApi = $client->getWatchlistsApi();
$apiResponse = $watchlistsApi->removeAssetFromWatchlist(
    $watchlistId,
    $symbol
);

// Extracting response status code
var_dump($apiResponse->getStatusCode());
// Extracting response headers
var_dump($apiResponse->getHeaders());

if ($apiResponse->isSuccess()) {
    echo 'Watchlist:';
    var_dump($apiResponse->getResult());
} else {
    $error = $apiResponse->getResult();
    var_dump($error);
}
```

