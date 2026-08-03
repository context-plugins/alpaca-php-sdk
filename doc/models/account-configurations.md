
# Account Configurations

The account configuration API provides custom configurations about your trading account settings. These configurations control various allow you to modify settings to suit your trading needs.

*This model accepts additional fields of type array.*

## Structure

`AccountConfigurations`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `dtbpCheck` | [`?string(DtbpCheck)`](../../doc/models/dtbp-check.md) | Optional | both, entry, or exit. Controls Day Trading Margin Call (DTMC) checks. | getDtbpCheck(): ?string | setDtbpCheck(?string dtbpCheck): void |
| `tradeConfirmEmail` | `?string` | Optional | all or none. If none, emails for order fills are not sent. | getTradeConfirmEmail(): ?string | setTradeConfirmEmail(?string tradeConfirmEmail): void |
| `suspendTrade` | `?bool` | Optional | If true, new orders are blocked. | getSuspendTrade(): ?bool | setSuspendTrade(?bool suspendTrade): void |
| `noShorting` | `?bool` | Optional | If true, account becomes long-only mode. | getNoShorting(): ?bool | setNoShorting(?bool noShorting): void |
| `fractionalTrading` | `?bool` | Optional | If true, account is able to participate in fractional trading | getFractionalTrading(): ?bool | setFractionalTrading(?bool fractionalTrading): void |
| `maxMarginMultiplier` | `?string` | Optional | Can be "1" or "2" | getMaxMarginMultiplier(): ?string | setMaxMarginMultiplier(?string maxMarginMultiplier): void |
| `pdtCheck` | `?string` | Optional | - | getPdtCheck(): ?string | setPdtCheck(?string pdtCheck): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use TraderApiLib\Models\Builders\AccountConfigurationsBuilder;
use TraderApiLib\Models\DtbpCheck;
use TraderApiLib\ApiHelper;

$accountConfigurations = AccountConfigurationsBuilder::init()
    ->dtbpCheck(DtbpCheck::EXIT_)
    ->tradeConfirmEmail('trade_confirm_email2')
    ->suspendTrade(false)
    ->noShorting(false)
    ->fractionalTrading(false)
    ->pdtCheck('entry')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

