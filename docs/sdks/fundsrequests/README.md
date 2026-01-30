# FundsRequests

## Overview

### Available Operations

* [list](#list) - Get all funds requests

## list

Retrieve a list of all funds requests submitted by partnered banks and financial institutions

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/funds_requests" method="get" path="/funds_requests" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->fundsRequests->list(
    request: $request
);

if ($response->listOfFundsRequests !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                | Type                                                                                     | Required                                                                                 | Description                                                                              |
| ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| `$request`                                                                               | [Operations\GetFundsRequestsRequest](../../Models/Operations/GetFundsRequestsRequest.md) | :heavy_check_mark:                                                                       | The request object to use for the request.                                               |

### Response

**[?Operations\GetFundsRequestsResponse](../../Models/Operations/GetFundsRequestsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |