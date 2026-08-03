
# Clock

*This model accepts additional fields of type array.*

## Structure

`Clock`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `timestamp` | `?DateTime` | Optional | Current timestamp | getTimestamp(): ?\DateTime | setTimestamp(?\DateTime timestamp): void |
| `isOpen` | `?bool` | Optional | Whether or not the market is open | getIsOpen(): ?bool | setIsOpen(?bool isOpen): void |
| `nextOpen` | `?DateTime` | Optional | Next Market open timestamp | getNextOpen(): ?\DateTime | setNextOpen(?\DateTime nextOpen): void |
| `nextClose` | `?DateTime` | Optional | Next market close timestamp | getNextClose(): ?\DateTime | setNextClose(?\DateTime nextClose): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use TraderApiLib\Models\Builders\ClockBuilder;
use TraderApiLib\Utils\DateTimeHelper;
use TraderApiLib\ApiHelper;

$clock = ClockBuilder::init()
    ->timestamp(DateTimeHelper::fromRfc3339DateTime('2016-03-13T12:52:32.123Z'))
    ->isOpen(false)
    ->nextOpen(DateTimeHelper::fromRfc3339DateTime('2016-03-13T12:52:32.123Z'))
    ->nextClose(DateTimeHelper::fromRfc3339DateTime('2016-03-13T12:52:32.123Z'))
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

