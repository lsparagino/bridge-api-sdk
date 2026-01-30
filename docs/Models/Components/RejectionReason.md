# RejectionReason

Reason why the kyc_status was rejected


## Fields

| Field                                                                                      | Type                                                                                       | Required                                                                                   | Description                                                                                |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| `developerReason`                                                                          | *?string*                                                                                  | :heavy_minus_sign:                                                                         | Developer information for why a customer was rejected. Not to be shared with the customer. |
| `reason`                                                                                   | *?string*                                                                                  | :heavy_minus_sign:                                                                         | Reason for why a customer was rejected. To be shared with the customer.                    |
| `createdAt`                                                                                | *?string*                                                                                  | :heavy_minus_sign:                                                                         | Time of creation of the rejection reason                                                   |