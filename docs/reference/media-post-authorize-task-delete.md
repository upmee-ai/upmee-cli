# Delete a TikTok Spark Ads Authorization Task

### Request URL

`https://www.upmee.cc/open_api/media/post/authorize/task/delete`

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
| task_id | Required | number | ID of the authorization task to delete. The task must belong to this team. |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "task_id": "xxxxxx"
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
