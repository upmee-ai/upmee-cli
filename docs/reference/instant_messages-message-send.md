# Send a Direct Message

### Request URL

`https://www.upmee.cc/open_api/instant_messages/message/send`

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
| message_type | Required | integer | Message type. Supported values:<br>- `1`: Text<br>- `5`: Image |
| text | Conditionally required | string | Message text. Required when `message_type` is `1`. |
| attachment | Conditionally required | object | Attachment. Contains the following field:<br>- `image_id` `string` Image object ID. Required when `message_type` is `5`. Upload the image through `/open_api/tool/s3/upload/v2/single` with `type` set to `image`. |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "conversation_id": 0,
    "message_type": 1,
    "text": "xxxxxx"
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| sent_at | integer | Time the message was sent, in milliseconds |
| message_id | integer | Message ID |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "sent_at": 1761545453099,
        "message_id": 0
    }
}
```
