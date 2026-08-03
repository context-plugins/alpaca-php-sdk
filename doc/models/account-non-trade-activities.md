
# Account Non Trade Activities

*This model accepts additional fields of type array.*

## Structure

`AccountNonTradeActivities`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `activityType` | [`?string(ActivityType)`](../../doc/models/activity-type.md) | Optional | - FILL<br>  Order fills (both partial and full fills)<br><br>- TRANS<br>  Cash transactions (both CSD and CSW)<br><br>- MISC<br>  Miscellaneous or rarely used activity types (All types except those in TRANS, DIV, or FILL)<br><br>- ACATC<br>  ACATS IN/OUT (Cash)<br><br>- ACATS<br>  ACATS IN/OUT (Securities)<br><br>- CFEE<br>  Crypto fee<br><br>- CSD<br>  Cash deposit(+)<br><br>- CSW<br>  Cash withdrawal(-)<br><br>- DIV<br>  Dividends<br><br>- DIVCGL<br>  Dividend (capital gain long term)<br><br>- DIVCGS<br>  Dividend (capital gain short term)<br><br>- DIVFEE<br>  Dividend fee<br><br>- DIVFT<br>  Dividend adjusted (Foreign Tax Withheld)<br><br>- DIVNRA<br>  Dividend adjusted (NRA Withheld)<br><br>- DIVROC<br>  Dividend return of capital<br><br>- DIVTW<br>  Dividend adjusted (Tefra Withheld)<br><br>- DIVTXEX<br>  Dividend (tax exempt)<br><br>- FEE<br>  Fee denominated in USD<br><br>- INT<br>  Interest (credit/margin)<br><br>- INTNRA<br>  Interest adjusted (NRA Withheld)<br><br>- INTTW<br>  Interest adjusted (Tefra Withheld)<br><br>- JNL<br>  Journal entry<br><br>- JNLC<br>  Journal entry (cash)<br><br>- JNLS<br>  Journal entry (stock)<br><br>- MA<br>  Merger/Acquisition<br><br>- NC<br>  Name change<br><br>- OPASN<br>  Option assignment<br><br>- OPEXP<br>  Option expiration<br><br>- OPXRC<br>  Option exercise<br><br>- PTC<br>  Pass Thru Charge<br><br>- PTR<br>  Pass Thru Rebate<br><br>- REORG<br>  Reorg CA<br><br>- SC<br>  Symbol change<br><br>- SSO<br>  Stock spinoff<br><br>- SSP<br>  Stock split | getActivityType(): ?string | setActivityType(?string activityType): void |
| `id` | `?string` | Optional | An ID for the activity, always in “::” format. Can be sent as page_token in requests to facilitate the paging of results. | getId(): ?string | setId(?string id): void |
| `date` | `?DateTime` | Optional | The date on which the activity occurred or on which the transaction associated with the activity settled. | getDate(): ?\DateTime | setDate(?\DateTime date): void |
| `netAmount` | `?string` | Optional | The net amount of money (positive or negative) associated with the activity. | getNetAmount(): ?string | setNetAmount(?string netAmount): void |
| `symbol` | `?string` | Optional | The symbol of the security involved with the activity. Not present for all activity types. | getSymbol(): ?string | setSymbol(?string symbol): void |
| `qty` | `?string` | Optional | For dividend activities, the number of shares that contributed to the payment. Not present for other activity types. | getQty(): ?string | setQty(?string qty): void |
| `perShareAmount` | `?string` | Optional | For dividend activities, the average amount paid per share. Not present for other activity types. | getPerShareAmount(): ?string | setPerShareAmount(?string perShareAmount): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use TraderApiLib\Models\Builders\AccountNonTradeActivitiesBuilder;
use TraderApiLib\Models\ActivityType;
use TraderApiLib\Utils\DateTimeHelper;
use TraderApiLib\ApiHelper;

$accountNonTradeActivities = AccountNonTradeActivitiesBuilder::init()
    ->activityType(ActivityType::SSO)
    ->id('id8')
    ->date(DateTimeHelper::fromRfc3339DateTime('2016-03-13T12:52:32.123Z'))
    ->netAmount('net_amount8')
    ->symbol('symbol0')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

