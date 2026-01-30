# GetTransfersStaticTemplatesStaticTemplates

List of static templates (the returned list is empty if none found). Static templates are transfers that are used as templates for other transfers and can be created using the static_templates feature flag.


## Fields

| Field                                                                             | Type                                                                              | Required                                                                          | Description                                                                       |
| --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| `count`                                                                           | *int*                                                                             | :heavy_check_mark:                                                                | The number of static templates returned                                           |
| `data`                                                                            | array<[Components\TransferResponse](../../Models/Components/TransferResponse.md)> | :heavy_check_mark:                                                                | N/A                                                                               |