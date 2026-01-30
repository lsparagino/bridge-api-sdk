# WebhookEventDeliveryLog


## Fields

| Field                                                         | Type                                                          | Required                                                      | Description                                                   |
| ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------------- |
| `status`                                                      | *int*                                                         | :heavy_check_mark:                                            | The status code of the delivery                               |
| `eventId`                                                     | *string*                                                      | :heavy_check_mark:                                            | A UUID that uniquely identifies a resource                    |
| `responseBody`                                                | *string*                                                      | :heavy_check_mark:                                            | The response body of the delivery                             |
| `createdAt`                                                   | [\DateTime](https://www.php.net/manual/en/class.datetime.php) | :heavy_check_mark:                                            | The time of the delivery                                      |