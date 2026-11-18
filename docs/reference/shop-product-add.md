# Add Products to a Showcase

### Request URL

`https://www.upmee.cc/open_api/shop/product/add`

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
| add_type | Required | string | Method for adding products:<br>- `PRODUCT_ID`: Add by product ID<br>- `PRODUCT_LINK`: Add by product URL |
| product_ids | Conditionally required | []string | List of product IDs. Required when `add_type=PRODUCT_ID`. |
| product_links | Conditionally required | []string | List of product URLs. Required when `add_type=PRODUCT_LINK`. Up to 20 per request. Query parameters are removed automatically. |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "media_id": "xxxxxx",
    "add_type": "xxxxxx",
    "product_ids": [
        "xxxxxx"
    ]
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| success | number | Number of products added |
| failed | number | Number of products that could not be added |
| errors | []object | Error details. Omitted if all products were added successfully. |
| errors.product_id | string | ID or URL of the product that could not be added |
| errors.message | string | Reason for failure |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "success": 1,
        "failed": 0
    }
}
```
