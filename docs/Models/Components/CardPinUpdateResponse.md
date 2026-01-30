# CardPinUpdateResponse

Response containing a secure URL to update a card's PIN


## Fields

| Field                                                                                      | Type                                                                                       | Required                                                                                   | Description                                                                                | Example                                                                                    |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| `url`                                                                                      | *string*                                                                                   | :heavy_check_mark:                                                                         | Single-use, time-limited URL that can be used to securely update the card PIN in an iframe | https://secure.example.com/update-pin?token=xyz789                                         |