# rethink/bridgesdk

Developer-friendly & type-safe Php SDK specifically catered to leverage *rethink/bridgesdk* API.

[![Built by Speakeasy](https://img.shields.io/badge/Built_by-SPEAKEASY-374151?style=for-the-badge&labelColor=f3f4f6)](https://www.speakeasy.com/?utm_source=rethink/bridgesdk&utm_campaign=php)
[![License: MIT](https://img.shields.io/badge/LICENSE_//_MIT-3b5bdb?style=for-the-badge&labelColor=eff6ff)](https://opensource.org/licenses/MIT)


<!-- Start Summary [summary] -->
## Summary

Bridge API: APIs to move into, out of, and between any form of a dollar
<!-- End Summary [summary] -->

<!-- Start Table of Contents [toc] -->
## Table of Contents
<!-- $toc-max-depth=2 -->
* [rethink/bridgesdk](#rethinkbridgesdk)
  * [SDK Installation](#sdk-installation)
  * [SDK Example Usage](#sdk-example-usage)
  * [Authentication](#authentication)
  * [Available Resources and Operations](#available-resources-and-operations)
  * [Error Handling](#error-handling)
  * [Server Selection](#server-selection)
* [Development](#development)
  * [Maturity](#maturity)
  * [Contributions](#contributions)

<!-- End Table of Contents [toc] -->

<!-- Start SDK Installation [installation] -->
## SDK Installation

> [!TIP]
> To finish publishing your SDK you must [run your first generation action](https://www.speakeasy.com/docs/github-setup#step-by-step-guide).


The SDK relies on [Composer](https://getcomposer.org/) to manage its dependencies.

To install the SDK first add the below to your `composer.json` file:

```json
{
    "repositories": [
        {
            "type": "github",
            "url": "<UNSET>.git"
        }
    ],
    "require": {
        "rethink/bridgesdk": "*"
    }
}
```

Then run the following command:

```bash
composer update
```
<!-- End SDK Installation [installation] -->

<!-- Start SDK Example Usage [usage] -->
## SDK Example Usage

### Example

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
<!-- End SDK Example Usage [usage] -->

<!-- Start Authentication [security] -->
## Authentication

### Per-Client Security Schemes

This SDK supports the following security scheme globally:

| Name     | Type   | Scheme  |
| -------- | ------ | ------- |
| `apiKey` | apiKey | API key |

To authenticate with the API the `apiKey` parameter must be set when initializing the SDK. For example:
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
<!-- End Authentication [security] -->

<!-- Start Available Resources and Operations [operations] -->
## Available Resources and Operations

<details open>
<summary>Available methods</summary>

### [AssociatedPersons](docs/sdks/associatedpersons/README.md)

* [get](docs/sdks/associatedpersons/README.md#get) - Get a single associated person (Beta)
* [delete](docs/sdks/associatedpersons/README.md#delete) - Delete a single associated person
* [update](docs/sdks/associatedpersons/README.md#update) - Update a single associated person

### [BatchSettlements](docs/sdks/batchsettlements/README.md)

* [create](docs/sdks/batchsettlements/README.md#create) - Create a Batch Settlement Schedule

### [BridgeWallets](docs/sdks/bridgewallets/README.md)

* [list](docs/sdks/bridgewallets/README.md#list) - Get all Bridge Wallets
* [getTotalBalances](docs/sdks/bridgewallets/README.md#gettotalbalances) - Get total balances of all Bridge Wallets
* [getHistory](docs/sdks/bridgewallets/README.md#gethistory) - Get transaction history for a Bridge Wallet
* [listByCustomer](docs/sdks/bridgewallets/README.md#listbycustomer) - Get all Bridge Wallets for a customer
* [create](docs/sdks/bridgewallets/README.md#create) - Create a Bridge Wallet
* [get](docs/sdks/bridgewallets/README.md#get) - Get a Bridge Wallet

### [Cards](docs/sdks/cards/README.md)

* [createPinUpdateUrl](docs/sdks/cards/README.md#createpinupdateurl) - Create Card PIN Update URL
* [generateEphemeralKey](docs/sdks/cards/README.md#generateephemeralkey) - Generate an Ephemeral Key to Reveal Card Details
* [getSummary](docs/sdks/cards/README.md#getsummary) - Get a summary of your card program
* [getDesigns](docs/sdks/cards/README.md#getdesigns) - Get a listing of your card program's card designs
* [get](docs/sdks/cards/README.md#get) - Retrieve a card account
* [list](docs/sdks/cards/README.md#list) - Get all card accounts
* [provisionAccount](docs/sdks/cards/README.md#provisionaccount) - Provision a card account
* [freeze](docs/sdks/cards/README.md#freeze) - Place a freeze on the card account
* [unfreeze](docs/sdks/cards/README.md#unfreeze) - Unfreeze the card account
* [createMobileWalletProvisioningRequest](docs/sdks/cards/README.md#createmobilewalletprovisioningrequest) - Create a mobile wallet push provisioning request
* [listAuthorizations](docs/sdks/cards/README.md#listauthorizations) - Retrieve pending card authorizations
* [getTransactions](docs/sdks/cards/README.md#gettransactions) - Retrieve card transactions
* [getTransaction](docs/sdks/cards/README.md#gettransaction) - Retrieve a card transaction
* [getAuthControls](docs/sdks/cards/README.md#getauthcontrols) - Retrieve authorization controls
* [provisionDepositAddress](docs/sdks/cards/README.md#provisiondepositaddress) - Provision an additional top-up deposit address for the card account
* [createWithdrawal](docs/sdks/cards/README.md#createwithdrawal) - Create a funds withdrawal request
* [listWithdrawals](docs/sdks/cards/README.md#listwithdrawals) - Retrieve the withdrawal history of funds
* [getWithdrawal](docs/sdks/cards/README.md#getwithdrawal) - Retrieve a card withdrawal
* [generateStatement](docs/sdks/cards/README.md#generatestatement) - Generate a card account statement

### [CryptoReturnPolicies](docs/sdks/cryptoreturnpolicies/README.md)

* [getAll](docs/sdks/cryptoreturnpolicies/README.md#getall) - Get all crypto return policies
* [create](docs/sdks/cryptoreturnpolicies/README.md#create) - Create a new crypto return policy
* [delete](docs/sdks/cryptoreturnpolicies/README.md#delete) - Delete a single crypto return policy object
* [update](docs/sdks/cryptoreturnpolicies/README.md#update) - Update an existing crypto return policy

### [Customers](docs/sdks/customers/README.md)

* [list](docs/sdks/customers/README.md#list) - Get all customers
* [create](docs/sdks/customers/README.md#create) - Create a customer
* [get](docs/sdks/customers/README.md#get) - Get a single customer object
* [update](docs/sdks/customers/README.md#update) - Update a single customer object
* [delete](docs/sdks/customers/README.md#delete) - Delete a single customer object
* [getAssociatedPersons](docs/sdks/customers/README.md#getassociatedpersons) - Get associated persons for a business customer (Beta)
* [addAssociatedPerson](docs/sdks/customers/README.md#addassociatedperson) - Create a new associated person for a business customer (Beta)
* [getAssociatedPerson](docs/sdks/customers/README.md#getassociatedperson) - Get a single associated person (Beta)
* [updateAssociatedPerson](docs/sdks/customers/README.md#updateassociatedperson) - Update a single associated person
* [deleteAssociatedPerson](docs/sdks/customers/README.md#deleteassociatedperson) - Delete a single associated person
* [getTosAcceptanceLink](docs/sdks/customers/README.md#gettosacceptancelink) - Retrieve a hosted URL for ToS acceptance for an existing customer
* [getKycLink](docs/sdks/customers/README.md#getkyclink) - Retrieve a hosted KYC Link for an existing customer
* [getTransfers](docs/sdks/customers/README.md#gettransfers) - Get all transfers
* [getStaticTemplates](docs/sdks/customers/README.md#getstatictemplates) - Get all static templates for a customer
* [createTosLink](docs/sdks/customers/README.md#createtoslink) - Request a hosted URL for ToS acceptance for new customer creation

### [Developers](docs/sdks/developers/README.md)

* [getFees](docs/sdks/developers/README.md#getfees) - Get the configured fees
* [updateFees](docs/sdks/developers/README.md#updatefees) - Update the configured fees
* [getFeeExternalAccount](docs/sdks/developers/README.md#getfeeexternalaccount) - Get the configured fee External Account
* [configureFeeExternalAccount](docs/sdks/developers/README.md#configurefeeexternalaccount) - Configure a fee External Account

### [ExchangeRates](docs/sdks/exchangerates/README.md)

* [get](docs/sdks/exchangerates/README.md#get) - Get current exchange rate between two currencies.

### [ExternalAccounts](docs/sdks/externalaccounts/README.md)

* [listForCustomer](docs/sdks/externalaccounts/README.md#listforcustomer) - Get all External Accounts
* [get](docs/sdks/externalaccounts/README.md#get) - Retrieve an External Account object
* [list](docs/sdks/externalaccounts/README.md#list) - Get all External Accounts
* [create](docs/sdks/externalaccounts/README.md#create) - Create a new External Account
* [update](docs/sdks/externalaccounts/README.md#update) - Update an External Account
* [delete](docs/sdks/externalaccounts/README.md#delete) - Delete a single External Account object
* [reactivate](docs/sdks/externalaccounts/README.md#reactivate) - Reactivate an External Account

### [FiatPayoutConfigurations](docs/sdks/fiatpayoutconfigurations/README.md)

* [get](docs/sdks/fiatpayoutconfigurations/README.md#get) - Get the fiat payout configuration for a customer
* [update](docs/sdks/fiatpayoutconfigurations/README.md#update) - Update the fiat payout configuration for a customer

### [FundsRequests](docs/sdks/fundsrequests/README.md)

* [list](docs/sdks/fundsrequests/README.md#list) - Get all funds requests

### [KycLinks](docs/sdks/kyclinks/README.md)

* [generate](docs/sdks/kyclinks/README.md#generate) - Generate the Links needs to complete KYC for an individual or business
* [list](docs/sdks/kyclinks/README.md#list) - Get all KYC links.
* [getById](docs/sdks/kyclinks/README.md#getbyid) - Check the status of a KYC link

### [LiquidationAddresses](docs/sdks/liquidationaddresses/README.md)

* [create](docs/sdks/liquidationaddresses/README.md#create) - Create a Liquidation Address
* [list](docs/sdks/liquidationaddresses/README.md#list) - Get all Liquidation Addresses
* [getById](docs/sdks/liquidationaddresses/README.md#getbyid) - Get a Liquidation Address
* [update](docs/sdks/liquidationaddresses/README.md#update) - Update a Liquidation Address
* [getDrains](docs/sdks/liquidationaddresses/README.md#getdrains) - Get drain history of a Liquidation Address
* [~~getBalance~~](docs/sdks/liquidationaddresses/README.md#getbalance) - Get the balance of a Liquidation Address (deprecated) :warning: **Deprecated**
* [allDrains](docs/sdks/liquidationaddresses/README.md#alldrains) - Liquidation Address Activity Across All Customers
* [listForCustomer](docs/sdks/liquidationaddresses/README.md#listforcustomer) - Get all Liquidation Addresses for a customer

### [Lists](docs/sdks/lists/README.md)

* [getOccupationCodes](docs/sdks/lists/README.md#getoccupationcodes) - Get occupation codes
* [listCountries](docs/sdks/lists/README.md#listcountries) - Get countries

### [Plaid](docs/sdks/plaid/README.md)

* [createLinkRequest](docs/sdks/plaid/README.md#createlinkrequest) - Generate a Plaid Link token for a customer
* [exchangePublicToken](docs/sdks/plaid/README.md#exchangepublictoken) - Exchange Plaid public token for an access token

### [PrefundedAccounts](docs/sdks/prefundedaccounts/README.md)

* [list](docs/sdks/prefundedaccounts/README.md#list) - Get a list of all Prefunded Account
* [get](docs/sdks/prefundedaccounts/README.md#get) - Get details for a specific Prefunded Account
* [getHistory](docs/sdks/prefundedaccounts/README.md#gethistory) - Get funding history of a Prefunded Account

### [Rewards](docs/sdks/rewards/README.md)

* [getRates](docs/sdks/rewards/README.md#getrates) - Get the current reward rates
* [summary](docs/sdks/rewards/README.md#summary) - Get a summary of all rewards for a given stablecoin
* [currencyRates](docs/sdks/rewards/README.md#currencyrates) - Get the currency reward rates for a given stablecoin
* [getSummary](docs/sdks/rewards/README.md#getsummary) - Get a summary of a customer's rewards
* [getCustomerHistory](docs/sdks/rewards/README.md#getcustomerhistory) - Get a history of a customer's rewards

### [StaticMemos](docs/sdks/staticmemos/README.md)

* [list](docs/sdks/staticmemos/README.md#list) - List Static Memos
* [create](docs/sdks/staticmemos/README.md#create) - Create a Static Memo
* [listByCustomer](docs/sdks/staticmemos/README.md#listbycustomer) - List Static Memos for Customer
* [get](docs/sdks/staticmemos/README.md#get) - Get a Static Memo
* [update](docs/sdks/staticmemos/README.md#update) - Update a Static Memo
* [getHistoryForCustomer](docs/sdks/staticmemos/README.md#gethistoryforcustomer) - Static Memo Activity
* [getHistory](docs/sdks/staticmemos/README.md#gethistory) - Static Memo Activity Across All Customers

### [Transfers](docs/sdks/transfers/README.md)

* [get](docs/sdks/transfers/README.md#get) - Get all transfers
* [create](docs/sdks/transfers/README.md#create) - Create a transfer
* [getById](docs/sdks/transfers/README.md#getbyid) - Get a transfer
* [update](docs/sdks/transfers/README.md#update) - Update a transfer
* [delete](docs/sdks/transfers/README.md#delete) - Delete a transfer
* [listStaticTemplates](docs/sdks/transfers/README.md#liststatictemplates) - Get all static templates

### [VirtualAccounts](docs/sdks/virtualaccounts/README.md)

* [create](docs/sdks/virtualaccounts/README.md#create) - Create a Virtual Account
* [listByCustomer](docs/sdks/virtualaccounts/README.md#listbycustomer) - List Virtual Accounts by Customer
* [get](docs/sdks/virtualaccounts/README.md#get) - Get a Virtual Account
* [update](docs/sdks/virtualaccounts/README.md#update) - Update a Virtual Account
* [deactivate](docs/sdks/virtualaccounts/README.md#deactivate) - Deactivate a Virtual Account
* [reactivate](docs/sdks/virtualaccounts/README.md#reactivate) - Reactivate a Virtual Account
* [customerHistory](docs/sdks/virtualaccounts/README.md#customerhistory) - Virtual Account Activity
* [list](docs/sdks/virtualaccounts/README.md#list) - List Virtual Accounts
* [getHistory](docs/sdks/virtualaccounts/README.md#gethistory) - Virtual Account Activity Across All Customers

### [Webhooks](docs/sdks/webhooks/README.md)

* [get](docs/sdks/webhooks/README.md#get) - Get all webhook endpoints
* [create](docs/sdks/webhooks/README.md#create) - Create a webhook endpoint
* [update](docs/sdks/webhooks/README.md#update) - Update a webhook
* [delete](docs/sdks/webhooks/README.md#delete) - Delete a webhook
* [getEvents](docs/sdks/webhooks/README.md#getevents) - List upcoming events
* [getLogs](docs/sdks/webhooks/README.md#getlogs) - View logs
* [send](docs/sdks/webhooks/README.md#send) - Send event

</details>
<!-- End Available Resources and Operations [operations] -->

<!-- Start Error Handling [errors] -->
## Error Handling

Handling errors in this SDK should largely match your expectations. All operations return a response object or throw an exception.

By default an API error will raise a `Errors\APIException` exception, which has the following properties:

| Property       | Type                                    | Description           |
|----------------|-----------------------------------------|-----------------------|
| `$message`     | *string*                                | The error message     |
| `$statusCode`  | *int*                                   | The HTTP status code  |
| `$rawResponse` | *?\Psr\Http\Message\ResponseInterface*  | The raw HTTP response |
| `$body`        | *string*                                | The response content  |

When custom error responses are specified for an operation, the SDK may also throw their associated exception. You can refer to respective *Errors* tables in SDK docs for more details on possible exception types for each operation. For example, the `list` method throws the following exceptions:

| Error Type          | Status Code   | Content Type     |
| ------------------- | ------------- | ---------------- |
| Errors\Error        | 400, 401, 404 | application/json |
| Errors\Error        | 500           | application/json |
| Errors\APIException | 4XX, 5XX      | \*/\*            |

### Example

```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;
use ReThink\BridgeSDK\Models\Errors;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();

try {
    $response = $sdk->bridgeWallets->list(

    );

    if ($response->bridgeWalletsList !== null) {
        // handle response
    }
} catch (Errors\ErrorThrowable $e) {
    // handle $e->$container data
    throw $e;
} catch (Errors\ErrorThrowable $e) {
    // handle $e->$container data
    throw $e;
} catch (Errors\APIException $e) {
    // handle default exception
    throw $e;
}
```
<!-- End Error Handling [errors] -->

<!-- Start Server Selection [server] -->
## Server Selection

### Override Server URL Per-Client

The default server can be overridden globally using the `setServerUrl(string $serverUrl)` builder method when initializing the SDK client instance. For example:
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setServerURL('https://api.bridge.xyz/v0')
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
<!-- End Server Selection [server] -->

<!-- Placeholder for Future Speakeasy SDK Sections -->

# Development

## Maturity

This SDK is in beta, and there may be breaking changes between versions without a major version update. Therefore, we recommend pinning usage
to a specific package version. This way, you can install the same version each time without breaking changes unless you are intentionally
looking for the latest version.

## Contributions

While we value open-source contributions to this SDK, this library is generated programmatically. Any manual changes added to internal files will be overwritten on the next generation. 
We look forward to hearing your feedback. Feel free to open a PR or an issue with a proof of concept and we'll do our best to include it in a future release. 

### SDK Created by [Speakeasy](https://www.speakeasy.com/?utm_source=rethink/bridgesdk&utm_campaign=php)
