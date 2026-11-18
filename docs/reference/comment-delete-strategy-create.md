# Create a Comment Auto-Delete Rule

### Request URL

`https://www.upmee.cc/open_api/comment/delete/strategy/create`

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
| media_ids | Required | array | List of linked media account IDs as strings. Provide at least one ID. An account can be linked to at most one auto-delete rule. |
| video_range | Required | integer | Video publication time range.Allowed values:<br>- `1`: Last 3 days<br>- `2`: Last 7 days<br>- `3`: Last 30 days |
| max_delete_per_video | Optional | integer | Maximum number of comments to delete per video.Allowed values:<br>- `0`: Unlimited<br>- `1`: 10 comments<br>- `2`: 20 comments<br>- `3`: 50 comments<br>- `4`: 100 comments<br>- `5`: 200 comments |
| match_mode | Required | integer | Match mode.Allowed values:<br>- `1`: All<br>- `2`: Keyword<br>- `3`: Intent<br>- `4`: Intent or keyword (delete if either matches) |
| intent | Optional | string | Intent description. Maximum of 500 characters. Required when `match_mode` is `3` or `4`. |
| keywords | Optional | string | Keywords separated by commas. Both ASCII and full-width Chinese commas are accepted. Maximum total length: 500 characters. Required when `match_mode` is `2` or `4`. |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "name": "xxxxxx",
    "enabled": true,
    "media_ids": [
        "xxxxxx"
    ],
    "video_range": 2,
    "max_delete_per_video": 2,
    "match_mode": 4,
    "intent": "xxxxxx",
    "keywords": "spam,promotion"
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
