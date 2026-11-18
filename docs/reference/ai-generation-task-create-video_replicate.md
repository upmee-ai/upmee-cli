# Create a Viral Video Replication Task

### Request URL

`https://www.upmee.cc/open_api/ai/generation/task/create/video_replicate`

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
| video_script_analysis_data | Required | object | Viral video replication task data. |
| video_script_analysis_data.source_video | Required | object | Source video. |
| video_script_analysis_data.source_video.object_id | Required | string | Uploaded video object_id. Maximum file size: 1 GB. |
| video_script_analysis_data.num_result | Required | integer | Number of videos to generate. |
| video_script_analysis_data.language | Optional | string | Target language. |
| video_script_analysis_data.task_name | Required | string | Task name. Must contain 1–50 characters. |
| video_script_analysis_data.reference_images | Required | array | Reference images, as objects. At least one image is required, up to 10 MB each. |
| video_script_analysis_data.reference_images.object_id | Required | string | Reference image object_id. |
| video_script_analysis_data.additional_prompt | Optional | string | Product introduction. Maximum of 1000 characters. |
| video_script_analysis_data.model | Required | string | Video model.Allowed values:<br>- `sora-2-community`: Sora 2 (third-party)<br>- `veo-3.1-fast-community`: Veo 3.1 Fast (third-party)<br>- `seedance-2.0-official`: Seedance 2.0 (official)<br>- `seedance-2.0-fast-official`: Seedance 2.0 Fast (official)<br>- `gemini-omni-1.1-flash-community`: Gemini Omni 1.1 Flash (third-party)<br>- `kling-v3-omni-community`: Kling V3 Omni (third-party)<br>- `grok-1.5-community`: Grok 1.5 (third-party)<br>- `seedance-2.0-mini-community`: Seedance 2.0 mini (third-party)<br>- `seedance-2.0-mini-official`: Seedance 2.0 mini (official)<br>- `muse-video-community`: Muse Video (third-party) |
| video_script_analysis_data.duration | Required | integer | Duration in seconds by model:<br>- `sora-2-community`: 4 / 8 / 12<br>- `veo-3.1-fast-community`: 8<br>- `seedance-2.0-official`: 5 / 10 / 15<br>- `seedance-2.0-fast-official`: 5 / 10 / 15<br>- `gemini-omni-1.1-flash-community`: 4 / 6 / 8 / 10<br>- `kling-v3-omni-community`: 3–15 (integer)<br>- `grok-1.5-community`: 5 / 10 / 15 / 20 / 25 / 30<br>- `seedance-2.0-mini-community`: 5 / 10 / 15<br>- `seedance-2.0-mini-official`: 5 / 10 / 15<br>- `muse-video-community`: 10 |
| video_script_analysis_data.aspect_ratio | Required | string | Aspect ratio by model:<br>- `sora-2-community`: 16:9 / 9:16<br>- `veo-3.1-fast-community`: 16:9 / 9:16<br>- `seedance-2.0-official`: 16:9 / 9:16 / 4:3 / 3:4 / 1:1 / 21:9<br>- `seedance-2.0-fast-official`: 16:9 / 9:16 / 4:3 / 3:4 / 1:1 / 21:9<br>- `gemini-omni-1.1-flash-community`: 16:9 / 9:16<br>- `kling-v3-omni-community`: 16:9 / 9:16 / 1:1<br>- `grok-1.5-community`: 16:9 / 3:2 / 1:1 / 2:3 / 9:16<br>- `seedance-2.0-mini-community`: 16:9 / 4:3 / 1:1 / 3:4 / 9:16 / 21:9<br>- `seedance-2.0-mini-official`: 16:9 / 4:3 / 1:1 / 3:4 / 9:16 / 21:9<br>- `muse-video-community`: 16:9 / 4:3 / 3:2 / 1:1 / 2:3 / 3:4 / 9:16 |
| video_script_analysis_data.resolution | Required | string | Resolution by model:<br>- `sora-2-community`: 720P<br>- `veo-3.1-fast-community`: 1080P<br>- `seedance-2.0-official`: 720P<br>- `seedance-2.0-fast-official`: 720P<br>- `gemini-omni-1.1-flash-community`: 1080P<br>- `kling-v3-omni-community`: 720P / 1080P / 4K<br>- `grok-1.5-community`: 720P<br>- `seedance-2.0-mini-community`: 720P / 480P<br>- `seedance-2.0-mini-official`: 720P / 480P<br>- `muse-video-community`: 720P |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "video_script_analysis_data": {
        "source_video": {
            "object_id": "xxxxxx"
        },
        "num_result": 1,
        "language": "en",
        "task_name": "xxxxxx",
        "reference_images": [
            {
                "object_id": "xxxxxx"
            }
        ],
        "additional_prompt": "xxxxxx",
        "model": "veo-3.1-fast-community",
        "duration": 8,
        "aspect_ratio": "9:16",
        "resolution": "1080P"
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
