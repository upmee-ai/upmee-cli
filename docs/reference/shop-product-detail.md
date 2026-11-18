# Get Product Details

### Request URL

`https://www.upmee.cc/open_api/shop/product/detail`

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
| product_id | Required | string | Product ID |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "media_id": "xxxxxx",
    "product_id": "xxxxxx"
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| product_id | string | Product ID |
| title | string | Product title |
| min_price | float | Minimum price |
| max_price | float | Maximum price |
| currency | string | Currency code |
| commission_rate | number | Commission rate as an integer. For example, `1234` means 12.34%. |
| inventory_status | string | Inventory status |
| detail_link | string | Product detail page URL |
| shop_name | string | Name of the shop that lists the product |
| main_images | []object | List of main product images |
| main_images.original_url | string | Original image URL |
| main_images.url | string | CDN-cached image URL |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "product_id": "xxxxxx",
        "title": "xxxxxx",
        "max_price": 20.5,
        "min_price": 20.5,
        "currency": "USD",
        "commission_rate": 5000,
        "inventory_status": "IN_STOCK",
        "detail_link": "xxxxxx",
        "shop_name": "xxxxxx",
        "main_images": [
            {
                "original_url": "https://xxxxxx",
                "url": "https://xxxxxx"
            },
            {
                "original_url": "https://xxxxxx",
                "url": "https://xxxxxx"
            },
            {
                "original_url": "https://xxxxxx",
                "url": "https://xxxxxx"
            },
            {
                "original_url": "https://xxxxxx",
                "url": "https://xxxxxx"
            },
            {
                "original_url": "https://xxxxxx",
                "url": "https://xxxxxx"
            },
            {
                "original_url": "https://xxxxxx",
                "url": "https://xxxxxx"
            },
            {
                "original_url": "https://xxxxxx",
                "url": "https://xxxxxx"
            },
            {
                "original_url": "https://xxxxxx",
                "url": "https://xxxxxx"
            },
            {
                "original_url": "https://xxxxxx",
                "url": "https://xxxxxx"
            }
        ]
    }
}
```
