
# Calendar

*This model accepts additional fields of type array.*

## Structure

`Calendar`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `date` | `string` | Required | Date string in “%Y-%m-%d” format<br><br>**Constraints**: *Minimum Length*: `1` | getDate(): string | setDate(string date): void |
| `open` | `string` | Required | The time the market opens at on this date in “%H:%M” format<br><br>**Constraints**: *Minimum Length*: `1` | getOpen(): string | setOpen(string open): void |
| `close` | `string` | Required | The time the market closes at on this date in “%H:%M” format<br><br>**Constraints**: *Minimum Length*: `1` | getClose(): string | setClose(string close): void |
| `sessionOpen` | `string` | Required | **Constraints**: *Minimum Length*: `1` | getSessionOpen(): string | setSessionOpen(string sessionOpen): void |
| `sessionClose` | `string` | Required | **Constraints**: *Minimum Length*: `1` | getSessionClose(): string | setSessionClose(string sessionClose): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use TraderApiLib\Models\Builders\CalendarBuilder;
use TraderApiLib\ApiHelper;

$calendar = CalendarBuilder::init(
    'date4',
    'open4',
    'close8',
    'session_open2',
    'session_close4'
)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

