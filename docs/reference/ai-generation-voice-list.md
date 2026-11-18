# List Voices

### Request URL

`https://www.upmee.cc/open_api/ai/generation/voice/list`

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
| scope | Optional | string | Voice scope. Defaults to `RECOMMEND`.Allowed values:<br>- `RECOMMEND`: System-recommended voices<br>- `FAVORITE`: Favorite voices<br>- `SELF`: Voices cloned by the team |
| keyword | Optional | string | Search by name. Maximum of 50 characters. |
| language | Optional | string | Filter by language. |
| gender | Optional | integer | Gender filter.Allowed values:<br>- `1`: Female<br>- `2`: Male<br>- `3`: Other<br>Other values apply no filter. |
| order | Optional | object | Sort。 |
| order.by | Optional | string | Sort field. Use `create_time` or default to `id`. |
| order.desc | Optional | boolean | Whether to sort in descending order. |
| page | Required | integer | Page number, starting at 1. |
| page_size | Required | integer | Items per page, from 1 to 50. |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "scope": "RECOMMEND",
    "language": "zh",
    "page": 1,
    "page_size": 20
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
| data.list | array | List of voices as objects. |
| data.list.favorite | boolean | Whether the current user marked the voice as a favorite. |
| data.list.voice_id | string | Voice ID. Pass it in `voice_ids` when creating a text-to-speech task. |
| data.list.status | string | Voice status.Allowed values:<br>- `ACTIVE`: Available<br>- `INACTIVE`: Unavailable |
| data.list.name | string | Voice name. |
| data.list.description | string | Voice description. |
| data.list.gender | string | Gender.Allowed values:<br>- `female`: Female<br>- `male`: Male<br>- `other`: Other |
| data.list.preload_url | string | Audio preview URL. |
| data.list.locale | string | Region or dialect identifier. |
| data.list.language | string | Language code. |
| data.list.styles | array | Available emotional styles as strings. |
| data.page | integer | Current page。 |
| data.page_size | integer | Items per page。 |
| data.total_size | integer | Total items。 |
| data.total_page | integer | Total pages。 |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "list": [
            {
                "favorite": false,
                "voice_id": "xxxxxx",
                "status": "ACTIVE",
                "name": "xxxxxx",
                "description": "xxxxxx",
                "gender": "female",
                "preload_url": "https://xxxxxx",
                "locale": "zh-CN",
                "language": "zh",
                "styles": [
                    "calm"
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
