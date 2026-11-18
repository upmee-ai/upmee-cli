# List Knowledge Bases

### Request URL

`https://www.upmee.cc/open_api/ai/knowledge_base/list`

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
| page | Required | integer | Page number, starting at 1. |
| page_size | Required | integer | Items per page, from 1 to 50. |

### Request Example

```json
{
    "team_id": "xxxxxx",
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
| data.list | array | List of knowledge base summaries as objects. The question and answer text is excluded. |
| data.list.status | string | Knowledge base status.Allowed values:<br>- `ACTIVE`: Enabled<br>- `INACTIVE`: Disabled |
| data.list.knowledge_base_id | string | Knowledge base ID。 |
| data.list.name | string | Knowledge base name. |
| data.list.pause_reason | string | Reason for disabling or pausing. May be empty. |
| data.list.create_time | integer | Creation time in milliseconds. |
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
                "status": "ACTIVE",
                "knowledge_base_id": "xxxxxx",
                "name": "xxxxxx",
                "create_time": 1710000000000
            }
        ],
        "page": 1,
        "page_size": 20,
        "total_size": 1,
        "total_page": 1
    }
}
```
