# Comment Management API

---

## List Comments {#list-comments}

**Path** `POST /open_api/media/item/comment/list`
**Auth** `API-Key: {your_key}`
**team_id** Required

> Returns top-level comments for the specified content item, sorted by publish time descending.

### Request Parameters

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| team_id | number | ✅ | Team ID |
| item_id | string | ✅ | Content ID (the platform-side video/post ID) |
| cursor | string | - | Pagination cursor — empty on first call, use `page_info.cursor` from the previous response |
| count | number | - | Items per page, default 20, max 50 |

### Response

| Field | Type | Description |
| :--- | :--- | :--- |
| list | object[] | Comment list |
| > comment_id | string | Comment ID |
| > item_id | string | Content ID this comment belongs to |
| > media_id | number | Account ID |
| > media_type | string | Platform type |
| > comment_user_id | string | Commenter's platform user ID |
| > comment_user_name | string | Commenter's username |
| > comment_user_avatar | string | Commenter's avatar URL |
| > comment_by_author | boolean | Whether this comment was posted by the account owner |
| > content | string | Comment text |
| > digg_count | number | Like count |
| > reply_comment_total | number | Reply count |
| > comment_time | number | Comment time (Unix ms) |
| > reply_to_comment_id | string | Parent comment ID (empty = top-level comment) |
| > top | boolean | Whether pinned |
| page_info | object | Pagination info |
| > cursor | string | Next page cursor — empty means no more data |
| > has_more | boolean | Whether more data exists |

---

## List Comment Replies {#list-comment-replies}

**Path** `POST /open_api/media/item/comment/reply/list`
**Auth** `API-Key: {your_key}`
**team_id** Required

> Returns the sub-replies for a specific comment.

### Request Parameters

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| team_id | number | ✅ | Team ID |
| item_id | string | ✅ | Content ID |
| comment_id | string | ✅ | Parent comment ID |
| cursor | string | - | Pagination cursor, empty on first call |
| count | number | - | Items per page, default 20, max 50 |

### Response

| Field | Type | Description |
| :--- | :--- | :--- |
| list | object[] | Reply list — same field structure as the comment list |
| page_info | object | Pagination info |
| > cursor | string | Next page cursor |
| > has_more | boolean | Whether more data exists |

---

## Reply to Comment {#reply-to-comment}

**Path** `POST /open_api/media/item/comment/reply`
**Auth** `API-Key: {your_key}`
**team_id** Required

### Request Parameters

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| team_id | number | ✅ | Team ID |
| item_id | string | ✅ | Content ID |
| comment_id | string | ✅ | ID of the comment to reply to |
| content | string | ✅ | Reply text |

### Response

| Field | Type | Description |
| :--- | :--- | :--- |
| comment_id | string | ID of the newly created reply |

---

## Delete Comment {#delete-comment}

**Path** `POST /open_api/media/item/comment/del`
**Auth** `API-Key: {your_key}`
**team_id** Required

> Supported platforms: Facebook Page, Instagram, YouTube, Threads, VK, TikTok, LinkedIn. Other platforms do not support comment deletion.

### Request Parameters

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| team_id | number | ✅ | Team ID |
| item_id | string | ✅ | Content ID |
| comment_id | string | ✅ | ID of the comment to delete |

### Response

No extra data — `code=0` means success. Deletion is asynchronous; re-query the comment list to confirm the result.