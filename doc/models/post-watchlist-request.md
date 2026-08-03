
# Post Watchlist Request

Request format used for creating a new watchlist or updating an existing watchlist with a set of assets and name.

*This model accepts additional fields of type array.*

## Structure

`PostWatchlistRequest`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `name` | `string` | Required | - | getName(): string | setName(string name): void |
| `symbols` | `?(array<?string>)` | Optional | - | getSymbols(): ?array | setSymbols(?array symbols): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use TraderApiLib\Models\Builders\PostWatchlistRequestBuilder;
use TraderApiLib\ApiHelper;

$postWatchlistRequest = PostWatchlistRequestBuilder::init(
    'name2'
)
    ->symbols(
        [
            'symbols1',
            'symbols2'
        ]
    )
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

