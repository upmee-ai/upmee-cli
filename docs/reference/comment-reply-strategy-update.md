# Update a Comment Auto-Reply Rule

### Request URL

`https://www.upmee.cc/open_api/comment/reply/strategy/update`

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
| strategy_id | Required | string | Rule ID。 |
| name | Required | string | Rule name. Must not be empty and must be at most 50 characters. |
| enabled | Optional | boolean | Whether the rule is enabled. |
| media_ids | Optional | array | Complete list of linked media account IDs as strings. Existing accounts omitted from the list are unlinked. Newly added accounts must not be linked to another auto-reply rule. |
| knowledge_base_id | Required | string | Linked knowledge base ID. The knowledge base must exist and be `ACTIVE`. |
| video_range | Required | integer | Video publication time range.Allowed values:<br>- `1`: Last 3 days<br>- `2`: Last 7 days<br>- `3`: Last 30 days |
| single_reply_count_total | Required | integer | Maximum total replies per video.Allowed values:<br>- `1`: 5 comments<br>- `2`: 10 comments<br>- `3`: 20 comments<br>- `4`: 30 comments<br>- `5`: 50 comments |
| language_rule | Required | integer | Reply language rule.Allowed values:<br>- `1`: Reply in a fixed language<br>- `2`: Translate automatically based on the user's language |
| regular_language | Optional | string | Default or fixed reply language code. |
| delay | Optional | integer | Reply delay in seconds. |
| prompt_text | Optional | string | Additional prompt for generating the reply. |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "strategy_id": "xxxxxx",
    "name": "xxxxxx",
    "enabled": true,
    "media_ids": [
        "xxxxxx"
    ],
    "knowledge_base_id": "xxxxxx",
    "video_range": 2,
    "single_reply_count_total": 2,
    "language_rule": 1,
    "regular_language": "zh",
    "delay": 30,
    "prompt_text": "xxxxxx"
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| code | integer | Application status code. `0` indicates success. |
| message | string | Response message. `OK` indicates success. |
| request_id | string | Request trace ID. |
| data | object | Response data. An empty object on success. |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {}
}
```
