# BridgeWalletBalance

The balance of a Bridge Wallet for a given currency


## Fields

| Field                                                                        | Type                                                                         | Required                                                                     | Description                                                                  |
| ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| `balance`                                                                    | *string*                                                                     | :heavy_check_mark:                                                           | The balance in the given currency. ex. "10.95"                               |
| `currency`                                                                   | [Components\Currency](../../Models/Components/Currency.md)                   | :heavy_check_mark:                                                           | N/A                                                                          |
| `chain`                                                                      | [Components\BridgeWalletChain](../../Models/Components/BridgeWalletChain.md) | :heavy_check_mark:                                                           | N/A                                                                          |
| `contractAddress`                                                            | *?string*                                                                    | :heavy_minus_sign:                                                           | The contract address of the currency, or null if it is a native currency     |