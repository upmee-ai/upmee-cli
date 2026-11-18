# Reply to a Comment

### Request URL

`https://www.upmee.cc/open_api/media/item/comment/reply`

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
| item_id | Required | string | Video ID. Supported platforms:<br>- `youtube`: YouTube<br>- `instagram`: Instagram<br>- `facebook_page`: Facebook Page<br>- `tiktok_business`: TikTok Business<br>- `linked_in`: LinkedIn<br>- `thread`: Threads<br>- `vk`: VK<br>- `bluesky`: Bluesky |
| content | Required | string | Reply text |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "item_id": "xxxxxx",
    "comment_id": "xxxxxx",
    "content": "xxxxxx"
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| comment_id | string | ID of the newly posted reply |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "comment_id": "xxxxxx"
    }
}
```
