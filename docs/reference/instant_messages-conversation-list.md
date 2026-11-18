# List Direct Message Conversations

When retrieving conversations for a single social account, the **request rate (QPM) must not exceed 20 per media\_id**. The rate limit applies separately to each media\_id. If your page polls for conversation updates, follow these guidelines:

1. Set the polling interval to **at least 20 seconds**.

2. Stop polling when the user has been **inactive for more than 5 minutes** to avoid unnecessary requests and resource use.

### Request URL

`https://www.upmee.cc/open_api/instant_messages/conversation/list`

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
| media_id | Required | string | Social account ID |
| cursor | Optional | string | For pagination, pass the cursor from the previous response: `cursor` |
| count | Required | integer | Items per page. Maximum: `50` |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "media_id": "xxxxxx",
    "cursor": "",
    "count": 4
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| has_more | bool | Whether more results are available |
| cursor | string | Cursor for the next page |
| conversations | PrivateConversation[] | Conversation list |
| conversations.favorite | bool | Whether the conversation is starred |
| conversations.last_message_type | integer | Message type. Supported values:<br>- `1`: Text<br>- `2`: Other<br>- `3`: Video<br>- `4`: Audio<br>- `5`: Image<br>- `6`: File<br>- `7`: Sticker or emoji<br>- `8`: Unsent message<br>- `9`: Shared post |
| conversations.last_active_time | integer | Time the last message was updated, in milliseconds |
| conversations.conversation_id | integer | Conversation ID |
| conversations.badge | integer | Unread message count |
| conversations.media_id | string | Social account ID |
| conversations.user_name | string | Username |
| conversations.avatar | string | Avatar URL |
| conversations.last_message | string | Contents of the last message |
| conversations.remark | string | Note |
| conversations.tags | object[] | Tag information. Contains the following fields:<br>- `tag_id` `integer` Tag ID<br>- `tag` `string` Tag name |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "has_more": true,
        "cursor": "xxxxxx",
        "conversations": [
            {
                "last_message_type": 1,
                "last_active_time": 1761451767292,
                "conversation_id": 0,
                "badge": 0,
                "media_id": "xxxxxx",
                "user_name": "xxxxxx",
                "avatar": "https://xxxxxx",
                "last_message": "xxxxxx"
            }
        ]
    }
}
```
