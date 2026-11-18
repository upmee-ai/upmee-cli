# List AI Generation Tasks

### Request URL

`https://www.upmee.cc/open_api/ai/generation/task/list`

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
| task_type | Required | string | Task type。Allowed values:<br>- `video`: Product video generation<br>- `image`: Image generation<br>- `video_replicate`: Viral video replication<br>- `hot_cover`: Viral cover image<br>- `background_remove`: Background removal<br>- `image_upscale`: Image upscaling<br>- `image_to_svg`: Image-to-SVG conversion<br>- `text_to_speech`: Text-to-speech generation |
| group_ids | Optional | array | List of task group IDs as strings. |
| task_group_states | Optional | array | Filter by task group status. Elements are integers.Allowed values:<br>- `1`: Generating<br>- `2`: Partially failed<br>- `3`: All failed<br>- `4`: AllSucceeded |
| start_time | Optional | integer | Start of the creation time range, in milliseconds. |
| end_time | Optional | integer | End of the creation time range, in milliseconds. |
| order_by | Optional | string | Sort field. Typically `create_time`. |
| order_desc | Optional | boolean | Whether to sort in descending order. Defaults to `false`. |
| page | Required | integer | Page number, starting at 1. |
| page_size | Required | integer | Items per page, from 1 to 50. |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "task_type": "image_to_svg",
    "page": 1,
    "page_size": 20,
    "order_by": "create_time",
    "order_desc": true
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
| data.list | array | List of task groups as objects. |
| data.list.group_id | string | Task group ID. |
| data.list.state | integer | Task group status.Allowed values:<br>- `1`: Generating<br>- `2`: Partially failed<br>- `3`: All failed<br>- `4`: AllSucceeded |
| data.list.create_time | integer | Creation time in milliseconds. |
| data.list.tasks | array | List of subtasks as objects. See the tables below for each type’s structure. |
| data.page | integer | Current page。 |
| data.page_size | integer | Items per page。 |
| data.total_size | integer | Total items。 |
| data.total_page | integer | Total pages。 |

The following sections describe the type-specific data and subtask fields for entries in `data.list`.

#### Product video generation (task_type=`video`)

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| data.list.ai_video_generation_data | object | Product video task parameters. |
| data.list.ai_video_generation_data.task_name | string | Task name. |
| data.list.ai_video_generation_data.reference_images | array | Reference images, as objects. |
| data.list.ai_video_generation_data.reference_images.object_id | string | Reference image object_id. |
| data.list.ai_video_generation_data.prompts | array | Prompts as strings. |
| data.list.ai_video_generation_data.model | string | Video model.Allowed values:<br>- `sora-2-community`: Sora 2 (third-party)<br>- `veo-3.1-fast-community`: Veo 3.1 Fast (third-party)<br>- `seedance-2.0-official`: Seedance 2.0 (official)<br>- `seedance-2.0-fast-official`: Seedance 2.0 Fast (official)<br>- `gemini-omni-1.1-flash-community`: Gemini Omni 1.1 Flash (third-party)<br>- `kling-v3-omni-community`: Kling V3 Omni (third-party)<br>- `grok-1.5-community`: Grok 1.5 (third-party)<br>- `seedance-2.0-mini-community`: Seedance 2.0 mini (third-party)<br>- `seedance-2.0-mini-official`: Seedance 2.0 mini (official)<br>- `muse-video-community`: Muse Video (third-party) |
| data.list.ai_video_generation_data.duration | integer | Duration in seconds. |
| data.list.ai_video_generation_data.aspect_ratio | string | Aspect ratio. |
| data.list.ai_video_generation_data.resolution | string | Resolution. |
| data.list.tasks | array | List of subtasks as objects. |
| data.list.tasks.state | integer | Subtask status.Allowed values:<br>- `1`: Generating<br>- `2`: Failed<br>- `3`: Succeeded |
| data.list.tasks.title | string | Title. May be empty. |
| data.list.tasks.reasons | array | Failure reasons as strings. |
| data.list.tasks.data | array | Output files, as objects. |
| data.list.tasks.data.file_id | string | File ID. |
| data.list.tasks.data.file_url | string | File URL. |

