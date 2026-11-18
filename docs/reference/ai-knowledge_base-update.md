# Update a Knowledge Base

### Request URL

`https://www.upmee.cc/open_api/ai/knowledge_base/update`

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
| status | Required | string | Knowledge base status.Allowed values:<br>- `ACTIVE`: Enabled<br>- `INACTIVE`: Disabled |
| name | Optional | string | Knowledge base name. Maximum of 50 characters. |
| data | Optional | array | List of questions and answers as objects. Replaces the entire list by removing omitted existing entries. Up to 20 entries. |
| data.item_id | Optional | string | Question-and-answer entry ID. Omit it or use `0` to create an entry. Provide an existing ID to update it. |
| data.question | Optional | string | Question. Maximum of 300 characters. |
| data.answers | Optional | array | List of answers as objects. Up to 1 entry. |
| data.answers.content_type | Required | integer | Answer type.Allowed values:<br>- `1`: Text |
| data.answers.content | Optional | string | Answer content. Maximum of 500 characters for text answers. |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "knowledge_base_id": "xxxxxx",
    "status": "ACTIVE",
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
