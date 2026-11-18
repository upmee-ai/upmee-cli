# Create an Image-to-SVG Task

### Request URL

`https://www.upmee.cc/open_api/ai/generation/task/create/image_to_svg`

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
| team_id | Required | string | Team ID。 |
| data | Required | object | SVG conversion task data. |
| data.task_name | Required | string | Task name. Must contain 1–50 characters. |
| data.images | Required | array | Images to convert, as objects. Provide `1` to `20` images. |
| data.images.object_id | Required | string | Image object_id. |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "data": {
        "task_name": "xxxxxx",
        "images": [
            {
                "object_id": "xxxxxx"
            }
        ]
    }
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| code | integer | Application status code. `0` indicates success. |
| message | string | Response message. `OK` indicates success. |
| request_id | string | Request trace ID. |
| data | object | Response data。 |
| data.task_group_id | string | Task group ID. |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "task_group_id": "xxxxxx"
    }
}
```
