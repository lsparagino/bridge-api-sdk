# AuthorizationControls

The authorization controls


## Fields

| Field                                                                               | Type                                                                                | Required                                                                            | Description                                                                         |
| ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `customerId`                                                                        | *string*                                                                            | :heavy_check_mark:                                                                  | The ID of the customer                                                              |
| `cardAccountId`                                                                     | *string*                                                                            | :heavy_check_mark:                                                                  | The ID of the card account                                                          |
| `spendingLimits`                                                                    | array<[Components\CardSpendingLimit](../../Models/Components/CardSpendingLimit.md)> | :heavy_check_mark:                                                                  | The various spending limits for the card account for the current time period        |