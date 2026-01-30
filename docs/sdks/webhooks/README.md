# Webhooks

## Overview

### Available Operations

* [get](#get) - Get all webhook endpoints
* [create](#create) - Create a webhook endpoint
* [update](#update) - Update a webhook
* [delete](#delete) - Delete a webhook
* [getEvents](#getevents) - List upcoming events
* [getLogs](#getlogs) - View logs
* [send](#send) - Send event

## get

Get the full list of active and disabled webhook endpoints configured on Bridge

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/webhooks" method="get" path="/webhooks" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->webhooks->get(

);

if ($response->webhooks !== null) {
    // handle response
}
```

### Response

**[?Operations\GetWebhooksResponse](../../Models/Operations/GetWebhooksResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## create

Create a new webhook endpoint to receive events from Bridge. Webhook endpoints begin in a disabled state and can be enabled with a PUT request. A maximum of 5 webhooks can be active or disabled at one time. Webhook endpoints can be created in Sandbox, but no webhook events will be sent.

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/webhooks" method="post" path="/webhooks" -->
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

$body = new Components\CreateWebhook(
    url: 'https://comfortable-scout.biz/',
    eventEpoch: Components\EventEpoch::BeginningOfTime,
);

$response = $sdk->webhooks->create(
    idempotencyKey: '<value>',
    body: $body

);

if ($response->webhook !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                            | Type                                                                 | Required                                                             | Description                                                          |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `idempotencyKey`                                                     | *string*                                                             | :heavy_check_mark:                                                   | N/A                                                                  |
| `body`                                                               | [Components\CreateWebhook](../../Models/Components/CreateWebhook.md) | :heavy_check_mark:                                                   | Information about the webhook endpoint to be created                 |

### Response

**[?Operations\PostWebhooksResponse](../../Models/Operations/PostWebhooksResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## update

Update the specified webhook object

### Example Usage

<!-- UsageSnippet language="php" operationID="put_/webhooks/{webhookID}" method="put" path="/webhooks/{webhookID}" -->
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

$body = new Components\PutWebhookPayload();

$response = $sdk->webhooks->update(
    webhookID: '<id>',
    body: $body

);

if ($response->webhook !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                    | Type                                                                         | Required                                                                     | Description                                                                  |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| `webhookID`                                                                  | *string*                                                                     | :heavy_check_mark:                                                           | N/A                                                                          |
| `body`                                                                       | [Components\PutWebhookPayload](../../Models/Components/PutWebhookPayload.md) | :heavy_check_mark:                                                           | Updated webhook endpoint object                                              |

### Response

**[?Operations\PutWebhooksWebhookIDResponse](../../Models/Operations/PutWebhooksWebhookIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401, 404            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## delete

Delete the specified webhook object. This webhook will no longer be accessible via API.

### Example Usage

<!-- UsageSnippet language="php" operationID="delete_/webhooks/{webhookID}" method="delete" path="/webhooks/{webhookID}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->webhooks->delete(
    webhookID: '<id>'
);

if ($response->webhook !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `webhookID`        | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\DeleteWebhooksWebhookIDResponse](../../Models/Operations/DeleteWebhooksWebhookIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401, 404            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getEvents

List the next 10 events that will be delivered to the specified webhook.

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/webhooks/{webhookID}/events" method="get" path="/webhooks/{webhookID}/events" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->webhooks->getEvents(
    webhookID: '<id>'
);

if ($response->webhookEvents !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `webhookID`        | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\GetWebhooksWebhookIDEventsResponse](../../Models/Operations/GetWebhooksWebhookIDEventsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getLogs

Display the most recent logs for deliveries to the specified webhook.

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/webhooks/{webhookID}/logs" method="get" path="/webhooks/{webhookID}/logs" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->webhooks->getLogs(
    webhookID: '<id>'
);

if ($response->deliveryLogs !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `webhookID`        | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\GetWebhooksWebhookIDLogsResponse](../../Models/Operations/GetWebhooksWebhookIDLogsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## send

Send an event to the specified webhook endpoint. This will not effect other events in the delivery queue. This operation is possible for both active and disabled webhook endpoints.

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/webhooks/{webhookID}/send" method="post" path="/webhooks/{webhookID}/send" -->
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

$body = new Components\SendWebhookPayload();

$response = $sdk->webhooks->send(
    webhookID: '<id>',
    idempotencyKey: '<value>',
    body: $body

);

if ($response->webhookEventSent !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                      | Type                                                                           | Required                                                                       | Description                                                                    |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| `webhookID`                                                                    | *string*                                                                       | :heavy_check_mark:                                                             | N/A                                                                            |
| `idempotencyKey`                                                               | *string*                                                                       | :heavy_check_mark:                                                             | N/A                                                                            |
| `body`                                                                         | [Components\SendWebhookPayload](../../Models/Components/SendWebhookPayload.md) | :heavy_check_mark:                                                             | Specify the event to send to your endpoint.                                    |

### Response

**[?Operations\PostWebhooksWebhookIDSendResponse](../../Models/Operations/PostWebhooksWebhookIDSendResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |