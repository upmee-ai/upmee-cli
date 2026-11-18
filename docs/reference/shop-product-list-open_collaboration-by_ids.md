# Look Up Products by ID in Bulk

### Request URL

`https://www.upmee.cc/open_api/shop/product/list/open_collaboration/by_ids`

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
| team_id | Required | number | Team ID |
| media_id | Required | number | TikTok Shop creator account ID |
| product_ids | Required | string[] | List of product IDs. Whitespace and duplicates are removed automatically. Up to 20 IDs per request. |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "media_id": "xxxxxx",
    "product_ids": [
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
| data.list | object[] | List of products. IDs with no matching product are omitted. |
| data.list.is_added | bool | Whether the product has been added to the current account’s showcase |
| data.list.id | string | Product ID |
| data.list.cover_id | string | Local cover image file ID when the product has been added |
| data.list.cover | string | CDN URL of the local cover image when the product has been added |
| data.list.source_cover | string | Original TikTok cover image URL |
| data.list.name | string | Product title |
| data.list.min_price | number | Lowest price. Uses the sale price when available, otherwise the original price. |
| data.list.max_price | number | Highest price |
| data.list.currency | string | Currency |
| data.list.brand_name | string | Brand name |
| data.list.has_inventory | bool | Whether the product is in stock |
| data.list.units_sold | number | Sales volume |
| data.list.commission_rate | number | Commission rate, as an integer in basis points. For example, `1234` means `12.34%`. |
| data.list.commission | number | Commission amount |
| data.list.detail_link | string | Product detail page URL |
| data.list.sale_region | string | Sales region |
| data.list.shop_name | string | Shop name |
| data.list.category_chains | object[] | Category path |
| data.list.category_chains.id | string | Category ID |
| data.list.category_chains.is_leaf | bool | Whether this is a leaf category |
| data.list.category_chains.name | string | Category name |
| data.list.category_chains.parent_id | string | Parent category ID |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "list": [
            {
                "is_added": false,
                "id": "xxxxxx",
                "cover_id": "xxxxxx",
                "cover": "xxxxxx",
                "source_cover": "https://xxxxxx",
                "name": "xxxxxx",
                "min_price": 19.9,
                "max_price": 29.9,
                "currency": "USD",
                "brand_name": "xxxxxx",
                "has_inventory": true,
                "units_sold": 1280,
                "commission_rate": 1234,
                "commission": 2.45,
                "detail_link": "https://xxxxxx",
                "sale_region": "US",
                "shop_name": "xxxxxx",
                "category_chains": [
                    {
                        "id": "xxxxxx",
                        "is_leaf": false,
                        "name": "xxxxxx",
                        "parent_id": "xxxxxx"
                    },
                    {
                        "id": "xxxxxx",
                        "is_leaf": true,
                        "name": "xxxxxx",
                        "parent_id": "xxxxxx"
                    }
                ]
            }
        ]
    }
}
```
