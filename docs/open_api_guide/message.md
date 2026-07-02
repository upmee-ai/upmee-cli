# Direct Message API

> All DM endpoints are rate-limited. Conversation list and message list: 20 requests/account/min. Message badge: 120 requests/min.

---

## List Conversations {#list-conversations}

**Path** `POST /open_api/instant_messages/conversation/list`
**Auth** `API-Key: {your_key}`
**team_id** Required
**Rate limit** 20 requests/account/min

### Request Parameters

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| team_id | number | ✅ | Team ID |
| media_id | number | ✅ | Account ID — single account only |
| cursor | string | - | Pagination cursor — empty on first call, use `cursor` from previous response |
| count | number | - | Items per page, default 20, max 50 |

### Response

| Field | Type | Description |
| :--- | :--- | :--- |
| has_more | boolean | Whether more data exists |
| cursor | string | Next page cursor — use when `has_more=true` |
| conversations | object[] | Conversation list |
| > conversation_id | number | Conversation ID — used for listing messages and sending messages |
| > media_id | string | Account ID this conversation belongs to |
| > user_name | string | Other party's username |
| > avatar | string | Other party's avatar URL |
| > last_message | string | Last message content |
| > last_message_type | number | Last message type: `1` text / `2` other / `3` video / `4` audio / `5` image / `6` file / `7` emoji / `8` retracted / `9` shared post |
| > last_active_time | number | Last active time (Unix ms) |
| > badge | number | Unread message count |
| > favorite | boolean | Whether starred |
| > remark | string | Notes |
| > tags | object[] | Tag list |
| > > tag_id | number | Tag ID |
| > > tag | string | Tag name |

---

## List Messages {#list-messages}

**Path** `POST /open_api/instant_messages/message/list`
**Auth** `API-Key: {your_key}`
**team_id** Required
**Rate limit** 20 requests/conversation/min

### Request Parameters

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| team_id | number | ✅ | Team ID |
| conversation_id | number | ✅ | Conversation ID |
| cursor | string | - | Pagination cursor, empty on first call |
| count | number | - | Items per page, default 20, max 50 |
| translate | boolean | - | Translate message content, default `false` |
| start_time | number | - | Query start time (Unix ms) |
| end_time | number | - | Query end time (Unix ms) |

### Response

| Field | Type | Description |
| :--- | :--- | :--- |
| has_more | boolean | Whether more data exists |
| cursor | string | Next page cursor |
| private_messages | object[] | Message list, sorted by time ascending |
| > message_id | number | Message ID |
| > message_type | number | Message type: `1` text / `2` other / `3` video / `4` audio / `5` image / `6` file / `7` emoji / `8` retracted / `9` shared post |
| > send_type | number | Send method: `0` normal reply / `1` bulk send / `2` auto-reply |
| > self | boolean | Whether sent by account owner (`true` = sent by owner, `false` = received) |
| > status | number | Message status: `1` sending / `2` delivered / `3` failed / `4` unknown |
| > message | string | Message text |
| > translated_message | string | Translated text (returned when `translate=true`) |
| > updated_time | number | Message time (Unix ms) |
| > lang | string | Message language code |
| > attachments | object[] | Attachment list (returned for image messages) |
| > > mime_type | string | Attachment MIME type |
| > > url | string | Attachment URL |
| > share_post | object | Shared post info (returned for shared post type) |
| > > post_id | string | Post ID |
| > > embed_url | string | Post embed URL |

---

## Send Message {#send-message}

**Path** `POST /open_api/instant_messages/message/send`
**Auth** `API-Key: {your_key}`
**team_id** Required

### Request Parameters

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| team_id | number | ✅ | Team ID |
| conversation_id | number | ✅ | Conversation ID |
| message_type | number | ✅ | Message type: `1` text / `5` image |
| text | string | - | Text content — required when `message_type=1` |
| attachment | object | - | Image attachment — used when `message_type=5` |
| > image_id | string | - | Image file ID (object_id from the upload endpoint) |

### Response

| Field | Type | Description |
| :--- | :--- | :--- |
| message_id | number | Sent message ID |
| sent_at | number | Send time (Unix ms) |

---

## Message Badge {#message-badge}

**Path** `POST /open_api/instant_messages/media/badge`
**Auth** `API-Key: {your_key}`
**team_id** Required
**Rate limit** 120 requests/min

> Check whether accounts have unread messages — useful for batch status checks across multiple accounts.

### Request Parameters

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| team_id | number | ✅ | Team ID |
| media_ids | number[] | - | Account IDs to query — omit to query all accounts in the team |

### Response

| Field | Type | Description |
| :--- | :--- | :--- |
| media_badge | object | Unread status map — key is account ID as string (e.g. `"12345"`), value is boolean (has unread messages) |