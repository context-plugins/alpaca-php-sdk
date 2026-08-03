
# Custom Header Signature



Documentation for accessing and setting credentials for API_Secret.

## Auth Credentials

| Name | Type | Description | Setter | Getter |
|  --- | --- | --- | --- | --- |
| APCA-API-SECRET-KEY | `string` | - | `apcaApiSecretKey` | `getApcaApiSecretKey()` |



**Note:** Auth credentials can be set using `ApiSecretCredentialsBuilder::init()` in `apiSecretCredentials` method in the client builder and accessed through `getApiSecretCredentials` method in the client instance.

## Usage Example

### Client Initialization

You must provide credentials in the client as shown in the following code snippet.

```php
use TraderApiLib\Authentication\ApiSecretCredentialsBuilder;
use TraderApiLib\TraderApiClientBuilder;

$client = TraderApiClientBuilder::init()
    ->apiSecretCredentials(
        ApiSecretCredentialsBuilder::init(
            'APCA-API-SECRET-KEY'
        )
    )
    ->build();
```


