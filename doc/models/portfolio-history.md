
# Portfolio History

*This model accepts additional fields of type array.*

## Structure

`PortfolioHistory`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `timestamp` | `?(int[])` | Optional | time of each data element, left-labeled (the beginning of time window) | getTimestamp(): ?array | setTimestamp(?array timestamp): void |
| `equity` | `?(float[])` | Optional | equity value of the account in dollar amount as of the end of each time window | getEquity(): ?array | setEquity(?array equity): void |
| `profitLoss` | `?(float[])` | Optional | profit/loss in dollar from the base value | getProfitLoss(): ?array | setProfitLoss(?array profitLoss): void |
| `profitLossPct` | `?(float[])` | Optional | profit/loss in percentage from the base value | getProfitLossPct(): ?array | setProfitLossPct(?array profitLossPct): void |
| `baseValue` | `?float` | Optional | basis in dollar of the profit loss calculation | getBaseValue(): ?float | setBaseValue(?float baseValue): void |
| `timeframe` | `?string` | Optional | time window size of each data element | getTimeframe(): ?string | setTimeframe(?string timeframe): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use TraderApiLib\Models\Builders\PortfolioHistoryBuilder;
use TraderApiLib\ApiHelper;

$portfolioHistory = PortfolioHistoryBuilder::init()
    ->timestamp(
        [
            63,
            64,
            65
        ]
    )
    ->equity(
        [
            189.38
        ]
    )
    ->profitLoss(
        [
            40.34
        ]
    )
    ->profitLossPct(
        [
            84.68,
            84.67
        ]
    )
    ->baseValue(39.6)
    ->timeframe('15Min')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

