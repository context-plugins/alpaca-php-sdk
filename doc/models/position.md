
# Position

The positions API provides information about an account’s current open positions. The response will include information such as cost basis, shares traded, and market value, which will be updated live as price information is updated. Once a position is closed, it will no longer be queryable through this API.

*This model accepts additional fields of type array.*

## Structure

`Position`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `assetId` | `string` | Required | Asset ID | getAssetId(): string | setAssetId(string assetId): void |
| `symbol` | `string` | Required | Symbol name of the asset | getSymbol(): string | setSymbol(string symbol): void |
| `exchange` | [`string(Exchange)`](../../doc/models/exchange.md) | Required | Represents the current exchanges Alpaca supports. List is currently:<br><br>- AMEX<br>- ARCA<br>- BATS<br>- NYSE<br>- NASDAQ<br>- NYSEARCA<br>- OTC | getExchange(): string | setExchange(string exchange): void |
| `assetClass` | [`string(AssetClass)`](../../doc/models/asset-class.md) | Required | Represents what class of asset this is. Currently only supports `us_equity` or `crypto` | getAssetClass(): string | setAssetClass(string assetClass): void |
| `avgEntryPrice` | `string` | Required | Average entry price of the position<br><br>**Constraints**: *Minimum Length*: `1` | getAvgEntryPrice(): string | setAvgEntryPrice(string avgEntryPrice): void |
| `qty` | `string` | Required | The number of shares<br><br>**Constraints**: *Minimum Length*: `1` | getQty(): string | setQty(string qty): void |
| `qtyAvailable` | `?string` | Optional | Total number of shares available minus open orders<br><br>**Constraints**: *Minimum Length*: `1` | getQtyAvailable(): ?string | setQtyAvailable(?string qtyAvailable): void |
| `side` | `string` | Required | “long”<br><br>**Constraints**: *Minimum Length*: `1` | getSide(): string | setSide(string side): void |
| `marketValue` | `string` | Required | Total dollar amount of the position<br><br>**Constraints**: *Minimum Length*: `1` | getMarketValue(): string | setMarketValue(string marketValue): void |
| `costBasis` | `string` | Required | Total cost basis in dollar<br><br>**Constraints**: *Minimum Length*: `1` | getCostBasis(): string | setCostBasis(string costBasis): void |
| `unrealizedPl` | `string` | Required | Unrealized profit/loss in dollars<br><br>**Constraints**: *Minimum Length*: `1` | getUnrealizedPl(): string | setUnrealizedPl(string unrealizedPl): void |
| `unrealizedPlpc` | `string` | Required | Unrealized profit/loss percent (by a factor of 1)<br><br>**Constraints**: *Minimum Length*: `1` | getUnrealizedPlpc(): string | setUnrealizedPlpc(string unrealizedPlpc): void |
| `unrealizedIntradayPl` | `string` | Required | Unrealized profit/loss in dollars for the day<br><br>**Constraints**: *Minimum Length*: `1` | getUnrealizedIntradayPl(): string | setUnrealizedIntradayPl(string unrealizedIntradayPl): void |
| `unrealizedIntradayPlpc` | `string` | Required | Unrealized profit/loss percent (by a factor of 1)<br><br>**Constraints**: *Minimum Length*: `1` | getUnrealizedIntradayPlpc(): string | setUnrealizedIntradayPlpc(string unrealizedIntradayPlpc): void |
| `currentPrice` | `string` | Required | Current asset price per share<br><br>**Constraints**: *Minimum Length*: `1` | getCurrentPrice(): string | setCurrentPrice(string currentPrice): void |
| `lastdayPrice` | `string` | Required | Last day’s asset price per share based on the closing value of the last trading day<br><br>**Constraints**: *Minimum Length*: `1` | getLastdayPrice(): string | setLastdayPrice(string lastdayPrice): void |
| `changeToday` | `string` | Required | Percent change from last day price (by a factor of 1)<br><br>**Constraints**: *Minimum Length*: `1` | getChangeToday(): string | setChangeToday(string changeToday): void |
| `assetMarginable` | `bool` | Required | - | getAssetMarginable(): bool | setAssetMarginable(bool assetMarginable): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use TraderApiLib\Models\Builders\PositionBuilder;
use TraderApiLib\Models\Exchange;
use TraderApiLib\Models\AssetClass;
use TraderApiLib\ApiHelper;

$position = PositionBuilder::init(
    '00001420-0000-0000-0000-000000000000',
    'AAPL',
    Exchange::NYSE,
    AssetClass::US_EQUITY,
    'avg_entry_price6',
    'qty2',
    'side4',
    'market_value4',
    'cost_basis4',
    'unrealized_pl4',
    'unrealized_plpc8',
    'unrealized_intraday_pl0',
    'unrealized_intraday_plpc6',
    'current_price2',
    'lastday_price2',
    'change_today8',
    false
)
    ->qtyAvailable('qty_available4')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

