# Remove Products from a Showcase

### Request URL

`https://www.upmee.cc/open_api/shop/product/remove`

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
| product_ids | Required | []string | List of product IDs to remove. Must contain at least one ID. |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "media_id": "xxxxxx",
    "product_ids": [
        "xxxxxx"
    ]
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| code | integer | Status code. `0` indicates success. |
| message | string | Response message. Contains the reason for failure if the request fails. |
| request_id | string | Unique request ID for troubleshooting. |
| data | object | Response data. Returns an empty object `{}` on success. |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {}
}
```
