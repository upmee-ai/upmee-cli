# Unlink Media Accounts

### Request URL

`https://www.upmee.cc/open_api/media/delete`

### HTTP Method

`POST`

### Request Headers

<!-- api-fields -->

| Field | Required <!-- api-tag --> | Type | Description |
| --- | --- | --- | --- |
| API-Key | Required | string | API key |
| Content-Type | Required | string | Request content type. The allowed format is `application/json`. |

### Request Parameters

<!-- api-fields -->

| Field | Required <!-- api-tag --> | Type | Description |
| --- | --- | --- | --- |
| team_id | Required | string | Team ID |
| media_ids | Required | string[] | List of media account IDs to unlink |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "media_ids": [
        "xxxxxx"
    ]
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| code | integer | Application status code. `0` indicates success. |
| message | string | Response message. On failure, it describes the reason for the error. |
| request_id | string | Unique request ID for troubleshooting. |
| data | object | Response data. An empty object `{}` is returned on success. |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {}
}
```
