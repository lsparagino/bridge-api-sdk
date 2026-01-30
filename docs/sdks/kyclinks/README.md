# KycLinks

## Overview

### Available Operations

* [generate](#generate) - Generate the Links needs to complete KYC for an individual or business
* [list](#list) - Get all KYC links.
* [getById](#getbyid) - Check the status of a KYC link

## generate

Generate the Links needs to complete KYC for an individual or business

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/kyc_links" method="post" path="/kyc_links" -->
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

$body = new Components\CreateKycLinks(
    email: 'Helen_Gleason29@yahoo.com',
    type: Components\CreateKycLinksType::Business,
);

$response = $sdk->kycLinks->generate(
    idempotencyKey: '<value>',
    body: $body

);

if ($response->individualKycLinkResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                              | Type                                                                   | Required                                                               | Description                                                            |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| `idempotencyKey`                                                       | *string*                                                               | :heavy_check_mark:                                                     | N/A                                                                    |
| `body`                                                                 | [Components\CreateKycLinks](../../Models/Components/CreateKycLinks.md) | :heavy_check_mark:                                                     | Information about the customer to create KYC Links for                 |

### Response

**[?Operations\PostKycLinksResponse](../../Models/Operations/PostKycLinksResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## list

Retrieve the full list of kyc links.

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/kyc_links" method="get" path="/kyc_links" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->kycLinks->list(
    request: $request
);

if ($response->kycLinks !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                      | Type                                                                           | Required                                                                       | Description                                                                    |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| `$request`                                                                     | [Operations\GetKycLinksRequest](../../Models/Operations/GetKycLinksRequest.md) | :heavy_check_mark:                                                             | The request object to use for the request.                                     |

### Response

**[?Operations\GetKycLinksResponse](../../Models/Operations/GetKycLinksResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401, 404            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getById

Retrieve the status of a KYC request from the passed in KYC link id

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/kyc_links/{kycLinkID}" method="get" path="/kyc_links/{kycLinkID}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->kycLinks->getById(
    kycLinkID: '<id>'
);

if ($response->individualKycLinkResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `kycLinkID`        | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\GetKycLinksKycLinkIDResponse](../../Models/Operations/GetKycLinksKycLinkIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401, 404            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |