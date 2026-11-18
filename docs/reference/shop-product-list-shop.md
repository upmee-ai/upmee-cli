# List Products in Shops Linked to Official or Marketing Accounts

### Request URL

`https://www.upmee.cc/open_api/shop/product/list/shop`

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
| keyword | Optional | string | Product name keyword |
| order | Optional | string | Sort order:<br>- `PRODUCT_ID_DESC`: Product ID, descending (default)<br>- `PRICE_DESC`: Price, highest first<br>- `PRICE_ASC`: Price, lowest first<br>- `SALE_DESC`: Sales volume, highest first |
| cursor | Optional | string | Pagination cursor. Pass an empty string on the first request, then pass the `cursor` from the previous response. |
| count | Optional | number | Items per page. Defaults to 20. |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "media_id": "xxxxxx",
    "keyword": "xxxxxx",
    "order": "PRICE_DESC",
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
                "is_added": true,
                "id": "xxxxxx",
                "cover_id": "xxxxxx",
                "cover": "https://xxxxxx",
                "source_cover": "https://xxxxxx",
                "name": "xxxxxx",
                "min_price": 10,
                "max_price": 10,
                "currency": "MXN",
                "brand_name": "xxxxxx"
            }
        ],
        "cursor": "xxxxxx",
        "has_more": false,
        "after": "xxxxxx"
    }
}
```
