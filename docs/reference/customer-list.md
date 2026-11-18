# List Customers

### Request URL

`https://www.upmee.cc/open_api/customer/list`

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
| page | Required | integer | Page number, starting at `1`。 |
| page_size | Required | integer | Items per page, from `1` to `50`. |
| statuses | Optional | array | Select multiple lead statuses. Elements are numbers. If empty or omitted, no status filter is applied. Allowed values:<br>- `1`: Awaiting follow-up<br>- `2`: Follow-up in progress<br>- `3`: Converted<br>- `4`: Invalid |
| user_ids | Optional | array | Filter by multiple assignee UID values. Elements are strings.<br>If empty or omitted, administrators can query without filtering by assignee. Other users can only query customers assigned to them. |
| tag_ids | Optional | array | Select multiple tag IDs. Elements are strings. Matches any provided tag. If empty or omitted, no tag filter is applied. |
| priorities | Optional | array | Select multiple priorities. Elements are numbers. If empty or omitted, no priority filter is applied. Allowed values:<br>- `1`: High<br>- `2`: Medium<br>- `3`: Low |
| has_unread | Optional | boolean | Whether there are unread messages。 |
| search_key | Optional | string | Fuzzy search by customer name. Ignored if empty after trimming leading and trailing whitespace. |
| sort_by | Optional | number | Sort order. Invalid values use the default. Allowed values:<br>- `0`: Default<br>- `1`: Acquisition time, ascending<br>- `2`: Acquisition time, descending<br>- `3`: Follow-up duration, ascending<br>- `4`: Follow-up duration, descending |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "page": 1,
    "page_size": 20,
    "statuses": [
        1,
        2
    ],
    "user_ids": [
        "xxxxxx"
    ],
    "tag_ids": [
        "xxxxxx"
    ],
    "priorities": [
        1,
        2
    ],
    "has_unread": true,
    "search_key": "xxxxxx",
    "sort_by": 2
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
| data.list | array | List of customers. Elements are objects. |
| data.list.customer_id | string | Customer ID. |
| data.list.customer_name | string | Customer name. |
| data.list.avatar | string | Customer avatar CDN URL. Returns an empty string if there is no avatar. |
| data.list.status | number | Lead status. Allowed values:<br>- `1`: Awaiting follow-up<br>- `2`: Follow-up in progress<br>- `3`: Converted<br>- `4`: Invalid |
| data.list.priority | number | Priority. Allowed values:<br>- `1`: High<br>- `2`: Medium<br>- `3`: Low |
| data.list.remark | string | Note。 |
| data.list.has_unread_message | number | Whether there are unread messages。Allowed values:<br>- `0`: No<br>- `1`: Yes |
| data.list.tags | array | List of tags. Elements are objects. Returns an empty array when there are no tags. |
| data.list.tags.tag_id | string | Tag ID。 |
| data.list.tags.tag_name | string | Tag name。 |
| data.list.user | object | Assignee information. May be omitted if there is no assignee or the user does not exist. |
| data.list.user.uid | string | Assignee UID. |
| data.list.user.name | string | Assignee name. |
| data.list.user.avatar | string | Assignee avatar. |
| data.list.fields | array | Custom field values. Elements are objects. The list includes every custom field defined for the team. `field_content` is empty for fields without a value. |
| data.list.fields.field_id | string | Field ID. |
| data.list.fields.field_name | string | Field name. |
| data.list.fields.field_content | string | Field value. |
| data.list.contacts | array | List of contact methods. Elements are objects. Returns an empty array when none are available. |
| data.list.contacts.contact_id | string | Contact entry ID. |
| data.list.contacts.contact_type | number | Contact method type. Allowed values:<br>- `1`: Mobile phone number<br>- `2`: Email address<br>- `3`: WhatsApp<br>- `4`: Facebook<br>- `5`: Instagram<br>- `6`: TikTok<br>- `7`: LinkedIn |
| data.list.contacts.add_type | number | Method used to add the contact. Allowed values:<br>- `1`: Text<br>- `2`: Linked conversation |
| data.list.contacts.content | string | Text content. May be empty for a linked conversation. |
| data.list.contacts.media_id | string | Linked media account ID. May be omitted if no account is linked. |
| data.list.contacts.media_type | number | Linked media type. May be omitted if no account is linked. |
| data.list.contacts.conversation_id | string | Linked direct message conversation ID. May be omitted if there is no conversation. |
| data.list.contacts.media_name | string | Display name of the media account in the linked conversation. |
| data.list.contacts.media_avatar | string | Avatar of the media account in the linked conversation. |
| data.list.contacts.user_name | string | Display name of the other participant in the direct message conversation. Empty if there is no conversation. |
| data.list.contacts.user_avatar | string | Avatar of the other participant in the direct message conversation. Empty if there is no conversation. |
| data.list.contacts.has_unread | boolean | Whether the linked direct message conversation has unread messages. Returns `false` if there is no conversation. |
| data.list.contacts.last_active_time | integer | Last activity timestamp of the linked direct message conversation, in milliseconds. May be omitted if the conversation or timestamp is unavailable. |
| data.page_info | object | Pagination information。 |
| data.page_info.page | integer | Current page number。 |
| data.page_info.page_size | integer | Items per page。 |
| data.page_info.total_size | integer | Total items。 |
| data.page_info.total_page | integer | Total pages。 |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "list": [
            {
                "customer_id": "xxxxxx",
                "customer_name": "xxxxxx",
                "avatar": "https://xxxxxx",
                "status": 2,
                "priority": 1,
                "remark": "xxxxxx",
                "has_unread_message": 1,
                "tags": [
                    {
                        "tag_id": "xxxxxx",
                        "tag_name": "xxxxxx"
                    }
                ],
                "user": {
                    "uid": "xxxxxx",
                    "name": "xxxxxx",
                    "avatar": "https://xxxxxx"
                },
                "fields": [
                    {
                        "field_id": "xxxxxx",
                        "field_name": "xxxxxx",
                        "field_content": "xxxxxx"
                    }
                ],
                "contacts": [
                    {
                        "contact_id": "xxxxxx",
                        "contact_type": 1,
                        "add_type": 1,
                        "content": "xxxxxx",
                        "has_unread": false
                    },
                    {
                        "contact_id": "xxxxxx",
                        "contact_type": 6,
                        "add_type": 2,
                        "media_id": "xxxxxx",
                        "media_type": 8,
                        "conversation_id": "xxxxxx",
                        "media_name": "xxxxxx",
                        "media_avatar": "https://xxxxxx",
                        "user_name": "xxxxxx",
                        "user_avatar": "https://xxxxxx",
                        "has_unread": true,
                        "last_active_time": 1710000000000
                    }
                ]
            }
        ],
        "page_info": {
            "page": 1,
            "page_size": 20,
            "total_size": 1,
            "total_page": 1
        }
    }
}
```
