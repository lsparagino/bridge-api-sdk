# ExchangeRates

## Overview

### Available Operations

* [get](#get) - Get current exchange rate between two currencies.

## get

Returns the current exchange rate from the "from" currency to the "to" currency.
The exchange rate is updated roughly every 30s. Note that as of this writing,
Bridge does not offer a "quote" by which a user can lock in a rate for a given
amount of time. This is provided only as a courtesy to estimate what you are
likely to get in a subsequent transfer request that involves currency exchange.

As of October 2025, we support:
  - USD - EUR
  - USD - MXN
  - USD - BRL
  - BRL - USD
  - BTC - USD
  - ETH - USD
  - EUR - USD
  - MXN - USD
  - SOL - USD
  - USDT - USD


### Example Usage

<!-- UsageSnippet language="php" operationID="get_/exchange_rates" method="get" path="/exchange_rates" -->
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



$response = $sdk->exchangeRates->get(
    from: Operations\FromT::Usd,
    to: Operations\To::Eur

);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                            | Type                                                 | Required                                             | Description                                          | Example                                              |
| ---------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------- |
| `from`                                               | [Operations\FromT](../../Models/Operations/FromT.md) | :heavy_check_mark:                                   | The currency code to convert from.                   | usd                                                  |
| `to`                                                 | [Operations\To](../../Models/Operations/To.md)       | :heavy_check_mark:                                   | The currency code to convert to.                     | eur                                                  |

### Response

**[?Operations\GetExchangeRatesResponse](../../Models/Operations/GetExchangeRatesResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\APIException | 4XX, 5XX            | \*/\*               |