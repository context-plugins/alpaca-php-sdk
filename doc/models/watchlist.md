
# Watchlist

The watchlist API provides CRUD operation for the account’s watchlist. An account can have multiple watchlists and each is uniquely identified by id but can also be addressed by user-defined name. Each watchlist is an ordered list of assets.

*This model accepts additional fields of type array.*

## Structure

`Watchlist`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `id` | `string` | Required | watchlist id | getId(): string | setId(string id): void |
| `accountId` | `string` | Required | account ID | getAccountId(): string | setAccountId(string accountId): void |
| `createdAt` | `DateTime` | Required | - | getCreatedAt(): \DateTime | setCreatedAt(\DateTime createdAt): void |
| `updatedAt` | `DateTime` | Required | - | getUpdatedAt(): \DateTime | setUpdatedAt(\DateTime updatedAt): void |
| `name` | `string` | Required | user-defined watchlist name (up to 64 characters)<br><br>**Constraints**: *Minimum Length*: `1` | getName(): string | setName(string name): void |
| `assets` | [`?(Assets[])`](../../doc/models/assets.md) | Optional | the content of this watchlist, in the order as registered by the client | getAssets(): ?array | setAssets(?array assets): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use TraderApiLib\Models\Builders\WatchlistBuilder;
use TraderApiLib\Utils\DateTimeHelper;
use TraderApiLib\Models\Builders\AssetsBuilder;
use TraderApiLib\Models\AssetClass;
use TraderApiLib\Models\Exchange;
use TraderApiLib\Models\Status;
use TraderApiLib\ApiHelper;

$watchlist = WatchlistBuilder::init(
    '000013ec-0000-0000-0000-000000000000',
    '00000d90-0000-0000-0000-000000000000',
    DateTimeHelper::fromRfc3339DateTimeRequired('2016-03-13T12:52:32.123Z'),
    DateTimeHelper::fromRfc3339DateTimeRequired('2016-03-13T12:52:32.123Z'),
    'name0'
)
    ->assets(
        [
            AssetsBuilder::init(
                '000004cc-0000-0000-0000-000000000000',
                AssetClass::US_EQUITY,
                Exchange::BATS,
                'symbol0',
                'name8',
                Status::ACTIVE,
                false,
                false,
                false,
                false,
                false
            )
                ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
                ->build()
        ]
    )
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

