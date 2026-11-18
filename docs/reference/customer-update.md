# Update Customer Information

### Request URL

`https://www.upmee.cc/open_api/customer/update`

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
| customer_id | Required | string | Customer ID. |
| customer_name | Required | string | Customer name.<br>Must be nonempty after trimming leading and trailing whitespace. Maximum length: 255 characters. |
| avatar | Optional | string | Customer avatar file_id.<br>An empty string clears the avatar. |
| user_id | Required | string | Assignee UID. The assignee must be a member of the current team. |
| priority | Required | number | Priority. Allowed values:<br>- `1`: High<br>- `2`: Medium<br>- `3`: Low |
| remark | Optional | string | Note。<br>Pass an empty string to clear the field. |
| status | Required | number | Lead status. Allowed values:<br>- `1`: Awaiting follow-up<br>- `2`: Follow-up in progress<br>- `3`: Converted<br>- `4`: Invalid<br>If the status is unchanged, the status timestamp and follow-up log remain unchanged.<br>Only administrators can switch the status to Awaiting follow-up. Doing so restarts the timer. |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "customer_id": "xxxxxx",
    "customer_name": "xxxxxx",
    "avatar": "xxxxxx",
    "user_id": "xxxxxx",
    "priority": 1,
    "remark": "xxxxxx",
    "status": 2
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
| data.customer_id | string | Customer ID. |

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
