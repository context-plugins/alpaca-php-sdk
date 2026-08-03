
# Canceled Order Response

Represents the result of a request to cancel and order

*This model accepts additional fields of type array.*

## Structure

`CanceledOrderResponse`

## Fields

| Name | Type | Tags | Description | Getter | Setter |
|  --- | --- | --- | --- | --- | --- |
| `id` | `?string` | Optional | orderId | getId(): ?string | setId(?string id): void |
| `status` | `?int` | Optional | http response code | getStatus(): ?int | setStatus(?int status): void |
| `additionalProperties` | `array<string, array>` | Optional | - | findAdditionalProperty(string key): array | additionalProperty(string key, array value): void |

## Example

```php
use TraderApiLib\Models\Builders\CanceledOrderResponseBuilder;
use TraderApiLib\ApiHelper;

$canceledOrderResponse = CanceledOrderResponseBuilder::init()
    ->id('00001068-0000-0000-0000-000000000000')
    ->status(200)
    ->additionalProperty('exampleAdditionalProperty', ApiHelper::deserialize('{"key1":"val1","key2":"val2"}'))
    ->build();
```

