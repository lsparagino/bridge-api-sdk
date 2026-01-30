# FiatPayoutConfiguration

A nested hash structure representing the fiat payout configuration. The top-level keys are currency codes. 
Each currency maps to a hash where keys are payment rail codes and values are payout names.



## Fields

| Field                                             | Type                                              | Required                                          | Description                                       |
| ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- |
| `usd`                                             | [?Components\Usd](../../Models/Components/Usd.md) | :heavy_minus_sign:                                | Payment rail configuration for USD                |
| `eur`                                             | [?Components\Eur](../../Models/Components/Eur.md) | :heavy_minus_sign:                                | Payment rail configuration for EUR                |
| `brl`                                             | [?Components\Brl](../../Models/Components/Brl.md) | :heavy_minus_sign:                                | Payment rail configuration for BRL                |
| `mxn`                                             | [?Components\Mxn](../../Models/Components/Mxn.md) | :heavy_minus_sign:                                | Payment rail configuration for MXN                |