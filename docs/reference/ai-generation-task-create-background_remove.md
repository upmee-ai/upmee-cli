# Create an Image Background Removal Task

### Request URL

`https://www.upmee.cc/open_api/ai/generation/task/create/background_remove`

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
| background_removal_data | Required | object | Background removal parameters. |
| background_removal_data.model | Optional | string | Model. Defaults to `rmbg-v2.0` if omitted.Allowed values:<br>- `rmbg-v2.0`: RMBG V2.0<br>- `pixnet-v2.0`: Pixnet V2.0 |
| background_removal_data.input_image_ids | Required | array | List of input image object_id values as strings. Provide `1` to `10` IDs. The server limits each image’s size. |
| background_removal_data.output_format | Required | string | Output format.Allowed values:<br>- `rmbg-v2.0`: PNG / WEBP<br>- `pixnet-v2.0`: PNG / JPEG |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "background_removal_data": {
        "model": "rmbg-v2.0",
        "input_image_ids": [
            "xxxxxx"
        ],
        "output_format": "PNG"
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
