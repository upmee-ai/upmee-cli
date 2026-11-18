# List Comments

### Request URL

`https://www.upmee.cc/open_api/media/item/comment/list`

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
| team_id | Required | number | Team ID |
| item_id | Required | string | Video ID |
| with_operator | Optional | bool | Whether to return the team member who replied (operator). Defaults to false. Set to true to identify which member sent the reply from the dashboard. |
| cursor | Optional | string | Pagination cursor. Omit it or pass an empty string on the first request. For subsequent requests, use the `cursor` from the previous response. |
| count | Optional | number | Items per page. Defaults to 20, with a maximum of 50.<br>> Default: 20<br>> <br>> |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "item_id": "xxxxxx",
    "count": 1,
    "cursor": ""
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| list | []object | List of comments |
| list.item_id | string | Video ID |
| list.comment_id | string | Comment ID, required to reply to or delete the comment. |
| list.comment_user_id | string | ID of the commenter on the platform |
| list.comment_user_name | string | Commenter name. A placeholder is generated if the platform does not provide one. |
| list.comment_user_avatar | string | Commenter avatar URL |
| list.comment_by_author | bool | Whether the account owner posted the comment |
| list.media_id | number | Account ID |
| list.media_type | string | Platform type.<br>- `youtube`：YouTube<br>- `instagram`：Instagram<br>- `facebook_page`：Facebook Page<br>- `tiktok_business`：TikTok Business<br>- `linked_in`：LinkedIn<br>- `thread`：Threads<br>- `vk`：VK |
| list.reply_to_comment_id | string | ID of the comment being replied to. Empty for top-level comments. |
| list.content | string | Comment text |
| list.digg_count | number | Number of likes |
| list.reply_comment_total | number | Number of replies |
| list.comment_time | number | Comment timestamp in milliseconds |
| list.top | bool | Whether the comment is pinned |
| list.operator | object | Reply author. Returned only when `with_operator=true`, `source=3`, and the user can be found. Otherwise omitted. |
| list.operator.uid | string | UPMee user UID |
| list.operator.name | string | UPMee user display name |
| list.operator.avatar | string | UPMee user avatar URL |
| page_info | object | Pagination information |
| page_info.cursor | string | Cursor for the next page. Pass it in the `cursor` field of the next request. |
| page_info.has_more | bool | Whether more results are available |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "list": [
            {
                "item_id": "xxxxxx",
                "comment_id": "xxxxxx",
                "comment_user_id": "xxxxxx",
                "comment_user_name": "xxxxxx",
                "comment_user_avatar": "https://xxxxxx",
                "comment_by_author": true,
                "media_id": "xxxxxx",
                "media_type": 7,
                "reply_to_comment_id": "",
                "content": "xxxxxx",
                "digg_count": 0,
                "reply_comment_total": 0,
                "comment_time": 1780577591000,
                "top": false
            },
            {
                "item_id": "xxxxxx",
                "comment_id": "xxxxxx",
                "comment_user_id": "xxxxxx",
                "comment_user_name": "xxxxxx",
                "comment_user_avatar": "https://xxxxxx",
                "comment_by_author": true,
                "media_id": "xxxxxx",
                "media_type": 7,
                "reply_to_comment_id": "",
                "content": "xxxxxx",
                "digg_count": 0,
                "reply_comment_total": 0,
                "comment_time": 1780561854000,
                "top": false
            }
        ],
        "page_info": {
            "cursor": "xxxxxx",
            "has_more": false,
            "after": ""
        }
    }
}
```
