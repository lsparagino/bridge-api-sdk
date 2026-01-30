# Developers

## Overview

### Available Operations

* [getFees](#getfees) - Get the configured fees
* [updateFees](#updatefees) - Update the configured fees
* [getFeeExternalAccount](#getfeeexternalaccount) - Get the configured fee External Account
* [configureFeeExternalAccount](#configurefeeexternalaccount) - Configure a fee External Account

## getFees

Get fees that have been configured for supported products.

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/developer/fees" method="get" path="/developer/fees" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->developers->getFees(

);

if ($response->developerFees !== null) {
    // handle response
}
```

### Response

**[?Operations\GetDeveloperFeesResponse](../../Models/Operations/GetDeveloperFeesResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## updateFees

Update fees for supported products.

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/developer/fees" method="post" path="/developer/fees" -->
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

$body = new Components\DeveloperFees(
    defaultLiquidationAddressFeePercent: '0.5',
);

$response = $sdk->developers->updateFees(
    idempotencyKey: '<value>',
    body: $body

);

if ($response->statusCode === 200) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                                          | Type                                                                                                                                               | Required                                                                                                                                           | Description                                                                                                                                        |
| -------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| `idempotencyKey`                                                                                                                                   | *string*                                                                                                                                           | :heavy_check_mark:                                                                                                                                 | N/A                                                                                                                                                |
| `body`                                                                                                                                             | [Components\DeveloperFees](../../Models/Components/DeveloperFees.md)                                                                               | :heavy_check_mark:                                                                                                                                 | The default fee percent that will be applied to all your Liquidation Addresses. The value is a base 100 percentage, i.e. 10.2% is 10.2 in the API. |

### Response

**[?Operations\PostDeveloperFeesResponse](../../Models/Operations/PostDeveloperFeesResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getFeeExternalAccount

Get the configured fee External Account.

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/developer/fee_external_account" method="get" path="/developer/fee_external_account" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->developers->getFeeExternalAccount(

);

if ($response->feeExternalAccount !== null) {
    // handle response
}
```

### Response

**[?Operations\GetDeveloperFeeExternalAccountResponse](../../Models/Operations/GetDeveloperFeeExternalAccountResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## configureFeeExternalAccount

Configure a fee External Account.

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/developer/fee_external_account" method="post" path="/developer/fee_external_account" -->
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



$response = $sdk->developers->configureFeeExternalAccount(
    idempotencyKey: '<value>',
    body: new Components\CreateFeeExternalAccountInputACHWire(
        accountType: Components\BankAccountNumberType::Us,
        currency: Components\CreateFeeExternalAccountInputCurrency1::Usd,
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
    )

);

if ($response->feeExternalAccount !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                                                                                                                                | Type                                                                                                                                                                                                                                                                                                                                                                                                     | Required                                                                                                                                                                                                                                                                                                                                                                                                 | Description                                                                                                                                                                                                                                                                                                                                                                                              |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `idempotencyKey`                                                                                                                                                                                                                                                                                                                                                                                         | *string*                                                                                                                                                                                                                                                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                                                                                                                                                                      |
| `body`                                                                                                                                                                                                                                                                                                                                                                                                   | [Components\CreateFeeExternalAccountInputACHWire\|Components\CreateFeeExternalAccountInputIBAN\|Components\CreateFeeExternalAccountInputSWIFT\|Components\CreateFeeExternalAccountInputCLABE\|Components\CreateFeeExternalAccountInputPixPixKey\|Components\CreateFeeExternalAccountInputPixBRCode\|Components\CreateFeeExternalAccountInputFPSBeta](../../Models/Components/CreateFeeExternalAccountInput.md) | :heavy_check_mark:                                                                                                                                                                                                                                                                                                                                                                                       | New External Account object to be created                                                                                                                                                                                                                                                                                                                                                                |

### Response

**[?Operations\PostDeveloperFeeExternalAccountResponse](../../Models/Operations/PostDeveloperFeeExternalAccountResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |