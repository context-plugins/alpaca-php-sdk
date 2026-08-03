
# Patch Order Request

Represents a request to patch an order.

*This model accepts additional fields of type array.*

## Structure

`PatchOrderRequest`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `qty` | `?string` | Optional | number of shares to trade | getQty(): ?string | setQty(?string qty): void |
| `timeInForce` | [`?string(TimeInForce)`](../../doc/models/time-in-force.md) | Optional | Note: For Crypto Trading, Alpaca supports the following Time-In-Force designations: day, gtc, ioc and fok. OPG and CLS are not supported.<br><br>Alpaca supports the following Time-In-Force designations:<br><br>- day<br>  A day order is eligible for execution only on the day it is live. By default, the order is only valid during Regular Trading Hours (9:30am - 4:00pm ET). If unfilled after the closing auction, it is automatically canceled. If submitted after the close, it is queued and submitted the following trading day. However, if marked as eligible for extended hours, the order can also execute during supported extended hours.<br><br>- gtc<br>  The order is good until canceled. Non-marketable GTC limit orders are subject to price adjustments to offset corporate actions affecting the issue. We do not currently support Do Not Reduce(DNR) orders to opt out of such price adjustments.<br><br>- opg<br>  Use this TIF with a market/limit order type to submit “market on open” (MOO) and “limit on open” (LOO) orders. This order is eligible to execute only in the market opening auction. Any unfilled orders after the open will be cancelled. OPG orders submitted after 9:28am but before 7:00pm ET will be rejected. OPG orders submitted after 7:00pm will be queued and routed to the following day’s opening auction. On open/on close orders are routed to the primary exchange. Such orders do not necessarily execute exactly at 9:30am / 4:00pm ET but execute per the exchange’s auction rules.<br><br>- cls<br>  Use this TIF with a market/limit order type to submit “market on close” (MOC) and “limit on close” (LOC) orders. This order is eligible to execute only in the market closing auction. Any unfilled orders after the close will be cancelled. CLS orders submitted after 3:50pm but before 7:00pm ET will be rejected. CLS orders submitted after 7:00pm will be queued and routed to the following day’s closing auction. Only available with API v2.<br><br>- ioc<br>  An Immediate Or Cancel (IOC) order requires all or part of the order to be executed immediately. Any unfilled portion of the order is canceled. Only available with API v2. Most market makers who receive IOC orders will attempt to fill the order on a principal basis only, and cancel any unfilled balance. On occasion, this can result in the entire order being cancelled if the market maker does not have any existing inventory of the security in question.<br><br>- fok<br>  A Fill or Kill (FOK) order is only executed if the entire order quantity can be filled, otherwise the order is canceled. Only available with API v2. | getTimeInForce(): ?string | setTimeInForce(?string timeInForce): void |
| `limitPrice` | `?string` | Optional | required if original order type is limit or stop_limit | getLimitPrice(): ?string | setLimitPrice(?string limitPrice): void |
| `stopPrice` | `?string` | Optional | required if original order type is limit or stop_limit | getStopPrice(): ?string | setStopPrice(?string stopPrice): void |
| `trail` | `?string` | Optional | the new value of the trail_price or trail_percent value (works only for type=“trailing_stop”) | getTrail(): ?string | setTrail(?string trail): void |
| `clientOrderId` | `?string` | Optional | A unique identifier for the order. Automatically generated if not sent.<br><br>**Constraints**: *Maximum Length*: `48` | getClientOrderId(): ?string | setClientOrderId(?string clientOrderId): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use TraderApiLib\Models\Builders\PatchOrderRequestBuilder;
use TraderApiLib\Models\TimeInForce;
use TraderApiLib\ApiHelper;

$patchOrderRequest = PatchOrderRequestBuilder::init()
    ->qty('qty8')
    ->timeInForce(TimeInForce::DAY)
    ->limitPrice('limit_price4')
    ->stopPrice('stop_price6')
    ->trail('trail6')
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