#### Image generation (task_type=`image`)

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| data.list.data | object | Image generation task parameters. |
| data.list.data.model | string | Image generation model.Allowed values:<br>- `seedream-5.0`: Seedream 5.0<br>- `gpt-4o-image`: GPT-4o-image<br>- `flux-2-pro-fast`: Flux 2 Pro (Fast)<br>- `flux-2-lite-fast`: Flux 2 Lite (Fast)<br>- `z-image`: Z-Image<br>- `gpt-image-2`: GPT Image 2<br>- `gpt-image-2.6`: GPT Image 2.6<br>- `nano-banana-2.1`: Nano Banana 2.1 |
| data.list.data.num_result | integer | Number of results to generate. |
| data.list.data.prompts | array | Prompts as strings. |
| data.list.data.output_format | string | Output format.Allowed values:<br>- `PNG`: PNG<br>- `JPEG`: JPEG<br>- `WEBP`: WEBP |
| data.list.data.reference_images | array | Reference images, as objects. |
| data.list.data.reference_images.object_id | string | Reference image object_id. |
| data.list.data.aspect_ratio | string | Aspect ratio. |
| data.list.data.resolution | string | Resolution. |
| data.list.tasks | array | List of subtasks as objects. |
| data.list.tasks.task_id | string | Subtask ID. |
| data.list.tasks.state | integer | Subtask status.Allowed values:<br>- `1`: Generating<br>- `2`: Failed<br>- `3`: Succeeded |
| data.list.tasks.data | array | Output files, as objects. |
| data.list.tasks.data.file_id | string | File ID. |
| data.list.tasks.data.file_url | string | File URL. |

#### Viral video replication (task_type=`video_replicate`)

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| data.list.video_script_analysis_data | object | Viral video replication task parameters. |
| data.list.video_script_analysis_data.source_video | object | Source video. |
| data.list.video_script_analysis_data.source_video.object_id | string | Video object_id. |
| data.list.video_script_analysis_data.num_result | integer | Number of results to generate. |
| data.list.video_script_analysis_data.language | string | Target language. |
| data.list.video_script_analysis_data.task_name | string | Task name. |
| data.list.video_script_analysis_data.reference_images | array | Reference images, as objects. |
| data.list.video_script_analysis_data.reference_images.object_id | string | Reference image object_id. |
| data.list.video_script_analysis_data.additional_prompt | string | Product introduction. |
| data.list.video_script_analysis_data.model | string | Video model.Allowed values:<br>- `sora-2-community`: Sora 2 (third-party)<br>- `veo-3.1-fast-community`: Veo 3.1 Fast (third-party)<br>- `seedance-2.0-official`: Seedance 2.0 (official)<br>- `seedance-2.0-fast-official`: Seedance 2.0 Fast (official)<br>- `gemini-omni-1.1-flash-community`: Gemini Omni 1.1 Flash (third-party)<br>- `kling-v3-omni-community`: Kling V3 Omni (third-party)<br>- `grok-1.5-community`: Grok 1.5 (third-party)<br>- `seedance-2.0-mini-community`: Seedance 2.0 mini (third-party)<br>- `seedance-2.0-mini-official`: Seedance 2.0 mini (official)<br>- `muse-video-community`: Muse Video (third-party) |
| data.list.video_script_analysis_data.duration | integer | Duration in seconds. |
| data.list.video_script_analysis_data.aspect_ratio | string | Aspect ratio. |
| data.list.video_script_analysis_data.resolution | string | Resolution. |
| data.list.video_script_analysis_data.script_prompt | string | Script extracted from the viral video. Populated as the task runs. |
| data.list.video_script_analysis_data.input_prompt | string | Replication prompt used to generate the video. Populated as the task runs. |
| data.list.tasks | array | List of subtasks as objects. |
| data.list.tasks.state | integer | Subtask status.Allowed values:<br>- `1`: Generating<br>- `2`: Failed<br>- `3`: Succeeded |
| data.list.tasks.title | string | Title. May be empty. |
| data.list.tasks.reasons | array | Failure reasons as strings. |
| data.list.tasks.data | array | Output files, as objects. |
| data.list.tasks.data.file_id | string | File ID. |
| data.list.tasks.data.file_url | string | File URL. |

#### Viral cover image generation (task_type=`hot_cover`)

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| data.list.data | object | Viral cover image task parameters. |
| data.list.data.model | string | Image generation model.Allowed values:<br>- `gpt-image-2`: GPT Image 2<br>- `gpt-image-2.6`: GPT Image 2.6<br>- `nano-banana-2.1`: Nano Banana 2.1<br>- `seedream-5.0`: Seedream 5.0<br>- `gpt-4o-image`: GPT-4o-image |
| data.list.data.num_result | integer | Number of results to generate. |
| data.list.data.output_format | string | Output format.Allowed values:<br>- `PNG`<br>- `JPEG`<br>- `WEBP` |
| data.list.data.reference_images | array | Reference images, as objects. |
| data.list.data.reference_images.object_id | string | Reference image object_id. |
| data.list.data.aspect_ratio | string | Aspect ratio. |
| data.list.data.resolution | string | Resolution. |
| data.list.data.language | string | Language. |
| data.list.data.video_theme | string | Video topic. |
| data.list.data.script_prompt | string | Script prompt generated during analysis. Populated as the task runs. |
| data.list.tasks | array | List of subtasks as objects. |
| data.list.tasks.task_id | string | Subtask ID. |
| data.list.tasks.state | integer | Subtask status.Allowed values:<br>- `1`: Generating<br>- `2`: Failed<br>- `3`: Succeeded |
| data.list.tasks.data | array | Output files, as objects. |
| data.list.tasks.data.file_id | string | File ID. |
| data.list.tasks.data.file_url | string | File URL. |

