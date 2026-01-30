# Cards

## Overview

### Available Operations

* [createPinUpdateUrl](#createpinupdateurl) - Create Card PIN Update URL
* [generateEphemeralKey](#generateephemeralkey) - Generate an Ephemeral Key to Reveal Card Details
* [getSummary](#getsummary) - Get a summary of your card program
* [getDesigns](#getdesigns) - Get a listing of your card program's card designs
* [get](#get) - Retrieve a card account
* [list](#list) - Get all card accounts
* [provisionAccount](#provisionaccount) - Provision a card account
* [freeze](#freeze) - Place a freeze on the card account
* [unfreeze](#unfreeze) - Unfreeze the card account
* [createMobileWalletProvisioningRequest](#createmobilewalletprovisioningrequest) - Create a mobile wallet push provisioning request
* [listAuthorizations](#listauthorizations) - Retrieve pending card authorizations
* [getTransactions](#gettransactions) - Retrieve card transactions
* [getTransaction](#gettransaction) - Retrieve a card transaction
* [getAuthControls](#getauthcontrols) - Retrieve authorization controls
* [provisionDepositAddress](#provisiondepositaddress) - Provision an additional top-up deposit address for the card account
* [createWithdrawal](#createwithdrawal) - Create a funds withdrawal request
* [listWithdrawals](#listwithdrawals) - Retrieve the withdrawal history of funds
* [getWithdrawal](#getwithdrawal) - Retrieve a card withdrawal
* [generateStatement](#generatestatement) - Generate a card account statement

## createPinUpdateUrl

Generates a URL that can be used to render a secure frame to update the PIN for a card account. The URL is single-use and time-limited.

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/customers/{customerID}/card_accounts/{cardAccountID}/pin" method="post" path="/customers/{customerID}/card_accounts/{cardAccountID}/pin" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->cards->createPinUpdateUrl(
    customerID: '<id>',
    idempotencyKey: '<value>',
    cardAccountID: 'f9809f16-3ed1-43e9-9ea5-bbfe3d9c0bd0'

);

if ($response->cardPinUpdateResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                  | Type                       | Required                   | Description                |
| -------------------------- | -------------------------- | -------------------------- | -------------------------- |
| `customerID`               | *string*                   | :heavy_check_mark:         | N/A                        |
| `idempotencyKey`           | *string*                   | :heavy_check_mark:         | N/A                        |
| `cardAccountID`            | *string*                   | :heavy_check_mark:         | The ID of the card account |

### Response

**[?Operations\PostCustomersCustomerIDCardAccountsCardAccountIDPinResponse](../../Models/Operations/PostCustomersCustomerIDCardAccountsCardAccountIDPinResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## generateEphemeralKey

Generates a one-time ephemeral key that can be used to reveal card details. Please see the integration guide on [safely revealing card details](https://apidocs.bridge.xyz/docs/safely-reveal-card-details-to-customers) for more information.

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/customers/{customerID}/card_accounts/{cardAccountID}/ephemeral_keys" method="post" path="/customers/{customerID}/card_accounts/{cardAccountID}/ephemeral_keys" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->cards->generateEphemeralKey(
    customerID: '<id>',
    idempotencyKey: '<value>',
    cardAccountID: '78a648bb-a3c1-45c8-b070-fe390db18ff8',
    body: $body

);

if ($response->cardAccountEphemeralKeyResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                   | Type                                                                                                        | Required                                                                                                    | Description                                                                                                 |
| ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| `customerID`                                                                                                | *string*                                                                                                    | :heavy_check_mark:                                                                                          | N/A                                                                                                         |
| `idempotencyKey`                                                                                            | *string*                                                                                                    | :heavy_check_mark:                                                                                          | N/A                                                                                                         |
| `cardAccountID`                                                                                             | *string*                                                                                                    | :heavy_check_mark:                                                                                          | The ID of the card account                                                                                  |
| `body`                                                                                                      | [?Components\PostCardAccountEphemeralKeyInput](../../Models/Components/PostCardAccountEphemeralKeyInput.md) | :heavy_minus_sign:                                                                                          | The client-side nonce that will be associated with the ephemeral key                                        |

### Response

**[?Operations\PostCustomersCustomerIDCardAccountsCardAccountIDEphemeralKeysResponse](../../Models/Operations/PostCustomersCustomerIDCardAccountsCardAccountIDEphemeralKeysResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getSummary

Get a summary of your card program, optionally for a specific period.

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/developer/cards/summary" method="get" path="/developer/cards/summary" -->
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



$response = $sdk->cards->getSummary(
    period: Components\CardProgramSummaryPeriodParameter::Day
);

if ($response->cardProgramSummary !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | Type                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Required                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `period`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | [Components\CardProgramSummaryPeriodParameter](../../Models/Components/CardProgramSummaryPeriodParameter.md)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | :heavy_check_mark:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | The type of period to summarize the card program by. If `lifetime` is specified, the `period_key` is not required.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `periodKey`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | *?string*                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | A string to indicate the period to retrieve the card program summary for.<br/>- For `year`, the period key should be in the `YYYY` format<br/>- For `month`, the period key should be in the `YYYYMM` format<br/>- For `week`, the period key should be in the `YYYYMMDD` format indicating the beginning day of the week.<br/>- For `day`, the period key should be in the `YYYYMMDD` format<br/>- For `lifetime`, the period key is not required<br/>Note that if a specific period is specified, this endpoint currently only supports fetching for periods with complete data (e.g. only up to the previous year, month, week, or day).<br/> |

### Response

**[?Operations\GetDeveloperCardsSummaryResponse](../../Models/Operations/GetDeveloperCardsSummaryResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getDesigns

Get a listing of the designs that you can use to issue a card with.

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/developer/cards/designs" method="get" path="/developer/cards/designs" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->cards->getDesigns(

);

if ($response->cardDesigns !== null) {
    // handle response
}
```

### Response

**[?Operations\GetDeveloperCardsDesignsResponse](../../Models/Operations/GetDeveloperCardsDesignsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## get

Retrieve the card account with the specified ID

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/card_accounts/{cardAccountID}" method="get" path="/customers/{customerID}/card_accounts/{cardAccountID}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->cards->get(
    customerID: '<id>',
    cardAccountID: '<id>'

);

if ($response->cardAccount !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `customerID`       | *string*           | :heavy_check_mark: | N/A                |
| `cardAccountID`    | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\GetCustomersCustomerIDCardAccountsCardAccountIDResponse](../../Models/Operations/GetCustomersCustomerIDCardAccountsCardAccountIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## list

Retrieve all card accounts for a customer. Currently, only one account is supported. An empty array will be returned if no card has been provisioned

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/card_accounts" method="get" path="/customers/{customerID}/card_accounts" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->cards->list(
    customerID: '<id>'
);

if ($response->arrayOfAllCardAccounts !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `customerID`       | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\GetCustomersCustomerIDCardAccountsResponse](../../Models/Operations/GetCustomersCustomerIDCardAccountsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## provisionAccount

Provision a card account. Currently, only one account can be provisioned per customer

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/customers/{customerID}/card_accounts" method="post" path="/customers/{customerID}/card_accounts" -->
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

$body = new Components\PostCardAccountsInput(
    currency: Components\CardsCryptoCurrency::Usdc,
    chain: Components\OfframpChainForCards::Polygon,
);

$response = $sdk->cards->provisionAccount(
    idempotencyKey: '<value>',
    customerID: '<id>',
    body: $body

);

if ($response->cardAccount !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                            | Type                                                                                 | Required                                                                             | Description                                                                          |
| ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| `idempotencyKey`                                                                     | *string*                                                                             | :heavy_check_mark:                                                                   | N/A                                                                                  |
| `customerID`                                                                         | *string*                                                                             | :heavy_check_mark:                                                                   | N/A                                                                                  |
| `body`                                                                               | [Components\PostCardAccountsInput](../../Models/Components/PostCardAccountsInput.md) | :heavy_check_mark:                                                                   | The card account to be provisioned                                                   |

### Response

**[?Operations\PostCustomersCustomerIDCardAccountsResponse](../../Models/Operations/PostCustomersCustomerIDCardAccountsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## freeze

Place a freeze on the card account

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/customers/{customerID}/card_accounts/{cardAccountID}/freeze" method="post" path="/customers/{customerID}/card_accounts/{cardAccountID}/freeze" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->cards->freeze(
    idempotencyKey: '<value>',
    customerID: '<id>',
    cardAccountID: '<id>',
    body: $body

);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                         | Type                                                                              | Required                                                                          | Description                                                                       |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| `idempotencyKey`                                                                  | *string*                                                                          | :heavy_check_mark:                                                                | N/A                                                                               |
| `customerID`                                                                      | *string*                                                                          | :heavy_check_mark:                                                                | N/A                                                                               |
| `cardAccountID`                                                                   | *string*                                                                          | :heavy_check_mark:                                                                | N/A                                                                               |
| `body`                                                                            | [?Components\PostCardFreezeInput](../../Models/Components/PostCardFreezeInput.md) | :heavy_minus_sign:                                                                | The freeze to be placed on the card account                                       |

### Response

**[?Operations\PostCustomersCustomerIDCardAccountsCardAccountIDFreezeResponse](../../Models/Operations/PostCustomersCustomerIDCardAccountsCardAccountIDFreezeResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## unfreeze

Remove the freeze on the card account placed by the specified initiator

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/customers/{customerID}/card_accounts/{cardAccountID}/unfreeze" method="post" path="/customers/{customerID}/card_accounts/{cardAccountID}/unfreeze" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->cards->unfreeze(
    idempotencyKey: '<value>',
    customerID: '<id>',
    cardAccountID: '<id>',
    body: $body

);

if ($response->cardUnfreezeResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                             | Type                                                                                  | Required                                                                              | Description                                                                           |
| ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| `idempotencyKey`                                                                      | *string*                                                                              | :heavy_check_mark:                                                                    | N/A                                                                                   |
| `customerID`                                                                          | *string*                                                                              | :heavy_check_mark:                                                                    | N/A                                                                                   |
| `cardAccountID`                                                                       | *string*                                                                              | :heavy_check_mark:                                                                    | N/A                                                                                   |
| `body`                                                                                | [?Components\PostCardUnfreezeInput](../../Models/Components/PostCardUnfreezeInput.md) | :heavy_minus_sign:                                                                    | A request to unfreeze the card account                                                |

### Response

**[?Operations\PostCustomersCustomerIDCardAccountsCardAccountIDUnfreezeResponse](../../Models/Operations/PostCustomersCustomerIDCardAccountsCardAccountIDUnfreezeResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## createMobileWalletProvisioningRequest

Create a request to push-provision a virtual card to a mobile wallet. This endpoint is part of a multiple-step integration that must be completed with each mobile wallet partner

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/customers/{customerID}/card_accounts/{cardAccountID}/create_mobile_wallet_provisioning_request" method="post" path="/customers/{customerID}/card_accounts/{cardAccountID}/create_mobile_wallet_provisioning_request" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->cards->createMobileWalletProvisioningRequest(
    idempotencyKey: '<value>',
    customerID: '<id>',
    cardAccountID: '<id>',
    body: $body

);

if ($response->cardPushProvisioningResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                             | Type                                                                                                  | Required                                                                                              | Description                                                                                           |
| ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| `idempotencyKey`                                                                                      | *string*                                                                                              | :heavy_check_mark:                                                                                    | N/A                                                                                                   |
| `customerID`                                                                                          | *string*                                                                                              | :heavy_check_mark:                                                                                    | N/A                                                                                                   |
| `cardAccountID`                                                                                       | *string*                                                                                              | :heavy_check_mark:                                                                                    | N/A                                                                                                   |
| `body`                                                                                                | [?Components\PostCardPushProvisioningInput](../../Models/Components/PostCardPushProvisioningInput.md) | :heavy_minus_sign:                                                                                    | A mobile wallet push provisioning request                                                             |

### Response

**[?Operations\PostCustomersCustomerIDCardAccountsCardAccountIDCreateMobileWalletProvisioningRequestResponse](../../Models/Operations/PostCustomersCustomerIDCardAccountsCardAccountIDCreateMobileWalletProvisioningRequestResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## listAuthorizations

Retrieve pending card authorizations.
Note: this endpoint is not paginated

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/card_accounts/{cardAccountID}/authorizations" method="get" path="/customers/{customerID}/card_accounts/{cardAccountID}/authorizations" -->
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

$request = new Operations\GetCustomersCustomerIDCardAccountsCardAccountIDAuthorizationsRequest(
    customerID: '<id>',
    cardAccountID: '<id>',
);

$response = $sdk->cards->listAuthorizations(
    request: $request
);

if ($response->listOfPendingCardAuthorizations !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                                                                          | Type                                                                                                                                                                               | Required                                                                                                                                                                           | Description                                                                                                                                                                        |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `$request`                                                                                                                                                                         | [Operations\GetCustomersCustomerIDCardAccountsCardAccountIDAuthorizationsRequest](../../Models/Operations/GetCustomersCustomerIDCardAccountsCardAccountIDAuthorizationsRequest.md) | :heavy_check_mark:                                                                                                                                                                 | The request object to use for the request.                                                                                                                                         |

### Response

**[?Operations\GetCustomersCustomerIDCardAccountsCardAccountIDAuthorizationsResponse](../../Models/Operations/GetCustomersCustomerIDCardAccountsCardAccountIDAuthorizationsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getTransactions

Retrieve completed card transactions and card-related crypto transaction activities

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/card_accounts/{cardAccountID}/transactions" method="get" path="/customers/{customerID}/card_accounts/{cardAccountID}/transactions" -->
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

$request = new Operations\GetCustomersCustomerIDCardAccountsCardAccountIDTransactionsRequest(
    customerID: '<id>',
    cardAccountID: '<id>',
);

$response = $sdk->cards->getTransactions(
    request: $request
);

if ($response->listOfCardTransactions !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                                                                      | Type                                                                                                                                                                           | Required                                                                                                                                                                       | Description                                                                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `$request`                                                                                                                                                                     | [Operations\GetCustomersCustomerIDCardAccountsCardAccountIDTransactionsRequest](../../Models/Operations/GetCustomersCustomerIDCardAccountsCardAccountIDTransactionsRequest.md) | :heavy_check_mark:                                                                                                                                                             | The request object to use for the request.                                                                                                                                     |

### Response

**[?Operations\GetCustomersCustomerIDCardAccountsCardAccountIDTransactionsResponse](../../Models/Operations/GetCustomersCustomerIDCardAccountsCardAccountIDTransactionsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getTransaction

Retrieve a card transaction with the specified ID

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/card_accounts/{cardAccountID}/transactions/{transactionID}" method="get" path="/customers/{customerID}/card_accounts/{cardAccountID}/transactions/{transactionID}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->cards->getTransaction(
    customerID: '<id>',
    cardAccountID: '<id>',
    transactionID: '<id>'

);

if ($response->cardTransaction !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `customerID`       | *string*           | :heavy_check_mark: | N/A                |
| `cardAccountID`    | *string*           | :heavy_check_mark: | N/A                |
| `transactionID`    | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\GetCustomersCustomerIDCardAccountsCardAccountIDTransactionsTransactionIDResponse](../../Models/Operations/GetCustomersCustomerIDCardAccountsCardAccountIDTransactionsTransactionIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getAuthControls

Retrieve the applicable spend limits for the given card account

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/card_accounts/{cardAccountID}/auth_controls" method="get" path="/customers/{customerID}/card_accounts/{cardAccountID}/auth_controls" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->cards->getAuthControls(
    customerID: '<id>',
    cardAccountID: '<id>'

);

if ($response->authorizationControls !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `customerID`       | *string*           | :heavy_check_mark: | N/A                |
| `cardAccountID`    | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\GetCustomersCustomerIDCardAccountsCardAccountIDAuthControlsResponse](../../Models/Operations/GetCustomersCustomerIDCardAccountsCardAccountIDAuthControlsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## provisionDepositAddress

Provision an additional deposit address for the card account, to allow topping up the card from multiple chains. This is only applicable to Bridge-custodied top-up card accounts. These additional deposit addresses will also be shown in the `additional_funding_instructions` field when fetching the card account details afterwards.

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/customers/{customerID}/card_accounts/{cardAccountID}/deposit_addresses" method="post" path="/customers/{customerID}/card_accounts/{cardAccountID}/deposit_addresses" -->
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

$body = new Components\PostCardAccountDepositAddressInput(
    chain: Components\OfframpChainForCards::Solana,
);

$response = $sdk->cards->provisionDepositAddress(
    idempotencyKey: '<value>',
    customerID: '<id>',
    cardAccountID: '<id>',
    body: $body

);

if ($response->cardAccountFundingInstructions !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                      | Type                                                                                                           | Required                                                                                                       | Description                                                                                                    |
| -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| `idempotencyKey`                                                                                               | *string*                                                                                                       | :heavy_check_mark:                                                                                             | N/A                                                                                                            |
| `customerID`                                                                                                   | *string*                                                                                                       | :heavy_check_mark:                                                                                             | N/A                                                                                                            |
| `cardAccountID`                                                                                                | *string*                                                                                                       | :heavy_check_mark:                                                                                             | N/A                                                                                                            |
| `body`                                                                                                         | [Components\PostCardAccountDepositAddressInput](../../Models/Components/PostCardAccountDepositAddressInput.md) | :heavy_check_mark:                                                                                             | The chain to provision the new deposit address on.                                                             |

### Response

**[?Operations\PostCustomersCustomerIDCardAccountsCardAccountIDDepositAddressesResponse](../../Models/Operations/PostCustomersCustomerIDCardAccountsCardAccountIDDepositAddressesResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## createWithdrawal

Request a funds withdrawal from the card account, applicable to top-up accounts only. For Bridge wallets, create a [transfer](/api-reference/transfers/create-a-transfer) from the Bridge wallet.

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/customers/{customerID}/card_accounts/{cardAccountID}/withdrawals" method="post" path="/customers/{customerID}/card_accounts/{cardAccountID}/withdrawals" -->
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

$body = new Components\CardWithdrawalInput(
    id: '<id>',
    amount: '728.78',
    currency: Components\CardsCryptoCurrency::Usdc,
    destination: new Components\CardWithdrawalDestinationInput(
        chain: '<value>',
        address: '18899 Vincenza Neck',
    ),
);

$response = $sdk->cards->createWithdrawal(
    idempotencyKey: '<value>',
    customerID: '<id>',
    cardAccountID: '<id>',
    body: $body

);

if ($response->cardWithdrawal !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                        | Type                                                                             | Required                                                                         | Description                                                                      |
| -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| `idempotencyKey`                                                                 | *string*                                                                         | :heavy_check_mark:                                                               | N/A                                                                              |
| `customerID`                                                                     | *string*                                                                         | :heavy_check_mark:                                                               | N/A                                                                              |
| `cardAccountID`                                                                  | *string*                                                                         | :heavy_check_mark:                                                               | N/A                                                                              |
| `body`                                                                           | [Components\CardWithdrawalInput](../../Models/Components/CardWithdrawalInput.md) | :heavy_check_mark:                                                               | The withdrawal request                                                           |

### Response

**[?Operations\PostCustomersCustomerIDCardAccountsCardAccountIDWithdrawalsResponse](../../Models/Operations/PostCustomersCustomerIDCardAccountsCardAccountIDWithdrawalsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## listWithdrawals

Retrieve the withdrawal history of funds, applicable to top-up accounts only

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/card_accounts/{cardAccountID}/withdrawals" method="get" path="/customers/{customerID}/card_accounts/{cardAccountID}/withdrawals" -->
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

$request = new Operations\GetCustomersCustomerIDCardAccountsCardAccountIDWithdrawalsRequest(
    customerID: '<id>',
    cardAccountID: '<id>',
);

$response = $sdk->cards->listWithdrawals(
    request: $request
);

if ($response->listOfWithdrawals !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                                                                    | Type                                                                                                                                                                         | Required                                                                                                                                                                     | Description                                                                                                                                                                  |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `$request`                                                                                                                                                                   | [Operations\GetCustomersCustomerIDCardAccountsCardAccountIDWithdrawalsRequest](../../Models/Operations/GetCustomersCustomerIDCardAccountsCardAccountIDWithdrawalsRequest.md) | :heavy_check_mark:                                                                                                                                                           | The request object to use for the request.                                                                                                                                   |

### Response

**[?Operations\GetCustomersCustomerIDCardAccountsCardAccountIDWithdrawalsResponse](../../Models/Operations/GetCustomersCustomerIDCardAccountsCardAccountIDWithdrawalsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getWithdrawal

Retrieve a card withdrawal with the specified ID, applicable to top-up accounts only

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/card_accounts/{cardAccountID}/withdrawals/{cardWithdrawalID}" method="get" path="/customers/{customerID}/card_accounts/{cardAccountID}/withdrawals/{cardWithdrawalID}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->cards->getWithdrawal(
    customerID: '<id>',
    cardAccountID: '<id>',
    cardWithdrawalID: '<id>'

);

if ($response->cardWithdrawal !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `customerID`       | *string*           | :heavy_check_mark: | N/A                |
| `cardAccountID`    | *string*           | :heavy_check_mark: | N/A                |
| `cardWithdrawalID` | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\GetCustomersCustomerIDCardAccountsCardAccountIDWithdrawalsCardWithdrawalIDResponse](../../Models/Operations/GetCustomersCustomerIDCardAccountsCardAccountIDWithdrawalsCardWithdrawalIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## generateStatement

Generate a card account statement for the specified period

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/customers/{customerID}/card_accounts/{cardAccountID}/statements/{period}.pdf" method="post" path="/customers/{customerID}/card_accounts/{cardAccountID}/statements/{period}.pdf" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->cards->generateStatement(
    customerID: '<id>',
    cardAccountID: '<id>',
    period: '<value>'

);

if ($response->bytes !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                            | Type                                                                 | Required                                                             | Description                                                          |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `customerID`                                                         | *string*                                                             | :heavy_check_mark:                                                   | N/A                                                                  |
| `cardAccountID`                                                      | *string*                                                             | :heavy_check_mark:                                                   | N/A                                                                  |
| `period`                                                             | *string*                                                             | :heavy_check_mark:                                                   | A string in the `YYYYMM` format representing a card statement period |

### Response

**[?Operations\PostCustomersCustomerIDCardAccountsCardAccountIDStatementsPeriodPdfResponse](../../Models/Operations/PostCustomersCustomerIDCardAccountsCardAccountIDStatementsPeriodPdfResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |