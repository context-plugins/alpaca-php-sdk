
# Custom Header Signature



Documentation for accessing and setting credentials for API_Key.

## Auth Credentials

| Name | Type | Description | Setter | Getter |
|  --- | --- | --- | --- | --- |
| APCA-API-KEY-ID | `string` | - | `apcaApiKeyId` | `getApcaApiKeyId()` |



**Note:** Auth credentials can be set using `ApiKeyCredentialsBuilder::init()` in `apiKeyCredentials` method in the client builder and accessed through `getApiKeyCredentials` method in the client instance.

## Usage Example

### Client Initialization

You must provide credentials in the client as shown in the following code snippet.

```php
use TraderApiLib\Authentication\ApiKeyCredentialsBuilder;
use TraderApiLib\TraderApiClientBuilder;

$client = TraderApiClientBuilder::init()
    ->apiKeyCredentials(
        ApiKeyCredentialsBuilder::init(
            'APCA-API-KEY-ID'
        )
    )
    ->build();
```


