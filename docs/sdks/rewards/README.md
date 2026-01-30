# Rewards

## Overview

### Available Operations

* [getRates](#getrates) - Get the current reward rates
* [summary](#summary) - Get a summary of all rewards for a given stablecoin
* [currencyRates](#currencyrates) - Get the currency reward rates for a given stablecoin
* [getSummary](#getsummary) - Get a summary of a customer's rewards
* [getCustomerHistory](#getcustomerhistory) - Get a history of a customer's rewards

## getRates

Get the current reward rates

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/rewards/rates" method="get" path="/rewards/rates" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->rewards->getRates(

);

if ($response->rewardRate !== null) {
    // handle response
}
```

### Parameters

| Parameter                           | Type                                | Required                            | Description                         |
| ----------------------------------- | ----------------------------------- | ----------------------------------- | ----------------------------------- |
| `since`                             | *?string*                           | :heavy_minus_sign:                  | The starting time in ISO8601 format |

### Response

**[?Operations\GetRewardsRatesResponse](../../Models/Operations/GetRewardsRatesResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## summary

Get a summary of all rewards for a given stablecoin

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/rewards/{currency}" method="get" path="/rewards/{currency}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->rewards->summary(
    currency: 'Jamaican Dollar'
);

if ($response->developerRewardSummary !== null) {
    // handle response
}
```

### Parameters

| Parameter             | Type                  | Required              | Description           |
| --------------------- | --------------------- | --------------------- | --------------------- |
| `currency`            | *string*              | :heavy_check_mark:    | The stablecoin symbol |

### Response

**[?Operations\GetRewardsCurrencyResponse](../../Models/Operations/GetRewardsCurrencyResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## currencyRates

Get the currency rewazrd rates for a given stablecoin

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/rewards/{currency}/rates" method="get" path="/rewards/{currency}/rates" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->rewards->currencyRates(
    currency: 'Dalasi'
);

if ($response->rewardRate !== null) {
    // handle response
}
```

### Parameters

| Parameter                           | Type                                | Required                            | Description                         |
| ----------------------------------- | ----------------------------------- | ----------------------------------- | ----------------------------------- |
| `currency`                          | *string*                            | :heavy_check_mark:                  | The stablecoin symbol               |
| `since`                             | *?string*                           | :heavy_minus_sign:                  | The starting time in ISO8601 format |

### Response

**[?Operations\GetRewardsCurrencyRatesResponse](../../Models/Operations/GetRewardsCurrencyRatesResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getSummary

Get a summary of a customer's rewards

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/rewards/{currency}/customer/{customerID}" method="get" path="/rewards/{currency}/customer/{customerID}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->rewards->getSummary(
    currency: 'Costa Rican Colon',
    customerID: '<id>'

);

if ($response->customerRewardSummary !== null) {
    // handle response
}
```

### Parameters

| Parameter             | Type                  | Required              | Description           |
| --------------------- | --------------------- | --------------------- | --------------------- |
| `currency`            | *string*              | :heavy_check_mark:    | The stablecoin symbol |
| `customerID`          | *string*              | :heavy_check_mark:    | N/A                   |

### Response

**[?Operations\GetRewardsCurrencyCustomerCustomerIDResponse](../../Models/Operations/GetRewardsCurrencyCustomerCustomerIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getCustomerHistory

Get a history of a customer's rewards

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/rewards/{currency}/customer/{customerID}/history" method="get" path="/rewards/{currency}/customer/{customerID}/history" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->rewards->getCustomerHistory(
    currency: 'Cape Verde Escudo',
    customerID: '<id>'

);

if ($response->customerRewardHistory !== null) {
    // handle response
}
```

### Parameters

| Parameter             | Type                  | Required              | Description           |
| --------------------- | --------------------- | --------------------- | --------------------- |
| `currency`            | *string*              | :heavy_check_mark:    | The stablecoin symbol |
| `customerID`          | *string*              | :heavy_check_mark:    | N/A                   |

### Response

**[?Operations\GetRewardsCurrencyCustomerCustomerIDHistoryResponse](../../Models/Operations/GetRewardsCurrencyCustomerCustomerIDHistoryResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |