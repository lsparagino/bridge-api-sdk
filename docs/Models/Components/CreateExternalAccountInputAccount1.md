# CreateExternalAccountInputAccount1

US or UK bank account information. Required when the `account_type` is `us` or `gb`. However, for `us`, the top-level `account_number` and `routing_number` fields in deprecation will continue to be supported.


## Supported Types

### `Components\UsBankAccountInput`

```php
/**
* @var Components\UsBankAccountInput
*/
Components\UsBankAccountInput $value = /* values here */
```

### `Components\GbBankAccount`

```php
/**
* @var Components\GbBankAccount
*/
Components\GbBankAccount $value = /* values here */
```

