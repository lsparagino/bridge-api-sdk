# Transfers

## Overview

### Available Operations

* [get](#get) - Get all transfers
* [create](#create) - Create a transfer
* [getById](#getbyid) - Get a transfer
* [update](#update) - Update a transfer
* [delete](#delete) - Delete a transfer
* [listStaticTemplates](#liststatictemplates) - Get all static templates

## get

Get all transfers

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/transfers" method="get" path="/transfers" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->transfers->get(
    request: $request
);

if ($response->transfers !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                        | Type                                                                             | Required                                                                         | Description                                                                      |
| -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| `$request`                                                                       | [Operations\GetTransfersRequest](../../Models/Operations/GetTransfersRequest.md) | :heavy_check_mark:                                                               | The request object to use for the request.                                       |

### Response

**[?Operations\GetTransfersResponse](../../Models/Operations/GetTransfersResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## create

Create a transfer

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/transfers" method="post" path="/transfers" -->
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

$body = new Components\TransferRequest(
    onBehalfOf: '<value>',
    source: new Components\TransferRequestSource(
        currency: Components\EuroInclusiveCurrency::Mxn,
        paymentRail: Components\BridgeWalletSepaSwiftInclusivePaymentRail::Arbitrum,
    ),
    destination: new Components\TransferRequestDestination(
        currency: Components\EuroInclusiveCurrency::Usdc,
        paymentRail: Components\SepaSwiftInclusiveOfframpPaymentRail::AvalancheCChain,
    ),
);

$response = $sdk->transfers->create(
    idempotencyKey: '<value>',
    body: $body

);

if ($response->oneOf !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                | Type                                                                     | Required                                                                 | Description                                                              |
| ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ | ------------------------------------------------------------------------ |
| `idempotencyKey`                                                         | *string*                                                                 | :heavy_check_mark:                                                       | N/A                                                                      |
| `body`                                                                   | [Components\TransferRequest](../../Models/Components/TransferRequest.md) | :heavy_check_mark:                                                       | Transfer object to be created                                            |

### Response

**[?Operations\PostTransfersResponse](../../Models/Operations/PostTransfersResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401, 403       | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getById

Retrieve a transfer object from the passed in transfer ID

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/transfers/{transferID}" method="get" path="/transfers/{transferID}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->transfers->getById(
    transferID: '<id>'
);

if ($response->transferResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `transferID`       | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\GetTransfersTransferIDResponse](../../Models/Operations/GetTransfersTransferIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401, 404            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## update

Update a transfer that was previously created. Must be in the awaiting_funds state.

### Example Usage

<!-- UsageSnippet language="php" operationID="put_/transfers/{transferID}" method="put" path="/transfers/{transferID}" -->
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

$body = new Components\TransferUpdateRequest();

$response = $sdk->transfers->update(
    transferID: '<id>',
    body: $body

);

if ($response->transferResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                            | Type                                                                                 | Required                                                                             | Description                                                                          |
| ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| `transferID`                                                                         | *string*                                                                             | :heavy_check_mark:                                                                   | N/A                                                                                  |
| `body`                                                                               | [Components\TransferUpdateRequest](../../Models/Components/TransferUpdateRequest.md) | :heavy_check_mark:                                                                   | Transfer object to be updated                                                        |

### Response

**[?Operations\PutTransfersTransferIDResponse](../../Models/Operations/PutTransfersTransferIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401, 403       | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## delete

Delete a transfer that was previously created. Must be in the awaiting_funds state.

### Example Usage

<!-- UsageSnippet language="php" operationID="delete_/transfers/{transferID}" method="delete" path="/transfers/{transferID}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->transfers->delete(
    transferID: '<id>'
);

if ($response->statusCode === 200) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `transferID`       | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\DeleteTransfersTransferIDResponse](../../Models/Operations/DeleteTransfersTransferIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401, 404            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## listStaticTemplates

Get all static templates

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/transfers/static_templates" method="get" path="/transfers/static_templates" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->transfers->listStaticTemplates(

);

if ($response->staticTemplates !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                                                                                                              | Type                                                                                                                                                                                                                                                                                                                                                                                   | Required                                                                                                                                                                                                                                                                                                                                                                               | Description                                                                                                                                                                                                                                                                                                                                                                            |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `limit`                                                                                                                                                                                                                                                                                                                                                                                | *?int*                                                                                                                                                                                                                                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                     | The number of items to return (default of 10, max of 100)                                                                                                                                                                                                                                                                                                                              |
| `startingAfter`                                                                                                                                                                                                                                                                                                                                                                        | *?string*                                                                                                                                                                                                                                                                                                                                                                              | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                     | This is a transfer id. If this is specified, the next page that starts with a transfer right AFTER the specified transfer id on the transfer timeline, which is always ordered from the newest to the oldest by creation time, will be returned. This also implies that transfers older than the specified transfer id will be returned (shouldn't be set if ending_before is set)     |
| `endingBefore`                                                                                                                                                                                                                                                                                                                                                                         | *?string*                                                                                                                                                                                                                                                                                                                                                                              | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                     | This is a transfer id. If this is specified, the previous page that ends with a transfer right BEFORE the specified transfer id on the transfer timeline, which is always ordered from the newest to the oldest by creation time, will be returned. This also implies that transfers newer than the specified transfer id will be returned (shouldn't be set if starting_after is set) |

### Response

**[?Operations\GetTransfersStaticTemplatesResponse](../../Models/Operations/GetTransfersStaticTemplatesResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |