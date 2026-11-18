# Create an AI Video Generation Task

### Request URL

`https://www.upmee.cc/open_api/ai/generation/task/create/video`

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
| ai_video_generation_data | Required | object | Video generation task parameters. |
| ai_video_generation_data.task_name | Required | string | Task name. Must be nonempty and at most 50 characters. |
| ai_video_generation_data.model | Required | string | Video generation model.<br>- `sora-2-community`: Sora 2 (third-party)<br>- `veo-3.1-fast-community`: Veo 3\.1 Fast (third-party)<br>- `seedance-2.0-official`: Seedance 2\.0 (official)<br>- `seedance-2.0-fast-official`: Seedance 2\.0 Fast (official)<br>- `gemini-omni-1.1-flash-community`: Gemini Omni 1\.1 Flash (third-party)<br>- `kling-v3-omni-community`: Kling V3 Omni (third-party)<br>- `grok-1.5-community`: Grok 1\.5 (third-party)<br>- `seedance-2.0-mini-community`: Seedance 2\.0 mini (third-party)<br>- `seedance-2.0-mini-official`: Seedance 2\.0 mini (official)<br>- `muse-video-community`: Muse Video (third-party) |
| ai_video_generation_data.reference_images | Required | array | List of reference images. Provide at least one. Images beyond the model limit are dropped. Each image must be at most 10 MB.<br>Supported counts by model:<br>- `sora-2-community`: Up to 1<br>- `veo-3.1-fast-community`: Up to 1<br>- `gemini-omni-1.1-flash-community`: Up to 1<br>- `kling-v3-omni-community`: Up to 7<br>- `grok-1.5-community`: Up to 7<br>- `seedance-2.0-official`: Up to 9<br>- `seedance-2.0-fast-official`: Up to 9<br>- `seedance-2.0-mini-community`: Up to 9<br>- `seedance-2.0-mini-official`: Up to 9<br>- `muse-video-community`: Up to 9 |
| ai_video_generation_data.reference_images.object_id | Required | string | Reference image file object\_id. |
| ai_video_generation_data.prompts | Required | array | List of prompts. Up to 20 prompts, each at most 2,000 characters. |
| ai_video_generation_data.duration | Required | integer | Video duration in seconds. Validated against the selected model.<br>Supported durations (seconds) by model:<br>- `sora-2-community`: 4 / 8 / 12<br>- `veo-3.1-fast-community`: 8<br>- `seedance-2.0-official`: 5 / 10 / 15<br>- `seedance-2.0-fast-official`: 5 / 10 / 15<br>- `gemini-omni-1.1-flash-community`: 4 / 6 / 8 / 10<br>- `kling-v3-omni-community`: 3–15 (integer)<br>- `grok-1.5-community`: 5 / 10 / 15 / 20 / 25 / 30<br>- `seedance-2.0-mini-community`: 5 / 10 / 15<br>- `seedance-2.0-mini-official`: 5 / 10 / 15<br>- `muse-video-community`: 10 |
| ai_video_generation_data.aspect_ratio | Required | string | Video aspect ratio. Validated against the selected model.<br>Supported aspect ratios by model:<br>- `sora-2-community`: 16:9 / 9:16<br>- `veo-3.1-fast-community`: 16:9 / 9:16<br>- `seedance-2.0-official`: 16:9 / 9:16 / 4:3 / 3:4 / 1:1 / 21:9<br>- `seedance-2.0-fast-official`: 16:9 / 9:16 / 4:3 / 3:4 / 1:1 / 21:9<br>- `gemini-omni-1.1-flash-community`: 16:9 / 9:16<br>- `kling-v3-omni-community`: 16:9 / 9:16 / 1:1<br>- `grok-1.5-community`: 16:9 / 3:2 / 1:1 / 2:3 / 9:16<br>- `seedance-2.0-mini-community`: 16:9 / 4:3 / 1:1 / 3:4 / 9:16 / 21:9<br>- `seedance-2.0-mini-official`: 16:9 / 4:3 / 1:1 / 3:4 / 9:16 / 21:9<br>- `muse-video-community`: 16:9 / 4:3 / 3:2 / 1:1 / 2:3 / 3:4 / 9:16 |
| ai_video_generation_data.resolution | Required | string | Video resolution. Validated against the selected model.<br>Supported resolutions by model:<br>- `sora-2-community`: 720P<br>- `veo-3.1-fast-community`: 1080P<br>- `seedance-2.0-official`: 720P<br>- `seedance-2.0-fast-official`: 720P<br>- `gemini-omni-1.1-flash-community`: 1080P<br>- `kling-v3-omni-community`: 720P / 1080P / 4K<br>- `grok-1.5-community`: 720P<br>- `seedance-2.0-mini-community`: 720P / 480P<br>- `seedance-2.0-mini-official`: 720P / 480P<br>- `muse-video-community`: 720P |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "ai_video_generation_data": {
        "task_name": "xxxxxx",
        "model": "veo-3.1-fast",
        "reference_images": [
            {
                "object_id": "xxxxxx"
            }
        ],
        "prompts": [
            "xxxxxx"
        ],
        "duration": 8,
        "aspect_ratio": "16:9",
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
