# Customers

## Overview

### Available Operations

* [list](#list) - Get all customers
* [create](#create) - Create a customer
* [get](#get) - Get a single customer object
* [update](#update) - Update a single customer object
* [delete](#delete) - Delete a single customer object
* [getAssociatedPersons](#getassociatedpersons) - Get associated persons for a business customer (Beta)
* [addAssociatedPerson](#addassociatedperson) - Create a new associated person for a business customer (Beta)
* [getAssociatedPerson](#getassociatedperson) - Get a single associated person (Beta)
* [updateAssociatedPerson](#updateassociatedperson) - Update a single associated person
* [deleteAssociatedPerson](#deleteassociatedperson) - Delete a single associated person
* [getTosAcceptanceLink](#gettosacceptancelink) - Retrieve a hosted URL for ToS acceptance for an existing customer
* [getKycLink](#getkyclink) - Retrieve a hosted KYC Link for an existing customer
* [getTransfers](#gettransfers) - Get all transfers
* [getStaticTemplates](#getstatictemplates) - Get all static templates for a customer
* [createTosLink](#createtoslink) - Request a hosted URL for ToS acceptance for new customer creation

## list

Get the full list of all customers created on Bridge

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers" method="get" path="/customers" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->customers->list(

);

if ($response->customers !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                                                                                                              | Type                                                                                                                                                                                                                                                                                                                                                                                   | Required                                                                                                                                                                                                                                                                                                                                                                               | Description                                                                                                                                                                                                                                                                                                                                                                            |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `startingAfter`                                                                                                                                                                                                                                                                                                                                                                        | *?string*                                                                                                                                                                                                                                                                                                                                                                              | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                     | This is a customer id. If this is specified, the next page that starts with a customer right AFTER the specified customer id on the customer timeline, which is always ordered from the newest to the oldest by creation time, will be returned. This also implies that customers older than the specified customer id will be returned (shouldn't be set if ending_before is set)     |
| `endingBefore`                                                                                                                                                                                                                                                                                                                                                                         | *?string*                                                                                                                                                                                                                                                                                                                                                                              | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                     | This is a customer id. If this is specified, the previous page that ends with a customer right BEFORE the specified customer id on the customer timeline, which is always ordered from the newest to the oldest by creation time, will be returned. This also implies that customers newer than the specified customer id will be returned (shouldn't be set if starting_after is set) |
| `limit`                                                                                                                                                                                                                                                                                                                                                                                | *?int*                                                                                                                                                                                                                                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                     | The number of items to return (default of 10, max of 100)                                                                                                                                                                                                                                                                                                                              |
| `email`                                                                                                                                                                                                                                                                                                                                                                                | *?string*                                                                                                                                                                                                                                                                                                                                                                              | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                     | If included, filters to customers with the given email                                                                                                                                                                                                                                                                                                                                 |

### Response

**[?Operations\GetCustomersResponse](../../Models/Operations/GetCustomersResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## create

Create a customer

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/customers" method="post" path="/customers" -->
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



$response = $sdk->customers->create(
    idempotencyKey: '<value>',
    body: new Components\CreateIndividualCustomerPayload(
        type: Components\CreateIndividualCustomerPayloadType::Individual,
    )

);

if ($response->customer !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                                                                                                                                | Type                                                                                                                                                                                                                                                                                                                                                                                                     | Required                                                                                                                                                                                                                                                                                                                                                                                                 | Description                                                                                                                                                                                                                                                                                                                                                                                              |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `idempotencyKey`                                                                                                                                                                                                                                                                                                                                                                                         | *string*                                                                                                                                                                                                                                                                                                                                                                                                 | :heavy_check_mark:                                                                                                                                                                                                                                                                                                                                                                                       | N/A                                                                                                                                                                                                                                                                                                                                                                                                      |
| `body`                                                                                                                                                                                                                                                                                                                                                                                                   | [Components\CreateIndividualCustomerPayload\|Components\CreateBusinessCustomerPayload](../../Models/Operations/PostCustomersRequestBody.md)                                                                                                                                                                                                                                                              | :heavy_check_mark:                                                                                                                                                                                                                                                                                                                                                                                       | Customer object to be created.<br/><br/>For individual customers (soon to be businesses as well), no fields are strictly required by the API. For example, it is valid to create a customer without a first name, last name, or residential address, but this customer will not be granted endorsements required to transact on Bridge until the necessary information is provided, possibly via a PUT request.<br/> |

### Response

**[?Operations\PostCustomersResponse](../../Models/Operations/PostCustomersResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## get

Retrieve a customer object from the passed in customer ID

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}" method="get" path="/customers/{customerID}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->customers->get(
    customerID: '<id>'
);

if ($response->customer !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `customerID`       | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\GetCustomersCustomerIDResponse](../../Models/Operations/GetCustomersCustomerIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401, 404            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## update

Updates to be made to the specified customer.

For individual customers (soon to be businesses as well), no fields are strictly required by the API. It is generally valid to provide any subset of data in a PUT request. For business customers, associated persons cannot be updated via PUT, and should instead be managed using v0/associated_persons.


### Example Usage

<!-- UsageSnippet language="php" operationID="put_/customers/{customerID}" method="put" path="/customers/{customerID}" -->
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



$response = $sdk->customers->update(
    customerID: '<id>',
    body: new Components\UpdateBusinessCustomerPayload(
        type: Components\UpdateBusinessCustomerPayloadType::Business,
        businessLegalName: '<value>',
        businessTradeName: '<value>',
        businessDescription: '<value>',
        email: 'Madie71@hotmail.com',
        businessType: Components\UpdateBusinessCustomerPayloadBusinessType::Other,
        registeredAddress: new Components\Address2025WinterRefresh(
            streetLine1: '<value>',
            city: 'Dayton',
            country: 'Angola',
        ),
        physicalAddress: new Components\Address2025WinterRefresh(
            streetLine1: '<value>',
            city: 'Lafayette',
            country: 'Brazil',
        ),
        signedAgreementId: '<id>',
        isDao: true,
        associatedPersons: [
            new Components\AssociatedPerson(
                firstName: 'Hayden',
                lastName: 'Torp',
                email: 'Granville.Swaniawski@gmail.com',
                residentialAddress: new Components\Address2025WinterRefresh(
                    streetLine1: '<value>',
                    city: 'Mountain View',
                    country: 'Kiribati',
                ),
                birthDate: '1991-10-05',
                hasOwnership: false,
                hasControl: false,
                isSigner: true,
                identifyingInformation: [],
            ),
        ],
        businessIndustry: [
            '<value 1>',
        ],
        hasMaterialIntermediaryOwnership: true,
        accountPurpose: Components\UpdateBusinessCustomerPayloadAccountPurpose::ReceivePaymentsForGoodsAndServices,
        sourceOfFunds: Components\UpdateBusinessCustomerPayloadSourceOfFunds::Grants,
        identifyingInformation: [],
        documents: [
            new Components\BusinessDocuments(
                purposes: [
                    Components\BusinessDocumentsPurpose::BusinessFormation,
                ],
                file: '<value>',
            ),
        ],
    )

);

if ($response->customer !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                                                                                           | Type                                                                                                                                                                                                | Required                                                                                                                                                                                            | Description                                                                                                                                                                                         |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `customerID`                                                                                                                                                                                        | *string*                                                                                                                                                                                            | :heavy_check_mark:                                                                                                                                                                                  | N/A                                                                                                                                                                                                 |
| `body`                                                                                                                                                                                              | [Components\UpdateIndividualCustomerPayload\|Components\UpdateBusinessCustomerPayload\|Components\UpdateBusinessCustomerPayloadPartial](../../Models/Operations/PutCustomersCustomerIDRequestBody.md) | :heavy_check_mark:                                                                                                                                                                                  | Customer object to update with                                                                                                                                                                      |

### Response

**[?Operations\PutCustomersCustomerIDResponse](../../Models/Operations/PutCustomersCustomerIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401, 404            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## delete

Delete a customer object from the passed in customer ID

### Example Usage

<!-- UsageSnippet language="php" operationID="delete_/customers/{customerID}" method="delete" path="/customers/{customerID}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->customers->delete(
    customerID: '<id>'
);

if ($response->customer !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `customerID`       | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\DeleteCustomersCustomerIDResponse](../../Models/Operations/DeleteCustomersCustomerIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401, 404            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getAssociatedPersons

Get all associated persons for a business customer.

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/associated_persons" method="get" path="/customers/{customerID}/associated_persons" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->customers->getAssociatedPersons(
    customerID: '<id>'
);

if ($response->associatedPersonsList !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `customerID`       | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\GetCustomersCustomerIDAssociatedPersonsResponse](../../Models/Operations/GetCustomersCustomerIDAssociatedPersonsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401, 404            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## addAssociatedPerson

Create a new associated person for a business customer (Beta)

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/customers/{customerID}/associated_persons" method="post" path="/customers/{customerID}/associated_persons" -->
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
    firstName: 'Colin',
    lastName: 'Hansen',
    email: 'Darrion_Farrell@gmail.com',
    residentialAddress: new Components\Address2025WinterRefresh(
        streetLine1: '<value>',
        city: 'Tellystad',
        country: 'Argentina',
    ),
    birthDate: '2006-12-14',
    hasOwnership: false,
    hasControl: true,
    isSigner: false,
    identifyingInformation: [
        new Components\IdentifyingInformation(
            type: Components\IdentifyingInformationType::Itin,
            issuingCountry: '<value>',
        ),
    ],
);

$response = $sdk->customers->addAssociatedPerson(
    customerID: '<id>',
    idempotencyKey: '<value>',
    body: $body

);

if ($response->associatedPersonResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                  | Type                                                                       | Required                                                                   | Description                                                                |
| -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| `customerID`                                                               | *string*                                                                   | :heavy_check_mark:                                                         | N/A                                                                        |
| `idempotencyKey`                                                           | *string*                                                                   | :heavy_check_mark:                                                         | N/A                                                                        |
| `body`                                                                     | [Components\AssociatedPerson](../../Models/Components/AssociatedPerson.md) | :heavy_check_mark:                                                         | New associated person to be created                                        |

### Response

**[?Operations\PostCustomersCustomerIDAssociatedPersonsResponse](../../Models/Operations/PostCustomersCustomerIDAssociatedPersonsResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401, 404       | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getAssociatedPerson

Retrieve an associated person by ID

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/associated_persons/{associatedPersonID}" method="get" path="/customers/{customerID}/associated_persons/{associatedPersonID}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->customers->getAssociatedPerson(
    customerID: '<id>',
    associatedPersonID: '<id>'

);

if ($response->associatedPersonResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                  | Type                                       | Required                                   | Description                                |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| `customerID`                               | *string*                                   | :heavy_check_mark:                         | N/A                                        |
| `associatedPersonID`                       | *string*                                   | :heavy_check_mark:                         | Unique identifier for an associated person |

### Response

**[?Operations\GetCustomersCustomerIDAssociatedPersonsAssociatedPersonIDResponse](../../Models/Operations/GetCustomersCustomerIDAssociatedPersonsAssociatedPersonIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401, 404            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## updateAssociatedPerson

Update a single associated person

### Example Usage

<!-- UsageSnippet language="php" operationID="put_/customers/{customerID}/associated_persons/{associatedPersonID}" method="put" path="/customers/{customerID}/associated_persons/{associatedPersonID}" -->
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
    firstName: 'Meggie',
    lastName: 'Zulauf-Adams',
    email: 'Tre39@gmail.com',
    residentialAddress: new Components\Address2025WinterRefresh(
        streetLine1: '<value>',
        city: 'South Monica',
        country: 'India',
    ),
    birthDate: '1945-08-18',
    hasOwnership: true,
    hasControl: false,
    isSigner: false,
    identifyingInformation: [
        new Components\IdentifyingInformation(
            type: Components\IdentifyingInformationType::Cnp,
            issuingCountry: '<value>',
        ),
    ],
);

$response = $sdk->customers->updateAssociatedPerson(
    customerID: '<id>',
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
| `customerID`                                                               | *string*                                                                   | :heavy_check_mark:                                                         | N/A                                                                        |
| `associatedPersonID`                                                       | *string*                                                                   | :heavy_check_mark:                                                         | Unique identifier for an associated person                                 |
| `body`                                                                     | [Components\AssociatedPerson](../../Models/Components/AssociatedPerson.md) | :heavy_check_mark:                                                         | Associated person data to update                                           |

### Response

**[?Operations\PutCustomersCustomerIDAssociatedPersonsAssociatedPersonIDResponse](../../Models/Operations/PutCustomersCustomerIDAssociatedPersonsAssociatedPersonIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 400, 401, 404       | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## deleteAssociatedPerson

Delete an associated person by ID

### Example Usage

<!-- UsageSnippet language="php" operationID="delete_/customers/{customerID}/associated_persons/{associatedPersonID}" method="delete" path="/customers/{customerID}/associated_persons/{associatedPersonID}" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->customers->deleteAssociatedPerson(
    customerID: '<id>',
    associatedPersonID: '<id>'

);

if ($response->associatedPersonResponse !== null) {
    // handle response
}
```

### Parameters

| Parameter                                  | Type                                       | Required                                   | Description                                |
| ------------------------------------------ | ------------------------------------------ | ------------------------------------------ | ------------------------------------------ |
| `customerID`                               | *string*                                   | :heavy_check_mark:                         | N/A                                        |
| `associatedPersonID`                       | *string*                                   | :heavy_check_mark:                         | Unique identifier for an associated person |

### Response

**[?Operations\DeleteCustomersCustomerIDAssociatedPersonsAssociatedPersonIDResponse](../../Models/Operations/DeleteCustomersCustomerIDAssociatedPersonsAssociatedPersonIDResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401, 404            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getTosAcceptanceLink

The page at the returned URL will guide the user through the Bridge Terms of Service (ToS) acceptance flow. This can be used by existing customers to accept a new version of the ToS.

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/tos_acceptance_link" method="get" path="/customers/{customerID}/tos_acceptance_link" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->customers->getTosAcceptanceLink(
    customerID: '<id>'
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `customerID`       | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\GetCustomersCustomerIDTosAcceptanceLinkResponse](../../Models/Operations/GetCustomersCustomerIDTosAcceptanceLinkResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getKycLink

The page at the returned URL will guide the user through a Bridge KYC flow. This can be used by existing customers to provide additional KYC information required for certain features or services that Bridge offers.

For example, to enable an existing customer to use the `SEPA`/`Euro` services, they are required to provide `proof of address`. An additional parameter, `endorsement=sepa`, can be included to request a KYC link specifically for this purpose

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/kyc_link" method="get" path="/customers/{customerID}/kyc_link" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->customers->getKycLink(
    customerID: '<id>',
    redirectUri: 'http%3A%2F%2Fexample.com%2Fredirect'

);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                       | Type                                                                                                            | Required                                                                                                        | Description                                                                                                     | Example                                                                                                         |
| --------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| `customerID`                                                                                                    | *string*                                                                                                        | :heavy_check_mark:                                                                                              | N/A                                                                                                             |                                                                                                                 |
| `endorsement`                                                                                                   | [?Components\EndorsementParameter](../../Models/Components/EndorsementParameter.md)                             | :heavy_minus_sign:                                                                                              | An endorsement is the approval required for a customer to use a particular product or service offered by Bridge |                                                                                                                 |
| `redirectUri`                                                                                                   | *?string*                                                                                                       | :heavy_minus_sign:                                                                                              | An optional url encoded link that users will be redirected to after completing the hosted KYC flow.             | http%3A%2F%2Fexample.com%2Fredirect                                                                             |

### Response

**[?Operations\GetCustomersCustomerIDKycLinkResponse](../../Models/Operations/GetCustomersCustomerIDKycLinkResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getTransfers

Get all active and completed transfers for a customer.

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/transfers" method="get" path="/customers/{customerID}/transfers" -->
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

$request = new Operations\GetCustomersCustomerIDTransfersRequest(
    customerID: '<id>',
);

$response = $sdk->customers->getTransfers(
    request: $request
);

if ($response->transfers !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                              | Type                                                                                                                   | Required                                                                                                               | Description                                                                                                            |
| ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `$request`                                                                                                             | [Operations\GetCustomersCustomerIDTransfersRequest](../../Models/Operations/GetCustomersCustomerIDTransfersRequest.md) | :heavy_check_mark:                                                                                                     | The request object to use for the request.                                                                             |

### Response

**[?Operations\GetCustomersCustomerIDTransfersResponse](../../Models/Operations/GetCustomersCustomerIDTransfersResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## getStaticTemplates

Get all static templates for a customer. Static templates are transfers that are used as templates for other transfers and can be created using the static_templates feature flag.

### Example Usage

<!-- UsageSnippet language="php" operationID="get_/customers/{customerID}/static_templates" method="get" path="/customers/{customerID}/static_templates" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->customers->getStaticTemplates(
    customerID: '<id>'
);

if ($response->staticTemplates !== null) {
    // handle response
}
```

### Parameters

| Parameter                                                                                                                                                                                                                                                                                                                                                                              | Type                                                                                                                                                                                                                                                                                                                                                                                   | Required                                                                                                                                                                                                                                                                                                                                                                               | Description                                                                                                                                                                                                                                                                                                                                                                            |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `customerID`                                                                                                                                                                                                                                                                                                                                                                           | *string*                                                                                                                                                                                                                                                                                                                                                                               | :heavy_check_mark:                                                                                                                                                                                                                                                                                                                                                                     | N/A                                                                                                                                                                                                                                                                                                                                                                                    |
| `limit`                                                                                                                                                                                                                                                                                                                                                                                | *?int*                                                                                                                                                                                                                                                                                                                                                                                 | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                     | The number of items to return (default of 10, max of 100)                                                                                                                                                                                                                                                                                                                              |
| `startingAfter`                                                                                                                                                                                                                                                                                                                                                                        | *?string*                                                                                                                                                                                                                                                                                                                                                                              | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                     | This is a transfer id. If this is specified, the next page that starts with a transfer right AFTER the specified transfer id on the transfer timeline, which is always ordered from the newest to the oldest by creation time, will be returned. This also implies that transfers older than the specified transfer id will be returned (shouldn't be set if ending_before is set)     |
| `endingBefore`                                                                                                                                                                                                                                                                                                                                                                         | *?string*                                                                                                                                                                                                                                                                                                                                                                              | :heavy_minus_sign:                                                                                                                                                                                                                                                                                                                                                                     | This is a transfer id. If this is specified, the previous page that ends with a transfer right BEFORE the specified transfer id on the transfer timeline, which is always ordered from the newest to the oldest by creation time, will be returned. This also implies that transfers newer than the specified transfer id will be returned (shouldn't be set if starting_after is set) |

### Response

**[?Operations\GetCustomersCustomerIDStaticTemplatesResponse](../../Models/Operations/GetCustomersCustomerIDStaticTemplatesResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401, 404            | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |

## createTosLink

The URL endpoint returned will guide the user through a Bridge TOS flow. Signing this acceptance flow is a requirement for creating customers.

### Example Usage

<!-- UsageSnippet language="php" operationID="post_/customers/tos_links" method="post" path="/customers/tos_links" -->
```php
declare(strict_types=1);

require 'vendor/autoload.php';

use ReThink\BridgeSDK;

$sdk = BridgeSDK\BridgeSDK::builder()
    ->setSecurity(
        '<YOUR_API_KEY_HERE>'
    )
    ->build();



$response = $sdk->customers->createTosLink(
    idempotencyKey: '<value>'
);

if ($response->object !== null) {
    // handle response
}
```

### Parameters

| Parameter          | Type               | Required           | Description        |
| ------------------ | ------------------ | ------------------ | ------------------ |
| `idempotencyKey`   | *string*           | :heavy_check_mark: | N/A                |

### Response

**[?Operations\PostCustomersTosLinksResponse](../../Models/Operations/PostCustomersTosLinksResponse.md)**

### Errors

| Error Type          | Status Code         | Content Type        |
| ------------------- | ------------------- | ------------------- |
| Errors\Error        | 401                 | application/json    |
| Errors\Error        | 500                 | application/json    |
| Errors\APIException | 4XX, 5XX            | \*/\*               |