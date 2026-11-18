# Create an Image Upscaling Task

### Request URL

`https://www.upmee.cc/open_api/ai/generation/task/create/image_upscale`

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
| input_image_ids | Required | array | List of input image object_id values as strings. Provide 1–10 IDs. Each image can contain up to 1,153,433 pixels (around 1280 × 900). |
| output_format | Required | string | Output format.Allowed values:<br>- `swinir`: PNG / WEBP / JPG |
| upscale_model | Optional | string | Upscaling model. Defaults to `swinir` if omitted.Allowed values:<br>- `swinir`: SwinIR |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "input_image_ids": [
        "xxxxxx"
    ],
    "output_format": "PNG",
    "upscale_model": "swinir"
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
