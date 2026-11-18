# Create a Direct Message Auto-Reply Rule

### Request URL

`https://www.upmee.cc/open_api/private_message/auto-reply/strategy/create`

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
| name | Required | string | Rule name. Must not be empty and must be at most 50 characters. |
| enabled | Optional | boolean | Whether to enable the rule. Defaults to `false`. |
| media_ids | Optional | array | List of linked media account IDs as strings. An account can be linked to at most one direct message auto-reply rule. |
| knowledge_base_id | Required | string | Linked knowledge base ID. The knowledge base must exist and be `ACTIVE`. |
| delay | Required | integer | Reply delay in seconds, from 0 to 1800 seconds (30 minutes). |
| language_rule | Required | integer | Reply language rule.Allowed values:<br>- `1`: Reply in a fixed language<br>- `2`: Translate automatically based on the user's language |
| regular_language | Required | string | Default or fixed reply language code. Must not be empty. |
| prompt_text | Optional | string | Additional prompt. Maximum of 200 characters. |
| terminate_reply_enabled | Optional | boolean | Whether to stop replies automatically. Defaults to `false`. |
| terminate_reply_scene | Optional | string | Description of when to stop replying. Maximum of 200 characters. Required when reply stopping is enabled. |
| terminate_reply_mode | Required | integer | How to stop replies.Allowed values:<br>- `1`: Stop replying in this conversation<br>- `2`: Stop automatic replies to this user |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "name": "xxxxxx",
    "enabled": true,
    "media_ids": [
        "xxxxxx"
    ],
    "knowledge_base_id": "xxxxxx",
    "delay": 30,
    "language_rule": 1,
    "regular_language": "zh",
    "prompt_text": "xxxxxx",
    "terminate_reply_enabled": true,
    "terminate_reply_scene": "xxxxxx",
    "terminate_reply_mode": 1
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
| data.strategy_id | string | Rule ID。 |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "strategy_id": "xxxxxx"
    }
}
```
