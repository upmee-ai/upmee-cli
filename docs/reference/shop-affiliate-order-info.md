# Get Affiliate Order Details

### Request URL

`https://www.upmee.cc/open_api/shop/affiliate/order/info`

### HTTP Method

`POST`

### Request Headers

<!-- api-fields -->

| Field | Required <!-- api-tag --> | Type | Description |
| --- | --- | --- | --- |
| API-Key | Required | string | API key |
| Content-Type | Required | string | Request content type. Allowed format: `application/json` |

### Request Parameters

<!-- api-fields -->

| Field | Required <!-- api-tag --> | Type | Description |
| --- | --- | --- | --- |
| team_id | Required | string | Team ID |
| media_id | Required | string | Creator account media\_id |
| platform_order_ids | Required | string[] | List of platform order IDs. After blank and duplicate values are removed, at least one ID must remain. Up to 50 per request. |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "media_id": "xxxxxx",
    "platform_order_ids": [
        "xxxxxx",
        "xxxxxx"
    ]
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| code | number | Application status code. `0` indicates success. |
| message | string | Message |
| request_id | string | Request ID |
| data | object | Response data |
| data.list | object[] | List of order details. Returns **matching orders** in the requested order ID sequence. IDs with no matching order are omitted. |
| data.list.media_id | string | Creator account ID |
| data.list.platform_order_id | string | Platform order number |
| data.list.create_time | number | Order placement timestamp in milliseconds |
| data.list.delivery_time | number | Shipment timestamp in milliseconds. Omitted if unavailable. |
| data.list.status | string | Original platform status |
| data.list.status_label | string | Normalized status. Allowed values: `PENDING_CONFIRM` Pending confirmation；`AWAITING_PAYMENT` Awaiting buyer payment；`TO_SETTLE` Pending settlement；`SETTLED` Settled；`REFUNDED` Refunded or canceled；`FROZEN` Commission frozen |
| data.list.currency | string | Currency |
| data.list.estimated_commission | number | Estimated commission total |
| data.list.actual_commission | number | Actual commission total |
| data.list.skus | object[] | List of SKU details |
| data.list.skus.platform_sku_id | string | Platform SKU ID |
| data.list.skus.product_id | string | Product ID |
| data.list.skus.product_name | string | Product name |
| data.list.skus.shop_name | string | Shop name |
| data.list.skus.cover | string | Product cover image URL |
| data.list.skus.quantity | number | Quantity purchased |
| data.list.skus.returned_quantity | number | Quantity returned |
| data.list.skus.refunded_quantity | number | Quantity refunded |
| data.list.skus.price | object | Unit price |
| data.list.skus.price.amount_raw | string | Original amount as a string |
| data.list.skus.price.amount_value | number | Numeric amount |
| data.list.skus.price.currency | string | Currency |
| data.list.skus.commission_model | string | Commission model |
| data.list.skus.commission_tier_setting | string | Commission tier settings |
| data.list.skus.commission_rate | number | Commission rate (percentage) |
| data.list.skus.standard_commission_rate | number | Standard commission rate |
| data.list.skus.shop_ads_commission_rate | number | Shop Ads commission rate |
| data.list.skus.commission_bonus_rate | number | Bonus commission rate |
| data.list.skus.creator_commission_reward_rate | number | Creator bonus commission rate |
| data.list.skus.campaign_id | string | Campaign ID |
| data.list.skus.open_collaboration_id | string | Open collaboration ID |
| data.list.skus.target_collaboration_id | string | Target collaboration ID |
| data.list.skus.content_type | string | Shoppable content type |
| data.list.skus.content_id | string | Shoppable content ID |
| data.list.skus.content_url | string | Shoppable content URL |
| data.list.skus.is_carousel | bool | Whether the content is a carousel |
| data.list.skus.estimated_commission | object | Estimated commission |
| data.list.skus.estimated_commission.amount_raw | string | Original amount as a string |
| data.list.skus.estimated_commission.amount_value | number | Numeric amount |
| data.list.skus.estimated_commission.currency | string | Currency |
| data.list.skus.estimated_commission_base | object | Estimated commission base |
| data.list.skus.estimated_commission_base.amount_raw | string | Original amount as a string |
| data.list.skus.estimated_commission_base.amount_value | number | Numeric amount |
| data.list.skus.estimated_commission_base.currency | string | Currency |
| data.list.skus.estimated_bonus_commission | object | Estimated bonus commission |
| data.list.skus.estimated_bonus_commission.amount_raw | string | Original amount as a string |
| data.list.skus.estimated_bonus_commission.amount_value | number | Numeric amount |
| data.list.skus.estimated_bonus_commission.currency | string | Currency |
| data.list.skus.estimated_standard_commission | object | Estimated standard commission |
| data.list.skus.estimated_standard_commission.amount_raw | string | Original amount as a string |
| data.list.skus.estimated_standard_commission.amount_value | number | Numeric amount |
| data.list.skus.estimated_standard_commission.currency | string | Currency |
| data.list.skus.estimated_shop_ads_commission | object | Estimated Shop Ads commission |
| data.list.skus.estimated_shop_ads_commission.amount_raw | string | Original amount as a string |
| data.list.skus.estimated_shop_ads_commission.amount_value | number | Numeric amount |
| data.list.skus.estimated_shop_ads_commission.currency | string | Currency |
| data.list.skus.estimated_creator_commission_reward_fee | object | Estimated creator bonus commission |
| data.list.skus.estimated_creator_commission_reward_fee.amount_raw | string | Original amount as a string |
| data.list.skus.estimated_creator_commission_reward_fee.amount_value | number | Numeric amount |
| data.list.skus.estimated_creator_commission_reward_fee.currency | string | Currency |
| data.list.skus.actual_commission | object | Actual commission |
| data.list.skus.actual_commission.amount_raw | string | Original amount as a string |
| data.list.skus.actual_commission.amount_value | number | Numeric amount |
| data.list.skus.actual_commission.currency | string | Currency |
| data.list.skus.actual_commission_base | object | Actual commission base |
| data.list.skus.actual_commission_base.amount_raw | string | Original amount as a string |
| data.list.skus.actual_commission_base.amount_value | number | Numeric amount |
| data.list.skus.actual_commission_base.currency | string | Currency |
| data.list.skus.actual_bonus_commission | object | Actual bonus commission |
| data.list.skus.actual_bonus_commission.amount_raw | string | Original amount as a string |
| data.list.skus.actual_bonus_commission.amount_value | number | Numeric amount |
| data.list.skus.actual_bonus_commission.currency | string | Currency |
| data.list.skus.actual_standard_commission | object | Actual standard commission |
| data.list.skus.actual_standard_commission.amount_raw | string | Original amount as a string |
| data.list.skus.actual_standard_commission.amount_value | number | Numeric amount |
| data.list.skus.actual_standard_commission.currency | string | Currency |
| data.list.skus.actual_shop_ads_commission | object | Actual Shop Ads commission |
| data.list.skus.actual_shop_ads_commission.amount_raw | string | Original amount as a string |
| data.list.skus.actual_shop_ads_commission.amount_value | number | Numeric amount |
| data.list.skus.actual_shop_ads_commission.currency | string | Currency |
| data.list.skus.actual_creator_commission_reward_fee | object | Actual creator bonus commission |
| data.list.skus.actual_creator_commission_reward_fee.amount_raw | string | Original amount as a string |
| data.list.skus.actual_creator_commission_reward_fee.amount_value | number | Numeric amount |
| data.list.skus.actual_creator_commission_reward_fee.currency | string | Currency |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "list": [
            {
                "media_id": "xxxxxx",
                "platform_order_id": "xxxxxx",
                "create_time": 1729386780000,
                "status": "To-SETTLE",
                "status_label": "TO_SETTLE",
                "currency": "MXN",
                "estimated_commission": 0.94,
                "actual_commission": null,
                "skus": [
                    {
                        "platform_sku_id": "xxxxxx",
                        "product_id": "xxxxxx",
                        "product_name": "xxxxxx",
                        "shop_name": "xxxxxx",
                        "cover": "https://xxxxxx",
                        "quantity": 1,
                        "returned_quantity": 0,
                        "refunded_quantity": 0,
                        "price": {
                            "amount_raw": "10",
                            "amount_value": 10.0,
                            "currency": "MXN"
                        },
                        "commission_model": "xxxxxx",
                        "commission_tier_setting": "xxxxxx",
                        "commission_rate": 10.0,
                        "standard_commission_rate": 10.0,
                        "shop_ads_commission_rate": null,
                        "commission_bonus_rate": null,
                        "creator_commission_reward_rate": null,
                        "campaign_id": "xxxxxx",
                        "open_collaboration_id": "xxxxxx",
                        "target_collaboration_id": "xxxxxx",
                        "content_type": "VIDEO",
                        "content_id": "xxxxxx",
                        "content_url": "https://xxxxxx",
                        "is_carousel": false,
                        "estimated_commission": {
                            "amount_raw": "0.94",
                            "amount_value": 0.94,
                            "currency": "MXN"
                        },
                        "estimated_commission_base": {
                            "amount_raw": "10",
                            "amount_value": 10.0,
                            "currency": "MXN"
                        },
                        "estimated_bonus_commission": {
                            "amount_raw": "",
                            "amount_value": null,
                            "currency": ""
                        },
                        "estimated_standard_commission": {
                            "amount_raw": "0.94",
                            "amount_value": 0.94,
                            "currency": "MXN"
                        },
                        "estimated_shop_ads_commission": {
                            "amount_raw": "",
                            "amount_value": null,
                            "currency": ""
                        },
                        "estimated_creator_commission_reward_fee": {
                            "amount_raw": "",
                            "amount_value": null,
                            "currency": ""
                        },
                        "actual_commission": {
                            "amount_raw": "",
                            "amount_value": null,
                            "currency": ""
                        },
                        "actual_commission_base": {
                            "amount_raw": "",
                            "amount_value": null,
                            "currency": ""
                        },
                        "actual_bonus_commission": {
                            "amount_raw": "",
                            "amount_value": null,
                            "currency": ""
                        },
                        "actual_standard_commission": {
                            "amount_raw": "",
                            "amount_value": null,
                            "currency": ""
                        },
                        "actual_shop_ads_commission": {
                            "amount_raw": "",
                            "amount_value": null,
                            "currency": ""
                        },
                        "actual_creator_commission_reward_fee": {
                            "amount_raw": "",
                            "amount_value": null,
                            "currency": ""
                        }
                    }
                ]
            }
        ]
    }
}
```
