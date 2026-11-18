# Delete a Comment Auto-Delete Rule

### Request URL

`https://www.upmee.cc/open_api/comment/delete/strategy/delete`

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

### Request Example

```json
{
    "team_id": "xxxxxx",
    "strategy_id": "xxxxxx"
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
