# CardLocalTransactionDetails

Details of a transaction processed in a local currency other than USD, with currency conversion applied


## Fields

| Field                                                                                       | Type                                                                                        | Required                                                                                    | Description                                                                                 |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `amount`                                                                                    | *string*                                                                                    | :heavy_check_mark:                                                                          | The amount in local currency, represented as a decimal string                               |
| `currency`                                                                                  | *string*                                                                                    | :heavy_check_mark:                                                                          | The transaction's local currency                                                            |
| `exchangeRate`                                                                              | *string*                                                                                    | :heavy_check_mark:                                                                          | The exchange rate applied to convert the local currency amount into USD for the transaction |