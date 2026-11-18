# List Product Marketplace Products

### Request URL

`https://www.upmee.cc/open_api/shop/product/list/open_collaboration`

### HTTP Method

`POST`

### Request Headers

<!-- api-fields -->

| Field | Required <!-- api-tag --> | Type | Description |
| --- | --- | --- | --- |
| API-Key | Required | string | API key |
| Content-Type | Required | string | Request content type.<br>Allowed format: `application/json`. |

### Request Parameters

<!-- api-fields -->

| Field | Required <!-- api-tag --> | Type | Description |
| --- | --- | --- | --- |
| team_id | Required | number | Team ID |
| media_id | Required | number | Account ID. Only TikTok Shop Creator accounts are supported. |
| keywords | Optional | []string | List of keywords. Returns results that match any of the keywords. |
| order | Optional | string | Sort order:<br>- `COMMISSION_RATE_ASC`: Commission rate, lowest first<br>- `COMMISSION_RATE_DESC`: Commission rate, highest first<br>- `PRICE_ASC`: Price, lowest first<br>- `PRICE_DESC`: Price, highest first<br>- `SALE_DESC`: Sales volume, highest first |
| price_filter | Optional | object | Price range filter, in the product’s currency |
| price_filter.min | Optional | number | Minimum price. Applies when the value is greater than 0. |
| price_filter.max | Optional | number | Maximum price. Applies when the value is greater than 0. |
| commission_rate_filter | Optional | object | Commission rate range filter |
| commission_rate_filter.min | Optional | number | Minimum commission rate, expressed as an integer in basis points. Applies only when the value is greater than `1000`. `1000` basis points equals `10%`. |
| commission_rate_filter.max | Optional | number | Maximum commission rate, expressed as an integer in basis points. Applies only when the value is greater than `1000`. `1000` basis points equals `10%`. |
| cursor | Optional | string | Pagination cursor. Pass an empty string on the first request, then pass the `cursor` from the previous response. |
| count | Optional | number | Items per page. Defaults to 20, with a minimum of 1. |

### Request Example

```json
{
    "team_id": 0,
    "media_id": 0,
    "keywords": [
        "xxxxxx"
    ],
    "order": "COMMISSION_RATE_ASC",
    "price_filter": {
        "min": 10,
        "max": 1000
    },
    "commission_rate_filter": {
        "min": 1000,
        "max": 2000
    },
    "count": 1,
    "cursor": "xxxxxx"
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| list | []object | List of products |
| list.id | string | Product ID |
| list.name | string | Product name |
| list.is_added | bool | Whether the product has been added to the showcase |
| list.cover_id | string | Cover image file ID. Populated only for products added to the showcase. |
| list.cover | string | CDN-cached cover image. Populated only for products added to the showcase. |
| list.source_cover | string | Original product cover image URL |
| list.min_price | float | Minimum price |
| list.max_price | float | Maximum price |
| list.currency | string | Currency code |
| list.brand_name | string | Brand name |
| list.has_inventory | bool | Whether the product is in stock |
| list.units_sold | number | Total units sold to date |
| list.commission_rate | number | Commission rate, expressed as an integer in basis points. For example, `1234` basis points equals `12.34%`. |
| list.commission | float | Commission amount per order |
| list.detail_link | string | Product detail page URL |
| list.sale_region | string | Sales region |
| list.shop_name | string | Shop name |
| list.category_chains | []object | Category path from the top-level category to the leaf |
| list.category_chains.id | string | Category ID |
| list.category_chains.name | string | Category name |
| list.category_chains.is_leaf | bool | Whether this is a leaf node |
| list.category_chains.parent_id | string | Parent category ID |
| cursor | string | Cursor for the next page. Empty if there are no more results. |
| has_more | bool | Whether more results are available |

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
                "min_price": 20.95,
                "max_price": 20.95,
                "currency": "USD",
                "brand_name": "xxxxxx",
                "has_inventory": false,
                "units_sold": 0,
                "commission_rate": 100,
                "commission": 0.2095,
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
                        "is_leaf": false,
                        "name": "xxxxxx",
                        "parent_id": "xxxxxx"
                    },
                    {
                        "id": "xxxxxx",
                        "is_leaf": false,
                        "name": "xxxxxx",
                        "parent_id": "xxxxxx"
                    }
                ]
            }
        ],
        "cursor": "xxxxxx",
        "has_more": true,
        "after": "xxxxxx"
    }
}
```
