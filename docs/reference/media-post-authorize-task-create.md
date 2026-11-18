# Create a TikTok Spark Ads Authorization Task

### Request URL

`https://www.upmee.cc/open_api/media/post/authorize/task/create`

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
| media_id | Required | number | Target TikTok account ID. The account must already be linked to the team. |
| item_ids | Required | []string | List of video IDs to authorize. Specify 1–20 IDs. |
| task_name | Required | string | Task name. Maximum length: 50 characters. |
| authorization_days | Required | number | Authorization duration in days. Supported values:<br>- `7`: Authorize for 7 days<br>- `30`: Authorize for 30 days<br>- `60`: Authorize for 60 days<br>- `365`: Authorize for 365 days |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "media_id": "xxxxxx",
    "item_ids": [
        "xxxxxx"
    ],
    "task_name": "xxxxxx",
    "authorization_days": 7
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| task_id | number | ID of the authorization task created |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "task_id": "xxxxxx"
    }
}
```
