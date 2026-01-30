# Lists

## Overview

### Available Operations

* [getOccupationCodes](#getoccupationcodes) - Get occupation codes
* [listCountries](#listcountries) - Get countries

## getOccupationCodes

Provide this list of occupation codes to your users as possible answers to the Source of Funds section in the KYC flow. The returned list will resemble the list of occupation codes found [here](https://apidocs.bridge.xyz/page/sof-eu-most-recent-occupation-list).


### Example Usage

<!-- UsageSnippet language="php" operationID="get_/lists/occupation_codes" method="get" path="/lists/occupation_codes" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->lists->getOccupationCodes(

);

if ($response->responseBodies !== null) {
    // handle response
}
```

### Response

**[?Operations\GetListsOccupationCodesResponse](../../Models/Operations/GetListsOccupationCodesResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## listCountries

Returns a list of countries and subdivisions recognized by Bridge. Inclusion in this list does not guarantee Bridge product support for any country or subdivision.

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/lists/countries" method="get" path="/lists/countries" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->lists->listCountries(

);

if ($response->countries !== null) {
    // handle response
}
```

### Response

**[?Operations\GetListsCountriesResponse](../../Models/Operations/GetListsCountriesResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |