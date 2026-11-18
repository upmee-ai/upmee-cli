# Create a Text-to-Speech Task

### Request URL

`https://www.upmee.cc/open_api/ai/generation/task/create/text_to_speech`

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
| text_to_speech_data | Required | object | Parameters for creating a text-to-speech task. |
| text_to_speech_data.model | Optional | string | Text-to-speech model. If empty, defaults to `speech-2.8-basic`.Allowed values:<br>- `speech-2.8-basic`: MiniMax Speech 2.8 Basic（Standard audio quality）<br>- `speech-2.8-hd`: MiniMax Speech 2.8 HD（High-fidelity audio） |
| text_to_speech_data.name | Required | string | Voiceover name. |
| text_to_speech_data.text | Required | array | List of scripts as strings. Each script must be nonempty and at most 10,000 characters. |
| text_to_speech_data.voice_ids | Required | array | List of voice IDs as strings. Each voice must be available and match the selected model’s platform. |
| text_to_speech_data.language | Optional | string | Text-to-speech language code. |
| text_to_speech_data.speech_rate | Required | number | Speaking rate, from 0.5 to 2. |
| text_to_speech_data.speech_volume | Required | number | Volume, from 0 to 10. |
| text_to_speech_data.style | Optional | string | Emotional style.Allowed values:<br>- `happy`: Happy<br>- `sad`: Sad<br>- `angry`: Angry<br>- `fearful`: Fearful<br>- `disgusted`: Disgusted<br>- `surprised`: Surprised<br>- `calm`: Calm<br>- Empty string: Unspecified |
| text_to_speech_data.output_format | Required | string | Export audio format.<br>Allowed values for `speech-2.8-basic` and `speech-2.8-hd`: `MP3`, `FLAC`, and `WAV`. |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "text_to_speech_data": {
        "model": "speech-2.8-basic",
        "name": "xxxxxx",
        "text": [
            "xxxxxx"
        ],
        "voice_ids": [
            "xxxxxx"
        ],
        "language": "zh",
        "speech_rate": 1,
        "speech_volume": 1,
        "output_format": "MP3"
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
