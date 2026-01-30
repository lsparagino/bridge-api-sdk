# StaticMemos

## Overview

### Available Operations

* [list](#list) - List Static Memos
* [create](#create) - Create a Static Memo
* [listByCustomer](#listbycustomer) - List Static Memos for Customer
* [get](#get) - Get a Static Memo
* [update](#update) - Update a Static Memo
* [getHistoryForCustomer](#gethistoryforcustomer) - Static Memo Activity
* [getHistory](#gethistory) - Static Memo Activity Across All Customers

## list

List all Static Memo objects

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/static_memos" method="get" path="/static_memos" -->
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



$response = $sdk->staticMemos->list(
    status: Components\VirtualAccountActivationStatus::Activated
);

if ($response->staticMemos !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                                                                                                                               | Type                                                                                                                                                                                                                                                                                                                                                                                                    | Required                                                                                                                                                                                                                                                                                                                                                                                                | Description                                                                                                                                                                                                                                                                                                                                                                                             | Example                                                                                                                                                                                                                                                                                                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `status`                                                                                                                                                                                                                                                                                                                                                                                                | [?Components\VirtualAccountActivationStatus](../../Models/Components/VirtualAccountActivationStatus.md)                                                                                                                                                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                      | Limit results to those with the given activation status                                                                                                                                                                                                                                                                                                                                                 | activated                                                                                                                                                                                                                                                                                                                                                                                               |
| `limit`                                                                                                                                                                                                                                                                                                                                                                                                 | *?int*                                                                                                                                                                                                                                                                                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                      | The number of items to return (default of 10, max of 100)                                                                                                                                                                                                                                                                                                                                               |                                                                                                                                                                                                                                                                                                                                                                                                         |
| `startingAfter`                                                                                                                                                                                                                                                                                                                                                                                         | *?string*                                                                                                                                                                                                                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                      | This is a static memo id. If this is specified, the next page that starts with a static memo right AFTER the specified static memo id on the static memo timeline, which is always ordered from the newest to the oldest by creation time, will be returned. This also implies that static memo older than the specified static memo id will be returned (shouldn't be set if ending_before is set)     |                                                                                                                                                                                                                                                                                                                                                                                                         |
| `endingBefore`                                                                                                                                                                                                                                                                                                                                                                                          | *?string*                                                                                                                                                                                                                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                      | This is a static memo id. If this is specified, the previous page that ends with a static memo right BEFORE the specified static memo id on the static memo timeline, which is always ordered from the newest to the oldest by creation time, will be returned. This also implies that static memo newer than the specified static memo id will be returned (shouldn't be set if starting_after is set) |                                                                                                                                                                                                                                                                                                                                                                                                         |

### Response

**[?Operations\GetStaticMemosResponse](../../Models/Operations/GetStaticMemosResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## create

Create a Static Memo for the specified customer

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/customers/{customerID}/static_memos" method="post" path="/customers/{customerID}/static_memos" -->
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

$body = new Components\CreateStaticMemo(
    developerFeePercent: '0.1',
    source: new Components\StaticMemoSourceInput(
        currency: Components\FiatCurrency::Usd,
        paymentRail: Components\PaymentRail::Wire,
    ),
    destination: new Components\StaticMemoDestination(
        currency: Components\CryptoCurrency::Usdc,
        paymentRail: Components\OfframpChain::Polygon,
        address: '0xdeadbeef',
    ),
);

$response = $sdk->staticMemos->create(
    idempotencyKey: '<value>',
    customerID: '<id>',
    body: $body

);

if ($response->staticMemoResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                  | Type                                                                       | Required                                                                   | Description                                                                |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| `idempotencyKey`                                                           | *string*                                                                   | :heavy_check_mark:                                                         | N/A                                                                        |
| `customerID`                                                               | *string*                                                                   | :heavy_check_mark:                                                         | N/A                                                                        |
| `body`                                                                     | [Components\CreateStaticMemo](../../Models/Components/CreateStaticMemo.md) | :heavy_check_mark:                                                         | Static Memo object to be created                                           |

### Response

**[?Operations\PostCustomersCustomerIDStaticMemosResponse](../../Models/Operations/PostCustomersCustomerIDStaticMemosResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## listByCustomer

List all Static Memo objects for a customer

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/static_memos" method="get" path="/customers/{customerID}/static_memos" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;
use ReThink\BridgeSDK\Models\Components;
use ReThink\BridgeSDK\Models\Operations;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();

$request = new Operations\GetCustomersCustomerIDStaticMemosRequest(
    customerID: '<id>',
    status: Components\VirtualAccountActivationStatus::Activated,
);

$response = $sdk->staticMemos->listByCustomer(
    request: $request
);

if ($response->staticMemos !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                  | Type                                                                                                                       | Required                                                                                                                   | Description                                                                                                                |
| -------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| `$request`                                                                                                                 | [Operations\GetCustomersCustomerIDStaticMemosRequest](../../Models/Operations/GetCustomersCustomerIDStaticMemosRequest.md) | :heavy_check_mark:                                                                                                         | The request object to use for the request.                                                                                 |

### Response

**[?Operations\GetCustomersCustomerIDStaticMemosResponse](../../Models/Operations/GetCustomersCustomerIDStaticMemosResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## get

Retrieve the Static Memo object from the passed ID

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/static_memos/{staticMemoID}" method="get" path="/customers/{customerID}/static_memos/{staticMemoID}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->staticMemos->get(
    customerID: '<id>',
    staticMemoID: '<id>'

);

if ($response->staticMemoResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `customerID`       | *string*           | :heavy_check_mark: | N/A                |
| `staticMemoID`     | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\GetCustomersCustomerIDStaticMemosStaticMemoIDResponse](../../Models/Operations/GetCustomersCustomerIDStaticMemosStaticMemoIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## update

Update instructions for an existing Static Memo

### Example Usage

<!-- UsageSnippet language="php" operationID="put_/customers/{customerID}/static_memos/{staticMemoID}" method="put" path="/customers/{customerID}/static_memos/{staticMemoID}" -->
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

$body = new Components\UpdateStaticMemo(
    destination: new Components\UpdateStaticMemoDestination(
        currency: Components\CryptoCurrency::Usdc,
        paymentRail: Components\OfframpChain::Polygon,
        address: '0xdeadbeef',
    ),
    developerFeePercent: '0.1',
);

$response = $sdk->staticMemos->update(
    customerID: '<id>',
    staticMemoID: '<id>',
    body: $body

);

if ($response->staticMemoResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                  | Type                                                                       | Required                                                                   | Description                                                                |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| `customerID`                                                               | *string*                                                                   | :heavy_check_mark:                                                         | N/A                                                                        |
| `staticMemoID`                                                             | *string*                                                                   | :heavy_check_mark:                                                         | N/A                                                                        |
| `body`                                                                     | [Components\UpdateStaticMemo](../../Models/Components/UpdateStaticMemo.md) | :heavy_check_mark:                                                         | The Static Memo details to be updated                                      |

### Response

**[?Operations\PutCustomersCustomerIDStaticMemosStaticMemoIDResponse](../../Models/Operations/PutCustomersCustomerIDStaticMemosStaticMemoIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getHistoryForCustomer

History of activity for a Static Memo

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/static_memos/{staticMemoID}/history" method="get" path="/customers/{customerID}/static_memos/{staticMemoID}/history" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;
use ReThink\BridgeSDK\Models\Operations;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();

$request = new Operations\GetCustomersCustomerIDStaticMemosStaticMemoIDHistoryRequest(
    customerID: '<id>',
    staticMemoID: '<id>',
);

$response = $sdk->staticMemos->getHistoryForCustomer(
    request: $request
);

if ($response->staticMemoHistory !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                                                        | Type                                                                                                                                                             | Required                                                                                                                                                         | Description                                                                                                                                                      |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `$request`                                                                                                                                                       | [Operations\GetCustomersCustomerIDStaticMemosStaticMemoIDHistoryRequest](../../Models/Operations/GetCustomersCustomerIDStaticMemosStaticMemoIDHistoryRequest.md) | :heavy_check_mark:                                                                                                                                               | The request object to use for the request.                                                                                                                       |

### Response

**[?Operations\GetCustomersCustomerIDStaticMemosStaticMemoIDHistoryResponse](../../Models/Operations/GetCustomersCustomerIDStaticMemosStaticMemoIDHistoryResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getHistory

History of activity across all customers and Virtual Accounts

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/static_memos/history" method="get" path="/static_memos/history" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->staticMemos->getHistory(
    request: $request
);

if ($response->staticMemoHistory !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                          | Type                                                                                               | Required                                                                                           | Description                                                                                        |
| -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| `$request`                                                                                         | [Operations\GetStaticMemosHistoryRequest](../../Models/Operations/GetStaticMemosHistoryRequest.md) | :heavy_check_mark:                                                                                 | The request object to use for the request.                                                         |

### Response

**[?Operations\GetStaticMemosHistoryResponse](../../Models/Operations/GetStaticMemosHistoryResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |