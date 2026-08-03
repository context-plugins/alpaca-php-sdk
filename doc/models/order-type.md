
# Order Type

Represents the types of orders Alpaca currently supports

- market
- limit
- stop
- stop_limit
- trailing_stop

## Enumeration

`OrderType`

## Fields

| Name |
|  --- |
| `MARKET` |
| `LIMIT` |
| `STOP` |
| `STOP_LIMIT` |
| `TRAILING_STOP` |

## Example

```php
use TraderApiLib\Models\OrderType;

$orderType = OrderType::STOP;
```

