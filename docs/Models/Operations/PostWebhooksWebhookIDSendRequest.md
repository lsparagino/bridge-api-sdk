# PostWebhooksWebhookIDSendRequest


## Fields

| Field                                                                          | Type                                                                           | Required                                                                       | Description                                                                    |
| ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ | ------------------------------------------------------------------------------ |
| `webhookID`                                                                    | *string*                                                                       | :heavy_check_mark:                                                             | N/A                                                                            |
| `idempotencyKey`                                                               | *string*                                                                       | :heavy_check_mark:                                                             | N/A                                                                            |
| `body`                                                                         | [Components\SendWebhookPayload](../../Models/Components/SendWebhookPayload.md) | :heavy_check_mark:                                                             | Specify the event to send to your endpoint.                                    |