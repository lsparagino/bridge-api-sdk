# CardCryptoAccount

The crypto account for a self-custodial card account. This field is not supported for a Bridge-custodial card funding setup (note that if you are on cards trial, you are automatically on a custodial funding setup).


## Fields

| Field                                                                                | Type                                                                                 | Required                                                                             | Description                                                                          |
| ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| `type`                                                                               | [Components\CardCryptoAccountType](../../Models/Components/CardCryptoAccountType.md) | :heavy_check_mark:                                                                   | The type of the crypto account                                                       |
| `address`                                                                            | *string*                                                                             | :heavy_check_mark:                                                                   | The public address of the crypto account                                             |