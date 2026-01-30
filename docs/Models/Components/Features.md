# Features

Features that should be enabled for this transfer. See [Transfer Features](https://apidocs.bridge.xyz/platform/orchestration/transfers/transfer-features) for more details.


## Fields

| Field                                                                                       | Type                                                                                        | Required                                                                                    | Description                                                                                 |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| `flexibleAmount`                                                                            | *?bool*                                                                                     | :heavy_minus_sign:                                                                          | Allows for variable amounts to be accepted. When true, omit `amount` from the request body. |
| `staticTemplate`                                                                            | *?bool*                                                                                     | :heavy_minus_sign:                                                                          | N/A                                                                                         |
| `allowAnyFromAddress`                                                                       | *?bool*                                                                                     | :heavy_minus_sign:                                                                          | N/A                                                                                         |