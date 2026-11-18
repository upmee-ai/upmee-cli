# Delete a Comment

### Request URL

`https://www.upmee.cc/open_api/media/item/comment/del`

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
| item_id | Required | string | Video ID |
| comment_id | Required | string | ID of the comment to delete. Obtain it from the comment list endpoint. |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "item_id": "xxxxxx",
    "comment_id": "xxxxxx"
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| code | integer | Application status code. `0` indicates success. |
| message | string | Response message. On failure, it describes the reason for the error. |
| request_id | string | Unique request ID for troubleshooting. |
| data | object | Response data. An empty object `{}` is returned on success. |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {}
}
```
