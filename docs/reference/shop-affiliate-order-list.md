# List Affiliate Orders

### Request URL

`https://www.upmee.cc/open_api/shop/affiliate/order/list`

### HTTP Method

`POST`

### Request Headers

<!-- api-fields -->

| Field | Required <!-- api-tag --> | Type | Description |
| --- | --- | --- | --- |
| API-Key | Required | string | API key |
| Content-Type | Required | string | Request content type. Allowed format: application/json |

### Request Parameters

<!-- api-fields -->

| Field | Required <!-- api-tag --> | Type | Description |
| --- | --- | --- | --- |
| team_id | Required | string | Team ID |
| media_id | Optional | string | media\_id of a single creator account. Specify either media\_id or media\_ids. If neither is supplied, the query covers all available Creator accounts in the team. |
| media_ids | Optional | string[] | List of media\_id values for multiple creator accounts |
| status | Optional | string | Order status filter. An empty value or ALL includes all statuses. Allowed values: `PENDING_CONFIRM` Pending confirmation；`AWAITING_PAYMENT` Awaiting buyer payment；`TO_SETTLE` Pending settlement；`SETTLED` Settled；`REFUNDED` Refunded or canceled；`FROZEN` Commission frozen |
| time_filter | Optional | string | Preset time filter. If start\_time and end\_time are also supplied, the custom range takes precedence. Allowed values: `unlimited` No time filtering；`today` Today；`yesterday` Yesterday；`latest_7_days` Last 7 days；`latest_30_days` Last 30 days；`latest_90_days` Last 90 days；`latest_365_days` Last 365 days |
| start_time | Conditionally required | number | Custom start timestamp in milliseconds. Supply it together with end\_time. If only one boundary is supplied or the start is later than the end, the request returns “Invalid time range.” |
| end_time | Conditionally required | number | Custom end timestamp in milliseconds. The filter is create\_time \< end\_time. |
| query | Optional | string | Keyword search, such as order ID, product ID, SKU ID, product name, affiliate campaign ID, open collaboration ID, or target collaboration ID |
| order_by | Optional | string | Sort field。Allowed values:<br>- `create_time`: Order placement time (default)<br>- `estimated_commission`: Estimated commission<br>- `actual_commission`: Actual commission<br>- `price`: Product amount<br>- `price_amount`: Product amount<br>- `standard_commission_rate`: Standard commission rate |
| order_desc | Optional | bool | Whether to sort in descending order. If order\_by is omitted, sorts by creation time in descending order. |
| page | Required | number | Page number, starting at 1 |
| page_size | Required | number | Items per page, up to 50 |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "media_id": "xxxxxx",
    "status": "TO_SETTLE",
    "start_time": 1727740800000,
    "end_time": 1728345600000,
    "page": 1,
    "page_size": 20,
    "order_by": "create_time",
    "order_desc": true
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| code | int | 0 indicates success |
| message | string | Status message |
| request_id | string | Unique request ID |
| data | object | Response data |
| data.list | object[] | List of orders |
| data.list.media_id | string | Creator account ID |
| data.list.platform_order_id | string | Platform order number |
| data.list.create_time | number | Order placement timestamp in milliseconds |
| data.list.delivery_time | number | Shipment timestamp in milliseconds. Omitted if unavailable. |
| data.list.status | string | Original platform status |
| data.list.status_label | string | Normalized status. Allowed values: `PENDING_CONFIRM` Pending confirmation；`AWAITING_PAYMENT` Awaiting buyer payment；`TO_SETTLE` Pending settlement；`SETTLED` Settled；`REFUNDED` Refunded or canceled；`FROZEN` Commission frozen |
| data.list.first_product_id | string | First product ID |
| data.list.product_name | string | Product name |
| data.list.cover | string | Product cover image URL |
| data.list.currency | string | Order commission currency. Uses the currency from the order summary when available. |
| data.list.estimated_commission | number | Estimated commission summed across all SKUs in the order. Expressed in major currency units, such as euros for EUR or whole Vietnamese đồng for VND. |
| data.list.actual_commission | number | Actual commission. null if unavailable. As with estimated commission, this is the order-level total in major currency units. |
| data.list.price_amount | number | Product amount. Uses the unit price of the first SKU in the order, in major currency units. |
| data.list.standard_commission_rate | number | Standard commission rate as a percentage. For example, 10 means 10%. |
| data.page_info | object | Pagination information |
| data.page_info.page | number | Current page |
| data.page_info.page_size | number | Items per page |
| data.page_info.total_size | number | Total items |
| data.page_info.total_page | number | Total pages |

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
                "first_product_id": "xxxxxx",
                "product_name": "xxxxxx",
                "cover": "https://xxxxxx",
                "currency": "MXN",
                "estimated_commission": 0.94,
                "actual_commission": null,
                "price_amount": 10.0,
                "standard_commission_rate": 10.0
            }
        ],
        "page_info": {
            "page": 1,
            "page_size": 20,
            "total_size": 100,
            "total_page": 5
        }
    }
}
```
