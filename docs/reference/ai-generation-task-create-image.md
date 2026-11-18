# Create an AI Image Generation Task

### Request URL

`https://www.upmee.cc/open_api/ai/generation/task/create/image`

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
| data | Required | object | Image generation parameters. |
| data.model | Required | string | Image generation model.<br>- `seedream-5.0`: Seedream 5\.0<br>- `gpt-4o-image`: GPT\-4o\-image<br>- `flux-2-pro-fast`: Flux 2 Pro \(Fast\)<br>- `flux-2-lite-fast`: Flux 2 Lite \(Fast\)<br>- `z-image`: Z\-Image<br>- `gpt-image-2`: GPT Image 2<br>- `gpt-image-2.6`: GPT Image 2\.6<br>- `nano-banana-2.1`: Nano Banana 2\.1 |
| data.num_result | Required | integer | Images generated per prompt, from `1` to `10` for all models. |
| data.prompts | Required | array\<string\> | List of prompts. Up to `10` for all models. |
| data.output_format | Required | string | Output format.`PNG` `JPEG` `WEBP`<br>Supported output formats by model:<br>- `seedream-5.0`: PNG / JPEG<br>- `gpt-4o-image`: PNG / JPEG / WEBP<br>- `flux-2-pro-fast`: PNG / JPEG / WEBP<br>- `flux-2-lite-fast`: PNG / JPEG / WEBP<br>- `z-image`: PNG / JPEG / WEBP<br>- `gpt-image-2`: PNG<br>- `gpt-image-2.6`: PNG<br>- `nano-banana-2.1`: PNG / JPEG / WEBP |
| data.reference_images | Optional | array | Reference images in JPEG or PNG, up to 10 MB each. Exceeding the model limit returns an error.<br>Supported reference image counts by model:<br>- `seedream-5.0`: Up to 4<br>- `gpt-4o-image`: Up to 4<br>- `flux-2-pro-fast`: Up to 4<br>- `flux-2-lite-fast`: Up to 4<br>- `z-image`: Unsupported (must be empty)<br>- `gpt-image-2`: Up to 4<br>- `gpt-image-2.6`: Up to 4<br>- `nano-banana-2.1`: Up to 4 |
| data.reference_images.object_id | Required | string | Image object\_id. |
| data.aspect_ratio | Required | string | Aspect ratio. Must meet the model’s restrictions.<br>Supported aspect ratios by model:<br>- `seedream-5.0`: 21:9 / 16:9 / 3:2 / 4:3 / 1:1 / 3:4 / 2:3 / 9:16 / 9:21<br>- `gpt-4o-image`: 3:2 / 1:1 / 2:3<br>- `flux-2-pro-fast`: 21:9 / 16:9 / 3:2 / 4:3 / 1:1 / 3:4 / 2:3 / 9:16 / 9:21<br>- `flux-2-lite-fast`: 21:9 / 16:9 / 3:2 / 4:3 / 1:1 / 3:4 / 2:3 / 9:16 / 9:21<br>- `z-image`: 21:9 / 16:9 / 3:2 / 4:3 / 1:1 / 3:4 / 2:3 / 9:16 / 9:21<br>- `gpt-image-2`: 9:21 / 21:9 / 16:9 / 9:16 / 3:2 / 2:3 / 4:3 / 3:4 / 1:1<br>- `gpt-image-2.6`: 9:21 / 21:9 / 16:9 / 9:16 / 3:2 / 2:3 / 4:3 / 3:4 / 1:1<br>- `nano-banana-2.1`: 21:9 / 16:9 / 3:2 / 4:3 / 1:1 / 3:4 / 2:3 / 9:16 |
| data.resolution | Required | string | Resolution. Must meet the model’s restrictions.<br>Supported resolutions by model:<br>- `seedream-5.0`: 2K / 3K<br>- `gpt-4o-image`: 1080P<br>- `flux-2-pro-fast`: 1080P<br>- `flux-2-lite-fast`: 1080P<br>- `z-image`: 1080P<br>- `gpt-image-2`: 1080P / 2K / 4K<br>- `gpt-image-2.6`: 1080P / 2K / 4K<br>- `nano-banana-2.1`: 1080P / 2K / 4K |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "data": {
        "model": "gpt-image-2",
        "num_result": 1,
        "prompts": [
            "xxxxxx"
        ],
        "output_format": "PNG",
        "reference_images": [
            {
                "object_id": "xxxxxx"
            }
        ],
        "aspect_ratio": "1:1",
        "resolution": "1080P"
    }
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| code | integer | Response status code. `0` indicates success. |
| message | string | Response message. `OK` indicates success. |
| request_id | string | Request trace ID. |
| data | object | Response data. |
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
