# PostCustomersRequestBody

Customer object to be created.

For individual customers (soon to be businesses as well), no fields are strictly required by the API. For example, it is valid to create a customer without a first name, last name, or residential address, but this customer will not be granted endorsements required to transact on Bridge until the necessary information is provided, possibly via a PUT request.



## Supported Types

### `Components\CreateIndividualCustomerPayload`

```php
/**
* @var Components\CreateIndividualCustomerPayload
*/
Components\CreateIndividualCustomerPayload $value = /* values here */
```

### `Components\CreateBusinessCustomerPayload`

```php
/**
* @var Components\CreateBusinessCustomerPayload
*/
Components\CreateBusinessCustomerPayload $value = /* values here */
```

