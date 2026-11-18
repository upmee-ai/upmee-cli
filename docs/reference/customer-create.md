# Create a Customer

### Request URL

`https://www.upmee.cc/open_api/customer/create`

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
| customer_name | Required | string | Customer name.<br>Must be nonempty after trimming leading and trailing whitespace. Maximum length: 255 characters. |
| avatar | Optional | string | Customer avatar file_id.<br>An empty value or omission indicates no avatar. |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "customer_name": "xxxxxx",
    "avatar": "xxxxxx"
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| code | integer | Response status code. `0` indicates success. |
| message | string | Response message. `OK` indicates success. |
| request_id | string | Request trace ID. |
| data | object | Response data。 |
| data.customer_id | string | ID of the newly created customer. |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "customer_id": "xxxxxx"
    }
}
```
