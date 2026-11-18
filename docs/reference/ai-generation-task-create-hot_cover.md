# Create a Viral Cover Image Generation Task

### Request URL

`https://www.upmee.cc/open_api/ai/generation/task/create/hot_cover`

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
| data | Required | object | Viral cover image task data. |
| data.model | Required | string | Image generation model.Allowed values:<br>- `gpt-image-2`: GPT Image 2<br>- `gpt-image-2.6`: GPT Image 2.6<br>- `nano-banana-2.1`: Nano Banana 2.1<br>- `seedream-5.0`: Seedream 5.0<br>- `gpt-4o-image`: GPT-4o-image |
| data.num_result | Required | integer | Number of results to generate, from 1 to 10. |
| data.output_format | Optional | string | Output format by model:<br>- `gpt-image-2`: PNG<br>- `gpt-image-2.6`: PNG<br>- `nano-banana-2.1`: PNG / JPEG / WEBP<br>- `seedream-5.0`: PNG / JPEG<br>- `gpt-4o-image`: PNG / JPEG / WEBP |
| data.reference_images | Required | array | Exactly one reference image as an object, in JPEG or PNG and no larger than 10 MB. |
| data.reference_images.object_id | Required | string | Reference image object_id. |
| data.aspect_ratio | Required | string | Aspect ratio by model:<br>- `gpt-image-2`: 9:21 / 21:9 / 16:9 / 9:16 / 3:2 / 2:3 / 4:3 / 3:4 / 1:1<br>- `gpt-image-2.6`: 9:21 / 21:9 / 16:9 / 9:16 / 3:2 / 2:3 / 4:3 / 3:4 / 1:1<br>- `nano-banana-2.1`: 21:9 / 16:9 / 3:2 / 4:3 / 1:1 / 3:4 / 2:3 / 9:16<br>- `seedream-5.0`: 21:9 / 16:9 / 3:2 / 4:3 / 1:1 / 3:4 / 2:3 / 9:16 / 9:21<br>- `gpt-4o-image`: 3:2 / 1:1 / 2:3 |
| data.resolution | Required | string | Resolution by model:<br>- `gpt-image-2`: 1080P / 2K / 4K<br>- `gpt-image-2.6`: 1080P / 2K / 4K<br>- `nano-banana-2.1`: 1080P / 2K / 4K<br>- `seedream-5.0`: 2K / 3K<br>- `gpt-4o-image`: 1080P |
| data.language | Optional | string | Prompt language. Defaults to en if omitted. |
| data.video_theme | Optional | string | Video topic description. Maximum of 1000 characters. |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "data": {
        "model": "gpt-image-2",
        "num_result": 1,
        "output_format": "PNG",
        "reference_images": [
            {
                "object_id": "xxxxxx"
            }
        ],
        "aspect_ratio": "1:1",
        "resolution": "1080P",
        "language": "en",
        "video_theme": "xxxxxx"
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
