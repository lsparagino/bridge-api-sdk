# CardDetails

Details of the issued card. This object contains enough payment card details to identify the issued card, but only provides the last four digits of the card number to maintain security.


## Fields

| Field                                                         | Type                                                          | Required                                                      | Description                                                   | Example                                                       |
| ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| `last4`                                                       | *string*                                                      | :heavy_check_mark:                                            | The last four digits of the card number                       | 1264                                                          |
| `expiry`                                                      | *string*                                                      | :heavy_check_mark:                                            | The expiration date of the card, in MM/YY format              | 10/24                                                         |
| `bin`                                                         | *string*                                                      | :heavy_check_mark:                                            | The BIN of the card, including the first 8 digits             | 44325280                                                      |
| `pinStatus`                                                   | [?Components\PinStatus](../../Models/Components/PinStatus.md) | :heavy_minus_sign:                                            | The current status of the card PIN                            |                                                               |