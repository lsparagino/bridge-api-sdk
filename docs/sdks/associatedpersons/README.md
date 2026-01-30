# AssociatedPersons

## Overview

### Available Operations

* [get](#get) - Get a single associated person (Beta)
* [delete](#delete) - Delete a single associated person
* [update](#update) - Update a single associated person

## get

Retrieve an associated person by ID

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/associated_persons/{associatedPersonID}" method="get" path="/associated_persons/{associatedPersonID}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->associatedPersons->get(
    associatedPersonID: '<id>'
);

if ($response->associatedPersonResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                  | Type                                       | Required                                   | Description                                |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| `associatedPersonID`                       | *string*                                   | :heavy_check_mark:                         | Unique identifier for an associated person |

### Response

**[?Operations\GetAssociatedPersonsAssociatedPersonIDResponse](../../Models/Operations/GetAssociatedPersonsAssociatedPersonIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401, 404            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## delete

Delete an associated person by ID

### Example Usage

<!-- UsageSnippet language="php" operationID="delete_/associated_persons/{associatedPersonID}" method="delete" path="/associated_persons/{associatedPersonID}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->associatedPersons->delete(
    associatedPersonID: '<id>'
);

if ($response->associatedPersonResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                  | Type                                       | Required                                   | Description                                |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| `associatedPersonID`                       | *string*                                   | :heavy_check_mark:                         | Unique identifier for an associated person |

### Response

**[?Operations\DeleteAssociatedPersonsAssociatedPersonIDResponse](../../Models/Operations/DeleteAssociatedPersonsAssociatedPersonIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401, 404            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## update

Update a single associated person

### Example Usage

<!-- UsageSnippet language="php" operationID="put_/associated_persons/{associatedPersonID}" method="put" path="/associated_persons/{associatedPersonID}" -->
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

$body = new Components\AssociatedPerson(
    firstName: 'Lauren',
    lastName: 'Gorczany',
    email: 'Herminio18@gmail.com',
    residentialAddress: new Components\Address2025WinterRefresh(
        streetLine1: '<value>',
        city: 'Angusfield',
        country: 'Luxembourg',
    ),
    birthDate: '1968-01-07',
    hasOwnership: false,
    hasControl: false,
    isSigner: true,
    identifyingInformation: [],
);

$response = $sdk->associatedPersons->update(
    associatedPersonID: '<id>',
    body: $body

);

if ($response->associatedPersonResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                  | Type                                                                       | Required                                                                   | Description                                                                |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| `associatedPersonID`                                                       | *string*                                                                   | :heavy_check_mark:                                                         | Unique identifier for an associated person                                 |
| `body`                                                                     | [Components\AssociatedPerson](../../Models/Components/AssociatedPerson.md) | :heavy_check_mark:                                                         | Associated person data to update                                           |

### Response

**[?Operations\PutAssociatedPersonsAssociatedPersonIDResponse](../../Models/Operations/PutAssociatedPersonsAssociatedPersonIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401, 404       | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |