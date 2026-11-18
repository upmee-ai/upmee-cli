# List Comment Auto-Reply Rules

### Request URL

`https://www.upmee.cc/open_api/comment/reply/strategy/list`

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
| data.list | array | List of rules as objects. |
| data.list.strategy_id | string | Rule ID。 |
| data.list.media_ids | array | List of linked media account IDs as strings, in the same order as `medias`. |
| data.list.medias | array | Details of linked accounts as objects. |
| data.list.medias.valid | boolean | Whether the current team still has access to this account. |
| data.list.medias.media_id | string | Social account ID。 |
| data.list.medias.media_type | integer | Platform type.Allowed values:<br>- `5`: YouTube<br>- `6`: Instagram<br>- `7`: Facebook Page<br>- `8`: TikTok Biz<br>- `11`: LinkedIn<br>- `15`: Threads<br>- `19`: Bluesky |
| data.list.medias.avatar | string | Avatar URL. |
| data.list.medias.name | string | Account name. |
| data.list.enabled | boolean | Whether the rule is enabled. |
| data.list.video_range | integer | Video publication time range.Allowed values:<br>- `1`: Last 3 days<br>- `2`: Last 7 days<br>- `3`: Last 30 days |
| data.list.single_reply_count_total | integer | Maximum total replies per video.Allowed values:<br>- `1`: 5 comments<br>- `2`: 10 comments<br>- `3`: 20 comments<br>- `4`: 30 comments<br>- `5`: 50 comments |
| data.list.language_rule | integer | Reply language rule.Allowed values:<br>- `1`: Reply in a fixed language<br>- `2`: Translate automatically based on the user's language |
| data.list.delay | integer | Reply delay in seconds. |
| data.list.knowledge_base_id | string | Linked knowledge base ID。 |
| data.list.prompt_text | string | Additional prompt for generating the reply. |
| data.list.regular_language | string | Default or fixed reply language code. |
| data.list.name | string | Rule name。 |
| data.list.pause_reason | string | Reason for pausing. May be empty. |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "list": [
            {
                "strategy_id": "xxxxxx",
                "media_ids": [
                    "xxxxxx"
                ],
                "medias": [
                    {
                        "valid": true,
                        "media_id": "xxxxxx",
                        "media_type": 8,
                        "avatar": "https://xxxxxx",
                        "name": "xxxxxx"
                    }
                ],
                "enabled": true,
                "video_range": 2,
                "single_reply_count_total": 2,
                "language_rule": 1,
                "delay": 30,
                "knowledge_base_id": "xxxxxx",
                "prompt_text": "xxxxxx",
                "regular_language": "zh",
                "name": "xxxxxx"
            }
        ]
    }
}
```
