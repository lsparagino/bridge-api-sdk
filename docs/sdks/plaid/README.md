# Plaid

## Overview

### Available Operations

* [createLinkRequest](#createlinkrequest) - Generate a Plaid Link token for a customer
* [exchangePublicToken](#exchangepublictoken) - Exchange Plaid public token for an access token

## createLinkRequest

Generate a Plaid Link token for a customer

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/customers/{customerID}/plaid_link_requests" method="post" path="/customers/{customerID}/plaid_link_requests" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->plaid->createLinkRequest(
    idempotencyKey: '<value>',
    customerID: '<id>'

);

if ($response->plaidLinkRequest !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `idempotencyKey`   | *string*           | :heavy_check_mark: | N/A                |
| `customerID`       | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\PostCustomersCustomerIDPlaidLinkRequestsResponse](../../Models/Operations/PostCustomersCustomerIDPlaidLinkRequestsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## exchangePublicToken

Exchange Plaid public token for an access token

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/plaid_exchange_public_token/{link_token}" method="post" path="/plaid_exchange_public_token/{link_token}" -->
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

$body = new Components\PlaidExchangePublicToken(
    publicToken: '<value>',
);

$response = $sdk->plaid->exchangePublicToken(
    linkToken: '<value>',
    body: $body

);

if ($response->plaidPublicTokenExchanged !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                  | Type                                                                                       | Required                                                                                   | Description                                                                                |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| `linkToken`                                                                                | *string*                                                                                   | :heavy_check_mark:                                                                         | Plaid Link token                                                                           |
| `body`                                                                                     | [Components\PlaidExchangePublicToken](../../Models/Components/PlaidExchangePublicToken.md) | :heavy_check_mark:                                                                         | Plaid public token to be exchanged                                                         |

### Response

**[?Operations\PostPlaidExchangePublicTokenLinkTokenResponse](../../Models/Operations/PostPlaidExchangePublicTokenLinkTokenResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |