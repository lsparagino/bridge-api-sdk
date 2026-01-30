# Address


## Fields

| Field                                                                | Type                                                                 | Required                                                             | Description                                                          |
| -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- | -------------------------------------------------------------------- |
| `streetLine1`                                                        | *string*                                                             | :heavy_check_mark:                                                   | N/A                                                                  |
| `streetLine2`                                                        | *?string*                                                            | :heavy_minus_sign:                                                   | N/A                                                                  |
| `city`                                                               | *string*                                                             | :heavy_check_mark:                                                   | N/A                                                                  |
| `state`                                                              | *?string*                                                            | :heavy_minus_sign:                                                   | ISO 3166-2 subdivision code. Must be supplied for US addresses.      |
| `postalCode`                                                         | *?string*                                                            | :heavy_minus_sign:                                                   | Must be supplied for countries that use postal codes.                |
| `country`                                                            | *string*                                                             | :heavy_check_mark:                                                   | Three-letter alpha-3 country code as defined in the ISO 3166-1 spec. |