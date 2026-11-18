# List Direct Message Auto-Reply Rules

### Request URL

`https://www.upmee.cc/open_api/private_message/auto-reply/strategy/list`

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
| strategy_ids | Optional | array | Filter by rule IDs as strings. If omitted, returns all rules for the team. |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "strategy_ids": [
        "xxxxxx"
    ]
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
| data.strategies | array | List of rules as objects. The remaining quota field is omitted. |
| data.strategies.strategy_id | string | Rule ID。 |
| data.strategies.knowledge_base_id | string | Linked knowledge base ID。 |
| data.strategies.name | string | Rule name。 |
| data.strategies.enabled | boolean | Whether the rule is enabled. |
| data.strategies.delay | integer | Reply delay in seconds. |
| data.strategies.language_rule | integer | Reply language rule.Allowed values:<br>- `1`: Reply in a fixed language<br>- `2`: Translate automatically based on the user's language |
| data.strategies.regular_language | string | Default or fixed reply language code. |
| data.strategies.prompt_text | string | Additional prompt. |
| data.strategies.pause_reason | string | Reason for pausing. May be empty. |
| data.strategies.terminate_reply_enabled | boolean | Whether automatic stopping of replies is enabled.<br> |
| data.strategies.terminate_reply_scene | string | Description of when to stop replying. |
| data.strategies.terminate_reply_mode | integer | How to stop replies.Allowed values:<br>- `1`: Stop replying in this conversation<br>- `2`: Stop automatic replies to this user |
| data.strategies.medias | array | Details of linked accounts as objects. |
| data.strategies.medias.valid | boolean | Whether the account token is valid. |
| data.strategies.medias.media_type | integer | Platform type.Allowed values:<br>- `6`: Instagram<br>- `7`: Facebook Page<br>- `8`: TikTok Biz<br>- `20`: WhatsApp |
| data.strategies.medias.media_id | string | Social account ID。 |
| data.strategies.medias.name | string | Account name. |
| data.strategies.medias.avatar | string | Avatar URL. |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "strategies": [
            {
                "strategy_id": "xxxxxx",
                "knowledge_base_id": "xxxxxx",
                "name": "xxxxxx",
                "enabled": true,
                "delay": 30,
                "language_rule": 1,
                "regular_language": "zh",
                "prompt_text": "xxxxxx",
                "terminate_reply_enabled": true,
                "terminate_reply_scene": "xxxxxx",
                "terminate_reply_mode": 1,
                "medias": [
                    {
                        "valid": true,
                        "media_type": 8,
                        "media_id": "xxxxxx",
                        "name": "xxxxxx",
                        "avatar": "https://xxxxxx"
                    }
                ]
            }
        ]
    }
}
```
