
# Get Account Activities Response

## Data Type

`AccountTradingActivities|AccountNonTradeActivities`

## Cases

| Type |
|  --- |
| [`AccountTradingActivities`](../../../doc/models/account-trading-activities.md) |
| [`AccountNonTradeActivities`](../../../doc/models/account-non-trade-activities.md) |

## AccountTradingActivities

### Initialization Code

#### Example

```php
$value = AccountTradingActivitiesBuilder::init()
    ->symbol('AAPL')
    ->type(Type::FILL)
    ->orderStatus(OrderStatus::NEW_)
    ->build();
```

## AccountNonTradeActivities

### Initialization Code

#### Example

```php
$value = AccountNonTradeActivitiesBuilder::init()->build();
```

