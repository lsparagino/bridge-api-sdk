# CryptoReturnPolicies

## Overview

### Available Operations

* [getAll](#getall) - Get all crypto return policies
* [create](#create) - Create a new crypto return policy
* [delete](#delete) - Delete a single crypto return policy object
* [update](#update) - Update an existing crypto return policy

## getAll

Retrieve all crypto return policies for the authenticated developer

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/crypto_return_policies" method="get" path="/crypto_return_policies" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->cryptoReturnPolicies->getAll(

);

if ($response->cryptoReturnPolicies !== null) {
    // handle response
}
```

### Response

**[?Operations\GetCryptoReturnPoliciesResponse](../../Models/Operations/GetCryptoReturnPoliciesResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## create

Create a new crypto return policy

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/crypto_return_policies" method="post" path="/crypto_return_policies" -->
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

$body = new Components\PostCryptoReturnPoliciesInput();

$response = $sdk->cryptoReturnPolicies->create(
    idempotencyKey: '<value>',
    body: $body

);

if ($response->cryptoReturnPolicy !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                            | Type                                                                                                 | Required                                                                                             | Description                                                                                          |
| ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| `idempotencyKey`                                                                                     | *string*                                                                                             | :heavy_check_mark:                                                                                   | N/A                                                                                                  |
| `body`                                                                                               | [Components\PostCryptoReturnPoliciesInput](../../Models/Components/PostCryptoReturnPoliciesInput.md) | :heavy_check_mark:                                                                                   | Crypto return policy object to be created                                                            |

### Response

**[?Operations\PostCryptoReturnPoliciesResponse](../../Models/Operations/PostCryptoReturnPoliciesResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## delete

Delete a crypto return policy object from the passed in crypto return policy ID

### Example Usage

<!-- UsageSnippet language="php" operationID="delete_/crypto_return_policies/{policyID}" method="delete" path="/crypto_return_policies/{policyID}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->cryptoReturnPolicies->delete(
    policyID: '<id>'
);

if ($response->cryptoReturnPolicy !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `policyID`         | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\DeleteCryptoReturnPoliciesPolicyIDResponse](../../Models/Operations/DeleteCryptoReturnPoliciesPolicyIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401, 404            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## update

Update an existing crypto return policy

### Example Usage

<!-- UsageSnippet language="php" operationID="put_/crypto_return_policies/{policyID}" method="put" path="/crypto_return_policies/{policyID}" -->
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

$body = new Components\PostCryptoReturnPoliciesInput();

$response = $sdk->cryptoReturnPolicies->update(
    policyID: '<id>',
    body: $body

);

if ($response->cryptoReturnPolicy !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                            | Type                                                                                                 | Required                                                                                             | Description                                                                                          |
| ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| `policyID`                                                                                           | *string*                                                                                             | :heavy_check_mark:                                                                                   | N/A                                                                                                  |
| `body`                                                                                               | [Components\PostCryptoReturnPoliciesInput](../../Models/Components/PostCryptoReturnPoliciesInput.md) | :heavy_check_mark:                                                                                   | Crypto return policy object to be updated                                                            |

### Response

**[?Operations\PutCryptoReturnPoliciesPolicyIDResponse](../../Models/Operations/PutCryptoReturnPoliciesPolicyIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401, 404       | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |