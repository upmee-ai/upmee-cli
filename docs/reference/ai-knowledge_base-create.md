# Create a Knowledge Base

### Request URL

`https://www.upmee.cc/open_api/ai/knowledge_base/create`

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
| name | Optional | string | Knowledge base name. Maximum of 50 characters. |
| data | Optional | array | List of questions and answers as objects. Up to 20 entries. |
| data.question | Optional | string | Question. Maximum of 300 characters. |
| data.answers | Optional | array | List of answers as objects. Up to 1 entry. |
| data.answers.content_type | Required | integer | Answer type.Allowed values:<br>- `1`: Text |
| data.answers.content | Optional | string | Answer content. Maximum of 500 characters for text answers. |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "name": "xxxxxx",
    "data": [
        {
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
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| code | integer | Application status code. `0` indicates success. |
| message | string | Response message. `OK` indicates success. |
| request_id | string | Request trace ID. |
| data | object | Response data。 |
| data.knowledge_base_id | string | Knowledge base ID。 |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "knowledge_base_id": "xxxxxx"
    }
}
```
