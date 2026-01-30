# PostCardPushProvisioningInputGooglePay

Google Pay specific push provisioning request data. Required for `google_pay` wallet provider.


## Fields

| Field                                          | Type                                           | Required                                       | Description                                    |
| ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- | ---------------------------------------------- |
| `clientWalletAccountId`                        | *string*                                       | :heavy_check_mark:                             | Value returned by Google Pay for use with Visa |
| `clientDeviceId`                               | *string*                                       | :heavy_check_mark:                             | Value returned by Google Pay for use with Visa |