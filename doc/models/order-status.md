
# Order Status

An order executed through Alpaca can experience several status changes during its lifecycle. The most common statuses are described in detail below:

- new
  The order has been received by Alpaca, and routed to exchanges for execution. This is the usual initial state of an order.

- partially_filled
  The order has been partially filled.

- filled
  The order has been filled, and no further updates will occur for the order.

- done_for_day
  The order is done executing for the day, and will not receive further updates until the next trading day.

- canceled
  The order has been canceled, and no further updates will occur for the order. This can be either due to a cancel request by the user, or the order has been canceled by the exchanges due to its time-in-force.

- expired
  The order has expired, and no further updates will occur for the order.

- replaced
  The order was replaced by another order, or was updated due to a market event such as corporate action.

- pending_cancel
  The order is waiting to be canceled.

- pending_replace
  The order is waiting to be replaced by another order. The order will reject cancel request while in this state.

Less common states are described below. Note that these states only occur on very rare occasions, and most users will likely never see their orders reach these states:

- accepted
  The order has been received by Alpaca, but hasn’t yet been routed to the execution venue. This could be seen often out side of trading session hours.

- pending_new
  The order has been received by Alpaca, and routed to the exchanges, but has not yet been accepted for execution. This state only occurs on rare occasions.

- accepted_for_bidding
  The order has been received by exchanges, and is evaluated for pricing. This state only occurs on rare occasions.

- stopped
  The order has been stopped, and a trade is guaranteed for the order, usually at a stated price or better, but has not yet occurred. This state only occurs on rare occasions.

- rejected
  The order has been rejected, and no further updates will occur for the order. This state occurs on rare occasions and may occur based on various conditions decided by the exchanges.

- suspended
  The order has been suspended, and is not eligible for trading. This state only occurs on rare occasions.

- calculated
  The order has been completed for the day (either filled or done for day), but remaining settlement calculations are still pending. This state only occurs on rare occasions.

An order may be canceled through the API up until the point it reaches a state of either filled, canceled, or expired.

## Enumeration

`OrderStatus`

## Fields

| Name |
|  --- |
| `NEW_` |
| `PARTIALLY_FILLED` |
| `FILLED` |
| `DONE_FOR_DAY` |
| `CANCELED` |
| `EXPIRED` |
| `REPLACED` |
| `PENDING_CANCEL` |
| `PENDING_REPLACE` |
| `ACCEPTED` |
| `PENDING_NEW` |
| `ACCEPTED_FOR_BIDDING` |
| `STOPPED` |
| `REJECTED` |
| `SUSPENDED` |
| `CALCULATED` |

## Example

```php
use TraderApiLib\Models\OrderStatus;

$orderStatus = OrderStatus::PENDING_NEW;
```

