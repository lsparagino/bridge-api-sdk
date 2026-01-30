# VirtualAccounts

## Overview

### Available Operations

* [create](#create) - Create a Virtual Account
* [listByCustomer](#listbycustomer) - List Virtual Accounts by Customer
* [get](#get) - Get a Virtual Account
* [update](#update) - Update a Virtual Account
* [deactivate](#deactivate) - Deactivate a Virtual Account
* [reactivate](#reactivate) - Reactivate a Virtual Account
* [customerHistory](#customerhistory) - Virtual Account Activity
* [list](#list) - List Virtual Accounts
* [getHistory](#gethistory) - Virtual Account Activity Across All Customers

## create

Create a Virtual Account or Virtual IBAN for the specified customer

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/customers/{customerID}/virtual_accounts" method="post" path="/customers/{customerID}/virtual_accounts" -->
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

$body = new Components\CreateVirtualAccount(
    developerFeePercent: '0.1',
    source: new Components\VirtualAccountSourceInput(
        currency: Components\EuroInclusiveFiatCurrency::Usd,
    ),
    destination: new Components\VirtualAccountDestination(
        currency: Components\CryptoCurrency::Usdc,
        paymentRail: Components\OfframpChain::Base,
        address: '0xdeadbeef',
    ),
);

$response = $sdk->virtualAccounts->create(
    idempotencyKey: '<value>',
    customerID: '<id>',
    body: $body

);

if ($response->virtualAccountResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                          | Type                                                                               | Required                                                                           | Description                                                                        |
| ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `idempotencyKey`                                                                   | *string*                                                                           | :heavy_check_mark:                                                                 | N/A                                                                                |
| `customerID`                                                                       | *string*                                                                           | :heavy_check_mark:                                                                 | N/A                                                                                |
| `body`                                                                             | [Components\CreateVirtualAccount](../../Models/Components/CreateVirtualAccount.md) | :heavy_check_mark:                                                                 | Virtual Account object to be created                                               |

### Response

**[?Operations\PostCustomersCustomerIDVirtualAccountsResponse](../../Models/Operations/PostCustomersCustomerIDVirtualAccountsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## listByCustomer

List all Virtual Account objects for a customer

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/virtual_accounts" method="get" path="/customers/{customerID}/virtual_accounts" -->
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

$request = new Operations\GetCustomersCustomerIDVirtualAccountsRequest(
    customerID: '<id>',
    status: Components\VirtualAccountActivationStatus::Activated,
);

$response = $sdk->virtualAccounts->listByCustomer(
    request: $request
);

if ($response->virtualAccounts !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                          | Type                                                                                                                               | Required                                                                                                                           | Description                                                                                                                        |
| ---------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| `$request`                                                                                                                         | [Operations\GetCustomersCustomerIDVirtualAccountsRequest](../../Models/Operations/GetCustomersCustomerIDVirtualAccountsRequest.md) | :heavy_check_mark:                                                                                                                 | The request object to use for the request.                                                                                         |

### Response

**[?Operations\GetCustomersCustomerIDVirtualAccountsResponse](../../Models/Operations/GetCustomersCustomerIDVirtualAccountsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## get

Retrieve the Virtual Account object from the passed ID

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/virtual_accounts/{virtualAccountID}" method="get" path="/customers/{customerID}/virtual_accounts/{virtualAccountID}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->virtualAccounts->get(
    customerID: '<id>',
    virtualAccountID: '<id>'

);

if ($response->virtualAccountResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `customerID`       | *string*           | :heavy_check_mark: | N/A                |
| `virtualAccountID` | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\GetCustomersCustomerIDVirtualAccountsVirtualAccountIDResponse](../../Models/Operations/GetCustomersCustomerIDVirtualAccountsVirtualAccountIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## update

Update instructions for an existing Virtual Account

### Example Usage

<!-- UsageSnippet language="php" operationID="put_/customers/{customerID}/virtual_accounts/{virtualAccountID}" method="put" path="/customers/{customerID}/virtual_accounts/{virtualAccountID}" -->
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

$body = new Components\UpdateVirtualAccount(
    destination: new Components\UpdateVirtualAccountDestination(
        currency: Components\CryptoCurrency::Usdc,
        paymentRail: Components\OfframpChain::Polygon,
        address: '0xdeadbeef',
        blockchainMemo: 'from_bridge',
    ),
    developerFeePercent: '0.1',
);

$response = $sdk->virtualAccounts->update(
    customerID: '<id>',
    virtualAccountID: '<id>',
    body: $body

);

if ($response->virtualAccountResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                          | Type                                                                               | Required                                                                           | Description                                                                        |
| ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| `customerID`                                                                       | *string*                                                                           | :heavy_check_mark:                                                                 | N/A                                                                                |
| `virtualAccountID`                                                                 | *string*                                                                           | :heavy_check_mark:                                                                 | N/A                                                                                |
| `body`                                                                             | [Components\UpdateVirtualAccount](../../Models/Components/UpdateVirtualAccount.md) | :heavy_check_mark:                                                                 | The Virtual Account details to be updated                                          |

### Response

**[?Operations\PutCustomersCustomerIDVirtualAccountsVirtualAccountIDResponse](../../Models/Operations/PutCustomersCustomerIDVirtualAccountsVirtualAccountIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## deactivate

Deactivate a Virtual Account to prevent it from acceping new incoming transactions

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/customers/{customerID}/virtual_accounts/{virtualAccountID}/deactivate" method="post" path="/customers/{customerID}/virtual_accounts/{virtualAccountID}/deactivate" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->virtualAccounts->deactivate(
    idempotencyKey: '<value>',
    customerID: '<id>',
    virtualAccountID: '<id>'

);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `idempotencyKey`   | *string*           | :heavy_check_mark: | N/A                |
| `customerID`       | *string*           | :heavy_check_mark: | N/A                |
| `virtualAccountID` | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\PostCustomersCustomerIDVirtualAccountsVirtualAccountIDDeactivateResponse](../../Models/Operations/PostCustomersCustomerIDVirtualAccountsVirtualAccountIDDeactivateResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## reactivate

Reactivate a previously deactivated Virtual Account

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/customers/{customerID}/virtual_accounts/{virtualAccountID}/reactivate" method="post" path="/customers/{customerID}/virtual_accounts/{virtualAccountID}/reactivate" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->virtualAccounts->reactivate(
    idempotencyKey: '<value>',
    customerID: '<id>',
    virtualAccountID: '<id>'

);

if ($response->virtualAccountResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `idempotencyKey`   | *string*           | :heavy_check_mark: | N/A                |
| `customerID`       | *string*           | :heavy_check_mark: | N/A                |
| `virtualAccountID` | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\PostCustomersCustomerIDVirtualAccountsVirtualAccountIDReactivateResponse](../../Models/Operations/PostCustomersCustomerIDVirtualAccountsVirtualAccountIDReactivateResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## customerHistory

History of activity for a Virtual Account

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/virtual_accounts/{virtualAccountID}/history" method="get" path="/customers/{customerID}/virtual_accounts/{virtualAccountID}/history" -->
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

$request = new Operations\GetCustomersCustomerIDVirtualAccountsVirtualAccountIDHistoryRequest(
    customerID: '<id>',
    virtualAccountID: '<id>',
);

$response = $sdk->virtualAccounts->customerHistory(
    request: $request
);

if ($response->virtualAccountHistory !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                                                                        | Type                                                                                                                                                                             | Required                                                                                                                                                                         | Description                                                                                                                                                                      |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `$request`                                                                                                                                                                       | [Operations\GetCustomersCustomerIDVirtualAccountsVirtualAccountIDHistoryRequest](../../Models/Operations/GetCustomersCustomerIDVirtualAccountsVirtualAccountIDHistoryRequest.md) | :heavy_check_mark:                                                                                                                                                               | The request object to use for the request.                                                                                                                                       |

### Response

**[?Operations\GetCustomersCustomerIDVirtualAccountsVirtualAccountIDHistoryResponse](../../Models/Operations/GetCustomersCustomerIDVirtualAccountsVirtualAccountIDHistoryResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## list

List all Virtual Account objects

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/virtual_accounts" method="get" path="/virtual_accounts" -->
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



$response = $sdk->virtualAccounts->list(
    status: Components\VirtualAccountActivationStatus::Activated
);

if ($response->virtualAccounts !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                                                                                                                                                       | Type                                                                                                                                                                                                                                                                                                                                                                                                                            | Required                                                                                                                                                                                                                                                                                                                                                                                                                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                     | Example                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `status`                                                                                                                                                                                                                                                                                                                                                                                                                        | [?Components\VirtualAccountActivationStatus](../../Models/Components/VirtualAccountActivationStatus.md)                                                                                                                                                                                                                                                                                                                         | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | Limit results to those with the given activation status                                                                                                                                                                                                                                                                                                                                                                         | activated                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `limit`                                                                                                                                                                                                                                                                                                                                                                                                                         | *?int*                                                                                                                                                                                                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | The number of items to return (default of 10, max of 100)                                                                                                                                                                                                                                                                                                                                                                       |                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `startingAfter`                                                                                                                                                                                                                                                                                                                                                                                                                 | *?string*                                                                                                                                                                                                                                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | This is a virtual account id. If this is specified, the next page that starts with a virtual account right AFTER the specified virtual account id on the virtual account timeline, which is always ordered from the newest to the oldest by creation time, will be returned. This also implies that virtual account older than the specified virtual account id will be returned (shouldn't be set if ending_before is set)     |                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `endingBefore`                                                                                                                                                                                                                                                                                                                                                                                                                  | *?string*                                                                                                                                                                                                                                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                              | This is a virtual account id. If this is specified, the previous page that ends with a virtual account right BEFORE the specified virtual account id on the virtual account timeline, which is always ordered from the newest to the oldest by creation time, will be returned. This also implies that virtual account newer than the specified virtual account id will be returned (shouldn't be set if starting_after is set) |                                                                                                                                                                                                                                                                                                                                                                                                                                 |

### Response

**[?Operations\GetVirtualAccountsResponse](../../Models/Operations/GetVirtualAccountsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getHistory

History of activity across all customers and Virtual Accounts

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/virtual_accounts/history" method="get" path="/virtual_accounts/history" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->virtualAccounts->getHistory(
    request: $request
);

if ($response->virtualAccountHistory !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                  | Type                                                                                                       | Required                                                                                                   | Description                                                                                                |
| ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| `$request`                                                                                                 | [Operations\GetVirtualAccountsHistoryRequest](../../Models/Operations/GetVirtualAccountsHistoryRequest.md) | :heavy_check_mark:                                                                                         | The request object to use for the request.                                                                 |

### Response

**[?Operations\GetVirtualAccountsHistoryResponse](../../Models/Operations/GetVirtualAccountsHistoryResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |