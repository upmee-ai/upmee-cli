# Get Knowledge Base Details

### Request URL

`https://www.upmee.cc/open_api/ai/knowledge_base/detail`

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
| knowledge_base_id | Required | string | Knowledge base ID。 |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "knowledge_base_id": "xxxxxx"
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
| data.status | string | Knowledge base status.Allowed values:<br>- `ACTIVE`: Enabled<br>- `INACTIVE`: Disabled |
| data.knowledge_base_id | string | Knowledge base ID。 |
| data.name | string | Knowledge base name. |
| data.data | array | List of questions and answers as objects. |
| data.data.item_id | string | Question-and-answer entry ID. |
| data.data.question | string | Question. |
| data.data.answers | array | List of answers as objects. |
| data.data.answers.content_type | integer | Answer type.Allowed values:<br>- `1`: Text |
| data.data.answers.content | string | Answer content. |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "status": "ACTIVE",
        "knowledge_base_id": "xxxxxx",
        "name": "xxxxxx",
        "data": [
            {
                "item_id": "xxxxxx",
                "question": "xxxxxx",
                "answers": [
                    {
                        "content_type": 1,
                        "content": "xxxxxx"
                    }
                ]
            }
        ]
    }
}
```
