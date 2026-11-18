# List TikTok Spark Ads Authorization Tasks

### Request URL

`https://www.upmee.cc/open_api/media/post/authorize/task/list`

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
| task_ids | Optional | []number | Filter by task ID. If omitted, returns all tasks for the team. |
| page | Required | number | Page number, starting at 1 |
| page_size | Required | number | Items per page |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "page_size": 20,
    "page": 1
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| list | []object | Authorization task list |
| list.task_id | number | Task ID |
| list.media_id | number | Social account ID |
| list.item_ids | []string | List of video IDs included in the task |
| list.task_name | string | Task name |
| list.status | number | Task status. Supported values:<br>- `1`: Generating (initialized)<br>- `2`: Partially failed<br>- `3`: All failed<br>- `4`: All succeeded |
| list.create_time | number | Task creation timestamp in milliseconds. Returned only when available. |
| list.result | []object | Authorization result for each video. May be empty until the task finishes. |
| list.result.item_id | string | Video ID |
| list.result.auth_code | string | Generated authorization code. Returned only on success. |
| list.result.start_time | number | Authorization code activation timestamp in milliseconds. Returned only when available. |
| list.result.end_time | number | Authorization code expiration timestamp in milliseconds. Returned only when available. |
| list.result.authorization_days | number | Authorization duration in days. Returned only when available. |
| list.result.failed_reason | string | Reason for failure. Returned only on failure. |
| page | number | Current page number |
| page_size | number | Items per page |
| total_size | number | Total items |
| total_page | number | Total pages |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "list": [
            {
                "task_id": "xxxxxx",
                "media_id": "xxxxxx",
                "item_ids": [
                    "xxxxxx"
                ],
                "task_name": "xxxxxx",
                "status": 4,
                "create_time": 1783800162000,
                "result": [
                    {
                        "item_id": "xxxxxx",
                        "auth_code": "xxxxxx",
                        "start_time": 1783828965000,
                        "end_time": 1784433765000,
                        "authorization_days": 7
                    }
                ]
            }
        ],
        "page": 1,
        "page_size": 20,
        "total_size": 1,
        "total_page": 1
    }
}
```
