
# Account Trading Activities

*This model accepts additional fields of type array.*

## Structure

`AccountTradingActivities`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `activityType` | [`?string(ActivityType)`](../../doc/models/activity-type.md) | Optional | - FILL<br>  Order fills (both partial and full fills)<br><br>- TRANS<br>  Cash transactions (both CSD and CSW)<br><br>- MISC<br>  Miscellaneous or rarely used activity types (All types except those in TRANS, DIV, or FILL)<br><br>- ACATC<br>  ACATS IN/OUT (Cash)<br><br>- ACATS<br>  ACATS IN/OUT (Securities)<br><br>- CFEE<br>  Crypto fee<br><br>- CSD<br>  Cash deposit(+)<br><br>- CSW<br>  Cash withdrawal(-)<br><br>- DIV<br>  Dividends<br><br>- DIVCGL<br>  Dividend (capital gain long term)<br><br>- DIVCGS<br>  Dividend (capital gain short term)<br><br>- DIVFEE<br>  Dividend fee<br><br>- DIVFT<br>  Dividend adjusted (Foreign Tax Withheld)<br><br>- DIVNRA<br>  Dividend adjusted (NRA Withheld)<br><br>- DIVROC<br>  Dividend return of capital<br><br>- DIVTW<br>  Dividend adjusted (Tefra Withheld)<br><br>- DIVTXEX<br>  Dividend (tax exempt)<br><br>- FEE<br>  Fee denominated in USD<br><br>- INT<br>  Interest (credit/margin)<br><br>- INTNRA<br>  Interest adjusted (NRA Withheld)<br><br>- INTTW<br>  Interest adjusted (Tefra Withheld)<br><br>- JNL<br>  Journal entry<br><br>- JNLC<br>  Journal entry (cash)<br><br>- JNLS<br>  Journal entry (stock)<br><br>- MA<br>  Merger/Acquisition<br><br>- NC<br>  Name change<br><br>- OPASN<br>  Option assignment<br><br>- OPEXP<br>  Option expiration<br><br>- OPXRC<br>  Option exercise<br><br>- PTC<br>  Pass Thru Charge<br><br>- PTR<br>  Pass Thru Rebate<br><br>- REORG<br>  Reorg CA<br><br>- SC<br>  Symbol change<br><br>- SSO<br>  Stock spinoff<br><br>- SSP<br>  Stock split | getActivityType(): ?string | setActivityType(?string activityType): void |
| `id` | `?string` | Optional | An id for the activity. Always in “::” format. Can be sent as page_token in requests to facilitate the paging of results. | getId(): ?string | setId(?string id): void |
| `cumQty` | `?string` | Optional | The cumulative quantity of shares involved in the execution. | getCumQty(): ?string | setCumQty(?string cumQty): void |
| `leavesQty` | `?string` | Optional | For partially_filled orders, the quantity of shares that are left to be filled. | getLeavesQty(): ?string | setLeavesQty(?string leavesQty): void |
| `price` | `?string` | Optional | The per-share price that the trade was executed at. | getPrice(): ?string | setPrice(?string price): void |
| `qty` | `?string` | Optional | The number of shares involved in the trade execution. | getQty(): ?string | setQty(?string qty): void |
| `side` | `?string` | Optional | buy or sell | getSide(): ?string | setSide(?string side): void |
| `symbol` | `?string` | Optional | The symbol of the security being traded. | getSymbol(): ?string | setSymbol(?string symbol): void |
| `transactionTime` | `?DateTime` | Optional | The time at which the execution occurred. | getTransactionTime(): ?\DateTime | setTransactionTime(?\DateTime transactionTime): void |
| `orderId` | `?string` | Optional | The id for the order that filled. | getOrderId(): ?string | setOrderId(?string orderId): void |
| `type` | [`?string(Type)`](../../doc/models/type.md) | Optional | fill or partial_fill | getType(): ?string | setType(?string type): void |
| `orderStatus` | [`?string(OrderStatus)`](../../doc/models/order-status.md) | Optional | An order executed through Alpaca can experience several status changes during its lifecycle. The most common statuses are described in detail below:<br><br>- new<br>  The order has been received by Alpaca, and routed to exchanges for execution. This is the usual initial state of an order.<br><br>- partially_filled<br>  The order has been partially filled.<br><br>- filled<br>  The order has been filled, and no further updates will occur for the order.<br><br>- done_for_day<br>  The order is done executing for the day, and will not receive further updates until the next trading day.<br><br>- canceled<br>  The order has been canceled, and no further updates will occur for the order. This can be either due to a cancel request by the user, or the order has been canceled by the exchanges due to its time-in-force.<br><br>- expired<br>  The order has expired, and no further updates will occur for the order.<br><br>- replaced<br>  The order was replaced by another order, or was updated due to a market event such as corporate action.<br><br>- pending_cancel<br>  The order is waiting to be canceled.<br><br>- pending_replace<br>  The order is waiting to be replaced by another order. The order will reject cancel request while in this state.<br><br>Less common states are described below. Note that these states only occur on very rare occasions, and most users will likely never see their orders reach these states:<br><br>- accepted<br>  The order has been received by Alpaca, but hasn’t yet been routed to the execution venue. This could be seen often out side of trading session hours.<br><br>- pending_new<br>  The order has been received by Alpaca, and routed to the exchanges, but has not yet been accepted for execution. This state only occurs on rare occasions.<br><br>- accepted_for_bidding<br>  The order has been received by exchanges, and is evaluated for pricing. This state only occurs on rare occasions.<br><br>- stopped<br>  The order has been stopped, and a trade is guaranteed for the order, usually at a stated price or better, but has not yet occurred. This state only occurs on rare occasions.<br><br>- rejected<br>  The order has been rejected, and no further updates will occur for the order. This state occurs on rare occasions and may occur based on various conditions decided by the exchanges.<br><br>- suspended<br>  The order has been suspended, and is not eligible for trading. This state only occurs on rare occasions.<br><br>- calculated<br>  The order has been completed for the day (either filled or done for day), but remaining settlement calculations are still pending. This state only occurs on rare occasions.<br><br>An order may be canceled through the API up until the point it reaches a state of either filled, canceled, or expired. | getOrderStatus(): ?string | setOrderStatus(?string orderStatus): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use TraderApiLib\Models\Builders\AccountTradingActivitiesBuilder;
use TraderApiLib\Models\ActivityType;
use TraderApiLib\Models\Type;
use TraderApiLib\Models\OrderStatus;
use TraderApiLib\ApiHelper;

$accountTradingActivities = AccountTradingActivitiesBuilder::init()
    ->activityType(ActivityType::DIVROC)
    ->id('id4')
    ->cumQty('cum_qty8')
    ->leavesQty('leaves_qty2')
    ->price('price8')
    ->symbol('AAPL')
    ->type(Type::FILL)
    ->orderStatus(OrderStatus::NEW_)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