#### Background removal (task_type=`background_remove`)

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| data.list.background_removal_data | object | Background removal task parameters. |
| data.list.background_removal_data.model | string | Model.Allowed values:<br>- `rmbg-v2.0`: RMBG V2.0<br>- `pixnet-v2.0`: Pixnet V2.0 |
| data.list.background_removal_data.input_image_ids | array | List of input image IDs as strings. |
| data.list.background_removal_data.output_format | string | Output format. |
| data.list.tasks | array | List of subtasks as objects. |
| data.list.tasks.state | integer | Subtask status.Allowed values:<br>- `1`: Generating<br>- `2`: Failed<br>- `3`: Succeeded |
| data.list.tasks.title | string | Title. May be empty. |
| data.list.tasks.reasons | array | Failure reasons as strings. |
| data.list.tasks.data | array | Output files, as objects. |
| data.list.tasks.data.file_id | string | File ID. |
| data.list.tasks.data.file_url | string | File URL. |

#### Image upscaling (task_type=`image_upscale`)

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| data.list.input_image_ids | array | Input image IDs as strings. |
| data.list.output_format | string | Output format.Allowed values:<br>- `PNG`<br>- `WEBP`<br>- `JPG` |
| data.list.upscale_model | string | Upscaling model.Allowed values:<br>- `swinir`: SwinIR |
| data.list.tasks | array | List of subtasks as objects. |
| data.list.tasks.state | integer | Subtask status.Allowed values:<br>- `1`: Generating<br>- `2`: Failed<br>- `3`: Succeeded |
| data.list.tasks.title | string | Title. May be empty. |
| data.list.tasks.reasons | array | Failure reasons as strings. |
| data.list.tasks.data | array | Output files, as objects. |
| data.list.tasks.data.file_id | string | File ID. |
| data.list.tasks.data.file_url | string | File URL. |

#### Image-to-SVG conversion (task_type=`image_to_svg`)

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| data.list.data | object | Image-to-SVG task parameters. |
| data.list.data.task_name | string | Task name. |
| data.list.data.images | array | Input images as objects. |
| data.list.data.images.object_id | string | Image object_id. |
| data.list.tasks | array | List of subtasks as objects. |
| data.list.tasks.task_id | string | Subtask ID. |
| data.list.tasks.state | integer | Subtask status.Allowed values:<br>- `1`: Generating<br>- `2`: Failed<br>- `3`: Succeeded |
| data.list.tasks.data | array | Output files, as objects. |
| data.list.tasks.data.file_id | string | File ID. |
| data.list.tasks.data.file_url | string | File URL. |

#### Text-to-speech generation (task_type=`text_to_speech`)

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| data.list.text_to_speech_data | object | Text-to-speech task parameters. |
| data.list.text_to_speech_data.model | string | Text-to-speech model.Allowed values:<br>- `speech-2.8-basic`: MiniMax Speech 2.8 Basic（Standard audio quality）<br>- `speech-2.8-hd`: MiniMax Speech 2.8 HD（High-fidelity audio） |
| data.list.text_to_speech_data.name | string | Voiceover name. |
| data.list.text_to_speech_data.text | array | List of scripts as strings. |
| data.list.text_to_speech_data.voice_ids | array | List of voice IDs as strings. |
| data.list.text_to_speech_data.language | string | Text-to-speech language code. |
| data.list.text_to_speech_data.speech_rate | number | Speaking rate. |
| data.list.text_to_speech_data.speech_volume | number | Volume. |
| data.list.text_to_speech_data.style | string | Emotional style. |
| data.list.text_to_speech_data.output_format | string | Export audio format.Allowed values:<br>- `MP3`<br>- `FLAC`<br>- `WAV` |
| data.list.tasks | array | List of subtasks as objects. |
| data.list.tasks.state | integer | Subtask status.Allowed values:<br>- `1`: Generating<br>- `2`: Failed<br>- `3`: Succeeded |
| data.list.tasks.title | string | Title。 |
| data.list.tasks.reasons | array | Failure reasons as strings. |
| data.list.tasks.data | array | Output files, as objects. |
| data.list.tasks.data.file_id | string | File ID. |
| data.list.tasks.data.file_url | string | File URL. |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "list": [
            {
                "group_id": "xxxxxx",
                "state": 4,
                "create_time": 1710000000000,
                "data": {
                    "task_name": "xxxxxx",
                    "images": [
                        {
                            "object_id": "xxxxxx"
                        }
                    ]
                },
                "tasks": [
                    {
                        "task_id": "xxxxxx",
                        "state": 3,
                        "data": [
                            {
                                "file_id": "xxxxxx",
                                "file_url": "https://xxxxxx"
                            }
                        ]
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
