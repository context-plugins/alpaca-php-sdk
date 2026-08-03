
# Assets

The assets API serves as the master list of assets available for trade and data consumption from Alpaca. Assets are sorted by asset class, exchange and symbol. Some assets are only available for data consumption via Polygon, and are not tradable with Alpaca. These assets will be marked with the flag tradable=false.

*This model accepts additional fields of type array.*

## Structure

`Assets`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `id` | `string` | Required | Asset ID | getId(): string | setId(string id): void |
| `class` | [`string(AssetClass)`](../../doc/models/asset-class.md) | Required | Represents what class of asset this is. Currently only supports `us_equity` or `crypto` | getClass(): string | setClass(string class): void |
| `exchange` | [`string(Exchange)`](../../doc/models/exchange.md) | Required | Represents the current exchanges Alpaca supports. List is currently:<br><br>- AMEX<br>- ARCA<br>- BATS<br>- NYSE<br>- NASDAQ<br>- NYSEARCA<br>- OTC | getExchange(): string | setExchange(string exchange): void |
| `symbol` | `string` | Required | The symbol of the asset | getSymbol(): string | setSymbol(string symbol): void |
| `name` | `string` | Required | The official name of the asset<br><br>**Constraints**: *Minimum Length*: `1` | getName(): string | setName(string name): void |
| `status` | [`string(Status)`](../../doc/models/status.md) | Required | active or inactive | getStatus(): string | setStatus(string status): void |
| `tradable` | `bool` | Required | Asset is tradable on Alpaca or not | getTradable(): bool | setTradable(bool tradable): void |
| `marginable` | `bool` | Required | Asset is marginable or not | getMarginable(): bool | setMarginable(bool marginable): void |
| `shortable` | `bool` | Required | Asset is shortable or not | getShortable(): bool | setShortable(bool shortable): void |
| `easyToBorrow` | `bool` | Required | Asset is easy-to-borrow or not (filtering for easy_to_borrow = True is the best way to check whether the name is currently available to short at Alpaca). | getEasyToBorrow(): bool | setEasyToBorrow(bool easyToBorrow): void |
| `fractionable` | `bool` | Required | Asset is fractionable or not | getFractionable(): bool | setFractionable(bool fractionable): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use TraderApiLib\Models\Builders\AssetsBuilder;
use TraderApiLib\Models\AssetClass;
use TraderApiLib\Models\Exchange;
use TraderApiLib\Models\Status;
use TraderApiLib\ApiHelper;

$assets = AssetsBuilder::init(
    '000004cc-0000-0000-0000-000000000000',
    AssetClass::US_EQUITY,
    Exchange::NYSE,
    'AAPL',
    'name8',
    Status::ACTIVE,
    false,
    false,
    false,
    false,
    false
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

