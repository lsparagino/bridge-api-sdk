# LiquidationAddresses

## Overview

### Available Operations

* [create](#create) - Create a Liquidation Address
* [list](#list) - Get all Liquidation Addresses
* [getById](#getbyid) - Get a Liquidation Address
* [update](#update) - Update a Liquidation Address
* [getDrains](#getdrains) - Get drain history of a Liquidation Address
* [~~getBalance~~](#getbalance) - Get the balance of a Liquidation Address (deprecated) :warning: **Deprecated**
* [allDrains](#alldrains) - Liquidation Address Activity Across All Customers
* [listForCustomer](#listforcustomer) - Get all Liquidation Addresses for a customer

## create

Create a Liquidation Address

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/customers/{customerID}/liquidation_addresses" method="post" path="/customers/{customerID}/liquidation_addresses" -->
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

$body = new Components\CreateLiquidationAddress(
    currency: Components\LiquidationAddressSourceCurrency::Eurc,
    chain: Components\LiquidationAddressSourceChain::Stellar,
    customDeveloperFeePercent: '0.1',
);

$response = $sdk->liquidationAddresses->create(
    customerID: '<id>',
    idempotencyKey: '<value>',
    body: $body

);

if ($response->createLiquidationAddressResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                  | Type                                                                                       | Required                                                                                   | Description                                                                                |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| `customerID`                                                                               | *string*                                                                                   | :heavy_check_mark:                                                                         | N/A                                                                                        |
| `idempotencyKey`                                                                           | *string*                                                                                   | :heavy_check_mark:                                                                         | N/A                                                                                        |
| `body`                                                                                     | [Components\CreateLiquidationAddress](../../Models/Components/CreateLiquidationAddress.md) | :heavy_check_mark:                                                                         | Liquidation Address object to be created                                                   |

### Response

**[?Operations\PostCustomersCustomerIDLiquidationAddressesResponse](../../Models/Operations/PostCustomersCustomerIDLiquidationAddressesResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## list

Get Liquidation Addresses

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/liquidation_addresses" method="get" path="/liquidation_addresses" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->liquidationAddresses->list(

);

if ($response->liquidationAddresses !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                                                                                                                                                                               | Type                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Required                                                                                                                                                                                                                                                                                                                                                                                                                                                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `limit`                                                                                                                                                                                                                                                                                                                                                                                                                                                 | *?int*                                                                                                                                                                                                                                                                                                                                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                                                      | The number of items to return (default of 10, max of 100)                                                                                                                                                                                                                                                                                                                                                                                               |
| `startingAfter`                                                                                                                                                                                                                                                                                                                                                                                                                                         | *?string*                                                                                                                                                                                                                                                                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                                                      | This is a liquidation address id. If this is specified, the next page that starts with a liquidation address right AFTER the specified liquidation address id on the liquidation address timeline, which is always ordered from the newest to the oldest by creation time, will be returned. This also implies that liquidation address older than the specified liquidation address id will be returned (shouldn't be set if ending_before is set)     |
| `endingBefore`                                                                                                                                                                                                                                                                                                                                                                                                                                          | *?string*                                                                                                                                                                                                                                                                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                                                      | This is a liquidation address id. If this is specified, the previous page that ends with a liquidation address right BEFORE the specified liquidation address id on the liquidation address timeline, which is always ordered from the newest to the oldest by creation time, will be returned. This also implies that liquidation address newer than the specified liquidation address id will be returned (shouldn't be set if starting_after is set) |

### Response

**[?Operations\GetLiquidationAddressesResponse](../../Models/Operations/GetLiquidationAddressesResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getById

Retrieve a Liquidation Address for the specified Liquidation Address ID

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/liquidation_addresses/{liquidationAddressID}" method="get" path="/customers/{customerID}/liquidation_addresses/{liquidationAddressID}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->liquidationAddresses->getById(
    customerID: '<id>',
    liquidationAddressID: '<id>'

);

if ($response->liquidationAddress !== null) {
    // handle response
}
```

### Parameters

| Parameter              | Type                   | Required               | Description            |
| ---------------------- | ---------------------- | ---------------------- | ---------------------- |
| `customerID`           | *string*               | :heavy_check_mark:     | N/A                    |
| `liquidationAddressID` | *string*               | :heavy_check_mark:     | N/A                    |

### Response

**[?Operations\GetCustomersCustomerIDLiquidationAddressesLiquidationAddressIDResponse](../../Models/Operations/GetCustomersCustomerIDLiquidationAddressesLiquidationAddressIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401, 404       | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## update

Update a Liquidation Address for the specified liquidation address ID. Note that `external_account_id` and `custom_developer_fee_percent` can be updated independently and are not both required.

### Example Usage

<!-- UsageSnippet language="php" operationID="put_/customers/{customerID}/liquidation_addresses/{liquidationAddressID}" method="put" path="/customers/{customerID}/liquidation_addresses/{liquidationAddressID}" -->
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

$body = new Components\UpdateLiquidationAddress(
    customDeveloperFeePercent: '0.1',
);

$response = $sdk->liquidationAddresses->update(
    customerID: '<id>',
    liquidationAddressID: '<id>',
    body: $body

);

if ($response->liquidationAddress !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                  | Type                                                                                       | Required                                                                                   | Description                                                                                |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| `customerID`                                                                               | *string*                                                                                   | :heavy_check_mark:                                                                         | N/A                                                                                        |
| `liquidationAddressID`                                                                     | *string*                                                                                   | :heavy_check_mark:                                                                         | N/A                                                                                        |
| `body`                                                                                     | [Components\UpdateLiquidationAddress](../../Models/Components/UpdateLiquidationAddress.md) | :heavy_check_mark:                                                                         | Liquidation Address details to be updated                                                  |

### Response

**[?Operations\PutCustomersCustomerIDLiquidationAddressesLiquidationAddressIDResponse](../../Models/Operations/PutCustomersCustomerIDLiquidationAddressesLiquidationAddressIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getDrains

Get drain history of a Liquidation Address

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/liquidation_addresses/{liquidationAddressID}/drains" method="get" path="/customers/{customerID}/liquidation_addresses/{liquidationAddressID}/drains" -->
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

$request = new Operations\GetCustomersCustomerIDLiquidationAddressesLiquidationAddressIDDrainsRequest(
    customerID: '<id>',
    liquidationAddressID: '<id>',
);

$response = $sdk->liquidationAddresses->getDrains(
    request: $request
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                                                                                        | Type                                                                                                                                                                                             | Required                                                                                                                                                                                         | Description                                                                                                                                                                                      |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `$request`                                                                                                                                                                                       | [Operations\GetCustomersCustomerIDLiquidationAddressesLiquidationAddressIDDrainsRequest](../../Models/Operations/GetCustomersCustomerIDLiquidationAddressesLiquidationAddressIDDrainsRequest.md) | :heavy_check_mark:                                                                                                                                                                               | The request object to use for the request.                                                                                                                                                       |

### Response

**[?Operations\GetCustomersCustomerIDLiquidationAddressesLiquidationAddressIDDrainsResponse](../../Models/Operations/GetCustomersCustomerIDLiquidationAddressesLiquidationAddressIDDrainsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## ~~getBalance~~

Get the balance of a Liquidation Address. Note that most Liquidation Addresses no longer hold a balance. To check recent activity on a Liquidation Address, use the `/customers/{customerID}/liquidation_addresses/{liquidationAddressID}/drains` endpoint.

> :warning: **DEPRECATED**: This will be removed in a future release, please migrate away from it as soon as possible.

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/liquidation_addresses/{liquidationAddressID}/balances" method="get" path="/customers/{customerID}/liquidation_addresses/{liquidationAddressID}/balances" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->liquidationAddresses->getBalance(
    customerID: '<id>',
    liquidationAddressID: '<id>'

);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter              | Type                   | Required               | Description            |
| ---------------------- | ---------------------- | ---------------------- | ---------------------- |
| `customerID`           | *string*               | :heavy_check_mark:     | N/A                    |
| `liquidationAddressID` | *string*               | :heavy_check_mark:     | N/A                    |

### Response

**[?Operations\GetCustomersCustomerIDLiquidationAddressesLiquidationAddressIDBalancesResponse](../../Models/Operations/GetCustomersCustomerIDLiquidationAddressesLiquidationAddressIDBalancesResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## allDrains

History of activity across all customers and Liquidation Addresses

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/liquidation_addresses/drains" method="get" path="/liquidation_addresses/drains" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->liquidationAddresses->allDrains(
    request: $request
);

if ($response->liquidationAddressHistory !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                          | Type                                                                                                               | Required                                                                                                           | Description                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ |
| `$request`                                                                                                         | [Operations\GetLiquidationAddressesDrainsRequest](../../Models/Operations/GetLiquidationAddressesDrainsRequest.md) | :heavy_check_mark:                                                                                                 | The request object to use for the request.                                                                         |

### Response

**[?Operations\GetLiquidationAddressesDrainsResponse](../../Models/Operations/GetLiquidationAddressesDrainsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## listForCustomer

Get Liquidation Addresses

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/liquidation_addresses" method="get" path="/customers/{customerID}/liquidation_addresses" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->liquidationAddresses->listForCustomer(
    customerID: '<id>'
);

if ($response->liquidationAddresses !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                                                                                                                                                                               | Type                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Required                                                                                                                                                                                                                                                                                                                                                                                                                                                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `customerID`                                                                                                                                                                                                                                                                                                                                                                                                                                            | *string*                                                                                                                                                                                                                                                                                                                                                                                                                                                | :heavy_check_mark:                                                                                                                                                                                                                                                                                                                                                                                                                                      | N/A                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `limit`                                                                                                                                                                                                                                                                                                                                                                                                                                                 | *?int*                                                                                                                                                                                                                                                                                                                                                                                                                                                  | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                                                      | The number of items to return (default of 10, max of 100)                                                                                                                                                                                                                                                                                                                                                                                               |
| `startingAfter`                                                                                                                                                                                                                                                                                                                                                                                                                                         | *?string*                                                                                                                                                                                                                                                                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                                                      | This is a liquidation address id. If this is specified, the next page that starts with a liquidation address right AFTER the specified liquidation address id on the liquidation address timeline, which is always ordered from the newest to the oldest by creation time, will be returned. This also implies that liquidation address older than the specified liquidation address id will be returned (shouldn't be set if ending_before is set)     |
| `endingBefore`                                                                                                                                                                                                                                                                                                                                                                                                                                          | *?string*                                                                                                                                                                                                                                                                                                                                                                                                                                               | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                                                      | This is a liquidation address id. If this is specified, the previous page that ends with a liquidation address right BEFORE the specified liquidation address id on the liquidation address timeline, which is always ordered from the newest to the oldest by creation time, will be returned. This also implies that liquidation address newer than the specified liquidation address id will be returned (shouldn't be set if starting_after is set) |

### Response

**[?Operations\GetCustomersCustomerIDLiquidationAddressesResponse](../../Models/Operations/GetCustomersCustomerIDLiquidationAddressesResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |