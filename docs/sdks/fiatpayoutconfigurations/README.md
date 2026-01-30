# FiatPayoutConfigurations

## Overview

### Available Operations

* [get](#get) - Get the fiat payout configuration for a customer
* [update](#update) - Update the fiat payout configuration for a customer

## get

Retrieve the fiat payout configuration for the given customer ID. This configuration determines which payout method (bridge, developer, payment_provider, or customer) is used for each currency and payment rail combination.

The configuration is a nested hash structure where:
- Top-level keys are currency codes (e.g., "usd", "eur", "brl", "mxn")
- Second-level keys are payment rail codes (e.g., "wire", "ach", "sepa", "pix", "spei")
- Values are payout names: `bridge`, `developer`, `payment_provider`, or `customer`

Currently, only the following values are supported for the payout method:
- usd.wire: `developer`, `customer`
- usd.ach: `bridge`
- eur.sepa: `bridge`
- brl.pix: `payment_provider`
- mxn.spei: `payment_provider`


### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/fiat_payout_configuration" method="get" path="/customers/{customerID}/fiat_payout_configuration" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->fiatPayoutConfigurations->get(
    customerID: '<id>'
);

if ($response->fiatPayoutConfigurationResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `customerID`       | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\GetCustomersCustomerIDFiatPayoutConfigurationResponse](../../Models/Operations/GetCustomersCustomerIDFiatPayoutConfigurationResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401, 404            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## update

Update the fiat payout configuration for the given customer ID. This configuration determines which payout method (bridge, developer, payment_provider, or customer) is used for each currency and payment rail combination.

The configuration is a nested hash structure where:
- Top-level keys are currency codes (e.g., "usd", "eur", "brl", "mxn")
- Second-level keys are payment rail codes (e.g., "wire", "ach", "sepa", "pix", "spei")
- Values are payout names: `bridge`, `developer`, `payment_provider`, or `customer`

Currently, only the following values are supported for the payout method:
- usd.wire: `developer`, `customer`
- usd.ach: `bridge`
- eur.sepa: `bridge`
- brl.pix: `payment_provider`
- mxn.spei: `payment_provider`

Only the currency/payment rail combinations provided will be updated. Other existing configurations will remain unchanged.


### Example Usage

<!-- UsageSnippet language="php" operationID="patch_/customers/{customerID}/fiat_payout_configuration" method="patch" path="/customers/{customerID}/fiat_payout_configuration" -->
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

$body = new Components\PatchFiatPayoutConfigurationInput(
    fiatPayoutConfiguration: new Components\FiatPayoutConfiguration(
        usd: new Components\Usd(
            wire: Components\Wire::Developer,
            ach: Components\AchEnum::Bridge,
        ),
        eur: new Components\Eur(
            sepa: Components\Sepa::Bridge,
        ),
        brl: new Components\Brl(
            pix: Components\PixEnum::PaymentProvider,
        ),
        mxn: new Components\Mxn(
            spei: Components\Spei::PaymentProvider,
        ),
    ),
);

$response = $sdk->fiatPayoutConfigurations->update(
    customerID: '<id>',
    body: $body

);

if ($response->fiatPayoutConfigurationResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                    | Type                                                                                                         | Required                                                                                                     | Description                                                                                                  | Example                                                                                                      |
| ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ |
| `customerID`                                                                                                 | *string*                                                                                                     | :heavy_check_mark:                                                                                           | N/A                                                                                                          |                                                                                                              |
| `body`                                                                                                       | [Components\PatchFiatPayoutConfigurationInput](../../Models/Components/PatchFiatPayoutConfigurationInput.md) | :heavy_check_mark:                                                                                           | Fiat payout configuration to update                                                                          | {<br/>"usd": {<br/>"wire": "customer"<br/>}<br/>}                                                            |

### Response

**[?Operations\PatchCustomersCustomerIDFiatPayoutConfigurationResponse](../../Models/Operations/PatchCustomersCustomerIDFiatPayoutConfigurationResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401, 403, 404  | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |