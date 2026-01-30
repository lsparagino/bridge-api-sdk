# BridgeWallets

## Overview

### Available Operations

* [list](#list) - Get all Bridge Wallets
* [getTotalBalances](#gettotalbalances) - Get total balances of all Bridge Wallets
* [getHistory](#gethistory) - Get transaction history for a Bridge Wallet
* [listByCustomer](#listbycustomer) - Get all Bridge Wallets for a customer
* [create](#create) - Create a Bridge Wallet
* [get](#get) - Get a Bridge Wallet

## list

List of Bridge Wallets

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/wallets" method="get" path="/wallets" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->bridgeWallets->list(

);

if ($response->bridgeWalletsList !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                                                                                                                                            | Type                                                                                                                                                                                                                                                                                                                                                                                                                 | Required                                                                                                                                                                                                                                                                                                                                                                                                             | Description                                                                                                                                                                                                                                                                                                                                                                                                          |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `limit`                                                                                                                                                                                                                                                                                                                                                                                                              | *?int*                                                                                                                                                                                                                                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                   | The number of items to return (default of 10, max of 100)                                                                                                                                                                                                                                                                                                                                                            |
| `startingAfter`                                                                                                                                                                                                                                                                                                                                                                                                      | *?string*                                                                                                                                                                                                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                   | This is a bridge wallet id. If this is specified, the next page that starts with a bridge wallet right AFTER the specified bridge wallet id on the bridge wallet timeline, which is always ordered from the newest to the oldest by creation time, will be returned. This also implies that bridge wallets older than the specified bridge wallet id will be returned (shouldn't be set if ending_before is set)     |
| `endingBefore`                                                                                                                                                                                                                                                                                                                                                                                                       | *?string*                                                                                                                                                                                                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                   | This is a bridge wallet id. If this is specified, the previous page that ends with a bridge wallet right BEFORE the specified bridge wallet id on the bridge wallet timeline, which is always ordered from the newest to the oldest by creation time, will be returned. This also implies that bridge wallets newer than the specified bridge wallet id will be returned (shouldn't be set if starting_after is set) |

### Response

**[?Operations\GetWalletsResponse](../../Models/Operations/GetWalletsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401, 404       | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getTotalBalances

Get the total balances of all Bridge Wallets

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/wallets/total_balances" method="get" path="/wallets/total_balances" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->bridgeWallets->getTotalBalances(

);

if ($response->bridgeWalletTotalBalances !== null) {
    // handle response
}
```

### Response

**[?Operations\GetWalletsTotalBalancesResponse](../../Models/Operations/GetWalletsTotalBalancesResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401, 404       | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getHistory

Get the list of transactions involving this Bridge Wallet

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/wallets/{bridgeWalletID}/history" method="get" path="/wallets/{bridgeWalletID}/history" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->bridgeWallets->getHistory(
    bridgeWalletID: '<id>'
);

if ($response->bridgeWalletHistory !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                       | Type                                                                                                                            | Required                                                                                                                        | Description                                                                                                                     |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `bridgeWalletID`                                                                                                                | *string*                                                                                                                        | :heavy_check_mark:                                                                                                              | N/A                                                                                                                             |
| `limit`                                                                                                                         | *?int*                                                                                                                          | :heavy_minus_sign:                                                                                                              | The number of items to return (default of 10, max of 100)                                                                       |
| `updatedAfterMs`                                                                                                                | *?int*                                                                                                                          | :heavy_minus_sign:                                                                                                              | This is a unix timestamp in milliseconds. If this is specified, objects updated AFTER the specified timestamp will be returned  |
| `updatedBeforeMs`                                                                                                               | *?int*                                                                                                                          | :heavy_minus_sign:                                                                                                              | This is a unix timestamp in milliseconds. If this is specified, objects updated BEFORE the specified timestamp will be returned |

### Response

**[?Operations\GetWalletsBridgeWalletIDHistoryResponse](../../Models/Operations/GetWalletsBridgeWalletIDHistoryResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401, 404       | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## listByCustomer

List of Bridge Wallets for the specified Customer ID

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/wallets" method="get" path="/customers/{customerID}/wallets" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->bridgeWallets->listByCustomer(
    customerID: '<id>'
);

if ($response->bridgeWalletsList !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                                                                                                                                            | Type                                                                                                                                                                                                                                                                                                                                                                                                                 | Required                                                                                                                                                                                                                                                                                                                                                                                                             | Description                                                                                                                                                                                                                                                                                                                                                                                                          |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `customerID`                                                                                                                                                                                                                                                                                                                                                                                                         | *string*                                                                                                                                                                                                                                                                                                                                                                                                             | :heavy_check_mark:                                                                                                                                                                                                                                                                                                                                                                                                   | N/A                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `limit`                                                                                                                                                                                                                                                                                                                                                                                                              | *?int*                                                                                                                                                                                                                                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                   | The number of items to return (default of 10, max of 100)                                                                                                                                                                                                                                                                                                                                                            |
| `startingAfter`                                                                                                                                                                                                                                                                                                                                                                                                      | *?string*                                                                                                                                                                                                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                   | This is a bridge wallet id. If this is specified, the next page that starts with a bridge wallet right AFTER the specified bridge wallet id on the bridge wallet timeline, which is always ordered from the newest to the oldest by creation time, will be returned. This also implies that bridge wallets older than the specified bridge wallet id will be returned (shouldn't be set if ending_before is set)     |
| `endingBefore`                                                                                                                                                                                                                                                                                                                                                                                                       | *?string*                                                                                                                                                                                                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                   | This is a bridge wallet id. If this is specified, the previous page that ends with a bridge wallet right BEFORE the specified bridge wallet id on the bridge wallet timeline, which is always ordered from the newest to the oldest by creation time, will be returned. This also implies that bridge wallets newer than the specified bridge wallet id will be returned (shouldn't be set if starting_after is set) |

### Response

**[?Operations\GetCustomersCustomerIDWalletsResponse](../../Models/Operations/GetCustomersCustomerIDWalletsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401, 404       | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## create

Create a Bridge Wallet

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/customers/{customerID}/wallets" method="post" path="/customers/{customerID}/wallets" -->
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

$body = new Components\CreateBridgeWallet(
    chain: Components\BridgeWalletChain::Solana,
);

$response = $sdk->bridgeWallets->create(
    customerID: '<id>',
    idempotencyKey: '<value>',
    body: $body

);

if ($response->createBridgeWalletResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                      | Type                                                                           | Required                                                                       | Description                                                                    |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| `customerID`                                                                   | *string*                                                                       | :heavy_check_mark:                                                             | N/A                                                                            |
| `idempotencyKey`                                                               | *string*                                                                       | :heavy_check_mark:                                                             | N/A                                                                            |
| `body`                                                                         | [Components\CreateBridgeWallet](../../Models/Components/CreateBridgeWallet.md) | :heavy_check_mark:                                                             | Bridge Wallet to be created                                                    |

### Response

**[?Operations\PostCustomersCustomerIDWalletsResponse](../../Models/Operations/PostCustomersCustomerIDWalletsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401, 404       | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## get

Retrieve a Bridge Wallet for the specified Bridge Wallet ID

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/wallets/{bridgeWalletID}" method="get" path="/customers/{customerID}/wallets/{bridgeWalletID}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->bridgeWallets->get(
    customerID: '<id>',
    bridgeWalletID: '<id>'

);

if ($response->bridgeWalletWithBalances !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `customerID`       | *string*           | :heavy_check_mark: | N/A                |
| `bridgeWalletID`   | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\GetCustomersCustomerIDWalletsBridgeWalletIDResponse](../../Models/Operations/GetCustomersCustomerIDWalletsBridgeWalletIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401, 404       | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |