# List Messages in a Conversation

When retrieving messages in a single conversation, the **request rate (QPM) must not exceed 20 per conversation\_id**. The rate limit applies separately to each conversation\_id. If your page polls for conversation updates, follow these guidelines:

1. Set the polling interval to **at least 20 seconds**.

2. Stop polling when the user has been **inactive for more than 5 minutes** to avoid unnecessary requests and resource use.

### Request URL

`https://www.upmee.cc/open_api/instant_messages/message/list`

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
| team_id | Required | string | Team ID |
| conversation_id | Required | integer | Conversation ID |
| cursor | Optional | string | For pagination, pass the cursor from the previous response: `cursor` |
| count | Required | integer | Items per page. Maximum: `50` |
| start_time | Optional | integer | Start of the message time range, as a timestamp in milliseconds. Returns only messages sent after this value. |
| end_time | Optional | integer | End of the message time range, as a timestamp in milliseconds. Returns messages sent at or before this value. |
| with_operator | Optional | bool | Whether to return the team member who replied (operator). Defaults to false. Set to true to identify which member sent the reply from the dashboard. |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "conversation_id": 0,
    "cursor": "",
    "count": 20,
    "start_time": 1761458588597,
    "end_time": 1761458588599
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| self | bool | Whether the current social account sent the message |
| message_type | integer | Message type. Supported values:<br>- `1`: Text<br>- `5`: Image<br>- `8`: Unsent message<br>- `9`: Shared post |
| send_type | integer | Message delivery type. Supported values:<br>- `0`: Default delivery<br>- `1`: Bulk delivery<br>- `2`: Automatic delivery |
| updated_time | integer | Message send timestamp in milliseconds |
| message_id | integer | Message ID |
| message | string | Message content. Returned only when `message_type` is `1`. |
| share_post | object[] | Shared post information. Returned only when `message_type` is `9`. Contains the following fields:<br>- `embed_url` `string` Embed URL |
| attachments | object[] | Attachment information. Returned when `message_type` is `5`. Contains the following fields:<br>- `url` `string` Attachment URL |
| operator | object | UPMee operator. Present only when the request sets `with_operator=true`. |
| operator.uid | string | UPMee user UID |
| operator.name | string | UPMee user display name |
| operator.avatar | string | UPMee user avatar URL |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "private_messages": [
            {
                "self": false,
                "message_type": 1,
                "send_type": 0,
                "updated_time": 1761458588598,
                "message_id": 0,
                "message": "Sure thing, we can chat a bit more."
            }
        ],
        "has_more": false
    }
}
```
