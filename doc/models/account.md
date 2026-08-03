
# Account

The account API serves important information related to an account, including account status, funds available for trade, funds available for withdrawal, and various flags relevant to an account’s ability to trade. An account maybe be blocked for just for trades (trades_blocked flag) or for both trades and transfers (account_blocked flag) if Alpaca identifies the account to engaging in any suspicious activity. Also, in accordance with FINRA’s pattern day trading rule, an account may be flagged for pattern day trading (pattern_day_trader flag), which would inhibit an account from placing any further day-trades. Please note that cryptocurrencies are not eligible assets to be used as collateral for margin accounts and will require the asset be traded using cash only.

*This model accepts additional fields of type array.*

## Structure

`Account`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `id` | `string` | Required | Account Id. | getId(): string | setId(string id): void |
| `accountNumber` | `?string` | Optional | Account number. | getAccountNumber(): ?string | setAccountNumber(?string accountNumber): void |
| `status` | [`string(AccountStatus)`](../../doc/models/account-status.md) | Required | An enum representing the various possible account status values.<br><br>Most likely, the account status is ACTIVE unless there is any problem. The account status may get in ACCOUNT_UPDATED when personal information is being updated from the dashboard, in which case you may not be allowed trading for a short period of time until the change is approved.<br><br>- ONBOARDING<br>  The account is onboarding.<br>- SUBMISSION_FAILED<br>  The account application submission failed for some reason.<br>- SUBMITTED<br>  The account application has been submitted for review.<br>- ACCOUNT_UPDATED<br>  The account information is being updated.<br>- APPROVAL_PENDING<br>  The final account approval is pending.<br>- ACTIVE<br>  The account is active for trading.<br>- REJECTED<br>  The account application has been rejected. | getStatus(): string | setStatus(string status): void |
| `currency` | `?string` | Optional | USD | getCurrency(): ?string | setCurrency(?string currency): void |
| `cash` | `?string` | Optional | Cash Balance | getCash(): ?string | setCash(?string cash): void |
| `portfolioValue` | `?string` | Optional | Total value of cash + holding positions (This field is deprecated. It is equivalent to the equity field.) | getPortfolioValue(): ?string | setPortfolioValue(?string portfolioValue): void |
| `patternDayTrader` | `?bool` | Optional | Whether or not the account has been flagged as a pattern day trader | getPatternDayTrader(): ?bool | setPatternDayTrader(?bool patternDayTrader): void |
| `tradeSuspendedByUser` | `?bool` | Optional | User setting. If true, the account is not allowed to place orders. | getTradeSuspendedByUser(): ?bool | setTradeSuspendedByUser(?bool tradeSuspendedByUser): void |
| `tradingBlocked` | `?bool` | Optional | If true, the account is not allowed to place orders. | getTradingBlocked(): ?bool | setTradingBlocked(?bool tradingBlocked): void |
| `transfersBlocked` | `?bool` | Optional | If true, the account is not allowed to request money transfers. | getTransfersBlocked(): ?bool | setTransfersBlocked(?bool transfersBlocked): void |
| `accountBlocked` | `?bool` | Optional | If true, the account activity by user is prohibited. | getAccountBlocked(): ?bool | setAccountBlocked(?bool accountBlocked): void |
| `createdAt` | `?DateTime` | Optional | Timestamp this account was created at | getCreatedAt(): ?\DateTime | setCreatedAt(?\DateTime createdAt): void |
| `shortingEnabled` | `?bool` | Optional | Flag to denote whether or not the account is permitted to short | getShortingEnabled(): ?bool | setShortingEnabled(?bool shortingEnabled): void |
| `longMarketValue` | `?string` | Optional | Real-time MtM value of all long positions held in the account | getLongMarketValue(): ?string | setLongMarketValue(?string longMarketValue): void |
| `shortMarketValue` | `?string` | Optional | Real-time MtM value of all short positions held in the account | getShortMarketValue(): ?string | setShortMarketValue(?string shortMarketValue): void |
| `equity` | `?string` | Optional | Cash + long_market_value + short_market_value | getEquity(): ?string | setEquity(?string equity): void |
| `lastEquity` | `?string` | Optional | Equity as of previous trading day at 16:00:00 ET | getLastEquity(): ?string | setLastEquity(?string lastEquity): void |
| `multiplier` | `?string` | Optional | Buying power multiplier that represents account margin classification; valid values 1 (standard limited margin account with 1x buying power), 2 (reg T margin account with 2x intraday and overnight buying power; this is the default for all non-PDT accounts with $2,000 or more equity), 4 (PDT account with 4x intraday buying power and 2x reg T overnight buying power) | getMultiplier(): ?string | setMultiplier(?string multiplier): void |
| `buyingPower` | `?string` | Optional | Current available $ buying power; If multiplier = 4, this is your daytrade buying power which is calculated as (last_equity - (last) maintenance_margin) * 4; If multiplier = 2, buying_power = max(equity – initial_margin,0) * 2; If multiplier = 1, buying_power = cash | getBuyingPower(): ?string | setBuyingPower(?string buyingPower): void |
| `initialMargin` | `?string` | Optional | Reg T initial margin requirement (continuously updated value) | getInitialMargin(): ?string | setInitialMargin(?string initialMargin): void |
| `maintenanceMargin` | `?string` | Optional | Maintenance margin requirement (continuously updated value) | getMaintenanceMargin(): ?string | setMaintenanceMargin(?string maintenanceMargin): void |
| `sma` | `?string` | Optional | Value of special memorandum account (will be used at a later date to provide additional buying_power) | getSma(): ?string | setSma(?string sma): void |
| `daytradeCount` | `?int` | Optional | The current number of daytrades that have been made in the last 5 trading days (inclusive of today) | getDaytradeCount(): ?int | setDaytradeCount(?int daytradeCount): void |
| `lastMaintenanceMargin` | `?string` | Optional | Your maintenance margin requirement on the previous trading day | getLastMaintenanceMargin(): ?string | setLastMaintenanceMargin(?string lastMaintenanceMargin): void |
| `daytradingBuyingPower` | `?string` | Optional | Your buying power for day trades (continuously updated value) | getDaytradingBuyingPower(): ?string | setDaytradingBuyingPower(?string daytradingBuyingPower): void |
| `regtBuyingPower` | `?string` | Optional | Your buying power under Regulation T (your excess equity - equity minus margin value - times your margin multiplier) | getRegtBuyingPower(): ?string | setRegtBuyingPower(?string regtBuyingPower): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use TraderApiLib\Models\Builders\AccountBuilder;
use TraderApiLib\Models\AccountStatus;
use TraderApiLib\ApiHelper;

$account = AccountBuilder::init(
    '000025e4-0000-0000-0000-000000000000',
    AccountStatus::ACTIVE
)
    ->accountNumber('account_number0')
    ->currency('USD')
    ->cash('cash0')
    ->portfolioValue('portfolio_value0')
    ->patternDayTrader(false)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

