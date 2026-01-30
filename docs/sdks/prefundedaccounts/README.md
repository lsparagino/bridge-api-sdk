# PrefundedAccounts

## Overview

### Available Operations

* [list](#list) - Get a list of all Prefunded Account
* [get](#get) - Get details for a specific Prefunded Account
* [getHistory](#gethistory) - Get funding history of a Prefunded Account

## list

Retrieve a all Prefunded Accounts

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/prefunded_accounts" method="get" path="/prefunded_accounts" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->prefundedAccounts->list(

);

if ($response->prefundedAccounts !== null) {
    // handle response
}
```

### Response

**[?Operations\GetPrefundedAccountsResponse](../../Models/Operations/GetPrefundedAccountsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401, 404            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## get

Retrieve a Prefunded Account

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/prefunded_accounts/{prefundedAccountID}" method="get" path="/prefunded_accounts/{prefundedAccountID}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->prefundedAccounts->get(
    prefundedAccountID: '<id>'
);

if ($response->prefundedAccount !== null) {
    // handle response
}
```

### Parameters

| Parameter            | Type                 | Required             | Description          |
| -------------------- | -------------------- | -------------------- | -------------------- |
| `prefundedAccountID` | *string*             | :heavy_check_mark:   | N/A                  |

### Response

**[?Operations\GetPrefundedAccountsPrefundedAccountIDResponse](../../Models/Operations/GetPrefundedAccountsPrefundedAccountIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401, 404            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getHistory

Retrieve the funding events and returns for a Prefunded Account

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/prefunded_accounts/{prefundedAccountID}/history" method="get" path="/prefunded_accounts/{prefundedAccountID}/history" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->prefundedAccounts->getHistory(
    prefundedAccountID: '<id>'
);

if ($response->prefundedAccountHistory !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                                                                                                       | Type                                                                                                                                                                                                                                                                                                                                                                            | Required                                                                                                                                                                                                                                                                                                                                                                        | Description                                                                                                                                                                                                                                                                                                                                                                     |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `prefundedAccountID`                                                                                                                                                                                                                                                                                                                                                            | *string*                                                                                                                                                                                                                                                                                                                                                                        | :heavy_check_mark:                                                                                                                                                                                                                                                                                                                                                              | N/A                                                                                                                                                                                                                                                                                                                                                                             |
| `limit`                                                                                                                                                                                                                                                                                                                                                                         | *?int*                                                                                                                                                                                                                                                                                                                                                                          | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                              | The number of items to return (default of 10, max of 100)                                                                                                                                                                                                                                                                                                                       |
| `startingAfter`                                                                                                                                                                                                                                                                                                                                                                 | *?string*                                                                                                                                                                                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                              | This is a prefunded event id. If this is specified, the next page that starts with an event right AFTER the specified event id on the event timeline, which is always ordered from the newest to the oldest by creation time, will be returned. This also implies that events older than the specified event id will be returned (shouldn't be set if ending_before is set)     |
| `endingBefore`                                                                                                                                                                                                                                                                                                                                                                  | *?string*                                                                                                                                                                                                                                                                                                                                                                       | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                              | This is a prefunded event id. If this is specified, the previous page that ends with an event right BEFORE the specified event id on the event timeline, which is always ordered from the newest to the oldest by creation time, will be returned. This also implies that events newer than the specified event id will be returned (shouldn't be set if starting_after is set) |

### Response

**[?Operations\GetPrefundedAccountsPrefundedAccountIDHistoryResponse](../../Models/Operations/GetPrefundedAccountsPrefundedAccountIDHistoryResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401, 404            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |