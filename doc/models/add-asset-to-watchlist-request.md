
# Add Asset to Watchlist Request

Append an asset for the symbol to the end of watchlist asset list

*This model accepts additional fields of type array.*

## Structure

`AddAssetToWatchlistRequest`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `symbol` | `?string` | Optional | symbol name to append to watchlist | getSymbol(): ?string | setSymbol(?string symbol): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use TraderApiLib\Models\Builders\AddAssetToWatchlistRequestBuilder;
use TraderApiLib\ApiHelper;

$addAssetToWatchlistRequest = AddAssetToWatchlistRequestBuilder::init()
    ->symbol('AAPL')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

