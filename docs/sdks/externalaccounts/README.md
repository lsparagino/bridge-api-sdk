# ExternalAccounts

## Overview

### Available Operations

* [listForCustomer](#listforcustomer) - Get all External Accounts
* [get](#get) - Retrieve an External Account object
* [list](#list) - Get all External Accounts
* [create](#create) - Create a new External Account
* [update](#update) - Update an External Account
* [delete](#delete) - Delete a single External Account object
* [reactivate](#reactivate) - Reactivate an External Account

## listForCustomer

Get all External Accounts for a passed in customer.

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/external_accounts" method="get" path="/customers/{customerID}/external_accounts" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->externalAccounts->listForCustomer(
    customerID: '<id>'
);

if ($response->externalAccount !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                                                                                                                                                                | Type                                                                                                                                                                                                                                                                                                                                                                                                                                     | Required                                                                                                                                                                                                                                                                                                                                                                                                                                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `customerID`                                                                                                                                                                                                                                                                                                                                                                                                                             | *string*                                                                                                                                                                                                                                                                                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                                                                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `limit`                                                                                                                                                                                                                                                                                                                                                                                                                                  | *?int*                                                                                                                                                                                                                                                                                                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                                       | The number of items to return (default of 10, max of 100)                                                                                                                                                                                                                                                                                                                                                                                |
| `startingAfter`                                                                                                                                                                                                                                                                                                                                                                                                                          | *?string*                                                                                                                                                                                                                                                                                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                                       | This is an external account id. If this is specified, the next page that starts with an external account right AFTER the specified external account id on the external account timeline, which is always ordered from the newest to the oldest by creation time, will be returned. This also implies that external accounts older than the specified external account id will be returned (shouldn't be set if ending_before is set)     |
| `endingBefore`                                                                                                                                                                                                                                                                                                                                                                                                                           | *?string*                                                                                                                                                                                                                                                                                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                                       | This is an external account id. If this is specified, the previous page that ends with an external account right BEFORE the specified external account id on the external account timeline, which is always ordered from the newest to the oldest by creation time, will be returned. This also implies that external accounts newer than the specified external account id will be returned (shouldn't be set if starting_after is set) |

### Response

**[?Operations\GetCustomersCustomerIDExternalAccountsResponse](../../Models/Operations/GetCustomersCustomerIDExternalAccountsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## get

Retrieve an External Account object (banks, debit cards etc) from the passed in customer ID and External Account ID

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/external_accounts/{externalAccountID}" method="get" path="/customers/{customerID}/external_accounts/{externalAccountID}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->externalAccounts->get(
    customerID: '<id>',
    externalAccountID: '<id>'

);

if ($response->externalAccountResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter           | Type                | Required            | Description         |
| ------------------- | ------------------- | ------------------- | ------------------- |
| `customerID`        | *string*            | :heavy_check_mark:  | N/A                 |
| `externalAccountID` | *string*            | :heavy_check_mark:  | N/A                 |

### Response

**[?Operations\GetCustomersCustomerIDExternalAccountsExternalAccountIDResponse](../../Models/Operations/GetCustomersCustomerIDExternalAccountsExternalAccountIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401, 404            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## list

Get all External Accounts.

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/external_accounts" method="get" path="/external_accounts" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->externalAccounts->list(

);

if ($response->externalAccount !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                                                                                                                                                                | Type                                                                                                                                                                                                                                                                                                                                                                                                                                     | Required                                                                                                                                                                                                                                                                                                                                                                                                                                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `limit`                                                                                                                                                                                                                                                                                                                                                                                                                                  | *?int*                                                                                                                                                                                                                                                                                                                                                                                                                                   | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                                       | The number of items to return (default of 10, max of 100)                                                                                                                                                                                                                                                                                                                                                                                |
| `startingAfter`                                                                                                                                                                                                                                                                                                                                                                                                                          | *?string*                                                                                                                                                                                                                                                                                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                                       | This is an external account id. If this is specified, the next page that starts with an external account right AFTER the specified external account id on the external account timeline, which is always ordered from the newest to the oldest by creation time, will be returned. This also implies that external accounts older than the specified external account id will be returned (shouldn't be set if ending_before is set)     |
| `endingBefore`                                                                                                                                                                                                                                                                                                                                                                                                                           | *?string*                                                                                                                                                                                                                                                                                                                                                                                                                                | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                                       | This is an external account id. If this is specified, the previous page that ends with an external account right BEFORE the specified external account id on the external account timeline, which is always ordered from the newest to the oldest by creation time, will be returned. This also implies that external accounts newer than the specified external account id will be returned (shouldn't be set if starting_after is set) |

### Response

**[?Operations\GetExternalAccountsResponse](../../Models/Operations/GetExternalAccountsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## create

_Note_: If adding US external accounts, we recommend reading through the US Beneficiary Address Validation doc ([link](https://apidocs.bridge.xyz/docs/us-beneficiary-address-validation)) to avoid issues related to incorrect addresses.


### Example Usage

<!-- UsageSnippet language="php" operationID="post_/customers/{customerID}/external_accounts" method="post" path="/customers/{customerID}/external_accounts" -->
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

$request = new Operations\PostCustomersCustomerIDExternalAccountsRequest(
    customerID: '<id>',
    idempotencyKey: '<value>',
    body: new Components\CreateExternalAccountInputACHWire(
        accountType: Components\BankAccountNumberType::Us,
        currency: Components\EuroInclusiveFiatCurrency::Usd,
        bankName: 'Wells Fargo',
        accountOwnerName: 'John Doe',
        account: new Components\UsBankAccountInput(
            accountNumber: '1210002481111',
            routingNumber: '121000248',
            checkingOrSavings: Components\CheckingOrSavingsType::Checking,
        ),
        address: new Components\ExternalAccountAddress(
            streetLine1: '123 Main St',
            city: 'San Francisco',
            state: 'CA',
            postalCode: '94102',
            country: 'USA',
        ),
    ),
);

$response = $sdk->externalAccounts->create(
    request: $request
);

if ($response->externalAccountResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                              | Type                                                                                                                                   | Required                                                                                                                               | Description                                                                                                                            |
| -------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| `$request`                                                                                                                             | [Operations\PostCustomersCustomerIDExternalAccountsRequest](../../Models/Operations/PostCustomersCustomerIDExternalAccountsRequest.md) | :heavy_check_mark:                                                                                                                     | The request object to use for the request.                                                                                             |

### Response

**[?Operations\PostCustomersCustomerIDExternalAccountsResponse](../../Models/Operations/PostCustomersCustomerIDExternalAccountsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## update

Update an External Account

### Example Usage

<!-- UsageSnippet language="php" operationID="put_/customers/{customerID}/external_accounts/{externalAccountID}" method="put" path="/customers/{customerID}/external_accounts/{externalAccountID}" -->
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

$body = new Components\UpdateExternalAccountInput(
    address: new Components\Address(
        streetLine1: '<value>',
        city: 'Evalynside',
        country: 'Peru',
    ),
);

$response = $sdk->externalAccounts->update(
    customerID: '<id>',
    externalAccountID: '<id>',
    body: $body

);

if ($response->externalAccountResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                      | Type                                                                                           | Required                                                                                       | Description                                                                                    |
| ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| `customerID`                                                                                   | *string*                                                                                       | :heavy_check_mark:                                                                             | N/A                                                                                            |
| `externalAccountID`                                                                            | *string*                                                                                       | :heavy_check_mark:                                                                             | N/A                                                                                            |
| `body`                                                                                         | [Components\UpdateExternalAccountInput](../../Models/Components/UpdateExternalAccountInput.md) | :heavy_check_mark:                                                                             | External Account details to be updated                                                         |

### Response

**[?Operations\PutCustomersCustomerIDExternalAccountsExternalAccountIDResponse](../../Models/Operations/PutCustomersCustomerIDExternalAccountsExternalAccountIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## delete

Delete an External Account object from the passed in External Account ID

### Example Usage

<!-- UsageSnippet language="php" operationID="delete_/customers/{customerID}/external_accounts/{externalAccountID}" method="delete" path="/customers/{customerID}/external_accounts/{externalAccountID}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->externalAccounts->delete(
    customerID: '<id>',
    externalAccountID: '<id>'

);

if ($response->externalAccountResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter           | Type                | Required            | Description         |
| ------------------- | ------------------- | ------------------- | ------------------- |
| `customerID`        | *string*            | :heavy_check_mark:  | N/A                 |
| `externalAccountID` | *string*            | :heavy_check_mark:  | N/A                 |

### Response

**[?Operations\DeleteCustomersCustomerIDExternalAccountsExternalAccountIDResponse](../../Models/Operations/DeleteCustomersCustomerIDExternalAccountsExternalAccountIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401, 404            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## reactivate

Reactivate a previously deactivated External Account

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/customers/{customerID}/external_accounts/{externalAccountID}/reactivate" method="post" path="/customers/{customerID}/external_accounts/{externalAccountID}/reactivate" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->externalAccounts->reactivate(
    idempotencyKey: '<value>',
    customerID: '<id>',
    externalAccountID: '<id>'

);

if ($response->externalAccountResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter           | Type                | Required            | Description         |
| ------------------- | ------------------- | ------------------- | ------------------- |
| `idempotencyKey`    | *string*            | :heavy_check_mark:  | N/A                 |
| `customerID`        | *string*            | :heavy_check_mark:  | N/A                 |
| `externalAccountID` | *string*            | :heavy_check_mark:  | N/A                 |

### Response

**[?Operations\PostCustomersCustomerIDExternalAccountsExternalAccountIDReactivateResponse](../../Models/Operations/PostCustomersCustomerIDExternalAccountsExternalAccountIDReactivateResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |