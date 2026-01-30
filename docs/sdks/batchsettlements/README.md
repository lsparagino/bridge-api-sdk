# BatchSettlements

## Overview

### Available Operations

* [create](#create) - Create a Batch Settlement Schedule

## create

Creates a Batch Settlement Schedule that can be used as the destination of a liquidation address.

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/customers/{customerID}/batch_settlement_schedules" method="post" path="/customers/{customerID}/batch_settlement_schedules" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;
use ReThink\BridgeSDK\Models\Components;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();

$body = new Components\CreateBatchSettlementSchedule(
    destination: new Components\TransferDestination(
        currency: Components\EuroInclusiveCurrency::Gbp,
        paymentRail: Components\SepaSwiftInclusiveOfframpPaymentRail::AchSameDay,
    ),
);

$response = $sdk->batchSettlements->create(
    customerID: '<id>',
    idempotencyKey: '<value>',
    body: $body

);

if ($response->batchSettlementSchedule !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                            | Type                                                                                                 | Required                                                                                             | Description                                                                                          |
| ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| `customerID`                                                                                         | *string*                                                                                             | :heavy_check_mark:                                                                                   | N/A                                                                                                  |
| `idempotencyKey`                                                                                     | *string*                                                                                             | :heavy_check_mark:                                                                                   | N/A                                                                                                  |
| `body`                                                                                               | [Components\CreateBatchSettlementSchedule](../../Models/Components/CreateBatchSettlementSchedule.md) | :heavy_check_mark:                                                                                   | N/A                                                                                                  |

### Response

**[?Operations\PostCustomersCustomerIDBatchSettlementSchedulesResponse](../../Models/Operations/PostCustomersCustomerIDBatchSettlementSchedulesResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |