# List Pinterest Boards

### Request URL

`https://www.upmee.cc/open_api/media/task/pinterest/boards/list`

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
| page_size | Required | integer | Page size |
| bookmark | Optional | string | Cursor for retrieving the next page |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "media_id": "xxxxxx",
    "page_size": 1,
    "bookmark": "LT45MjA3NzUxNTUwMDQ5MTY5ODl8MXw2MjMxOTEwNjc4Mjg0NDkyKkdRTCp8ODBjZTZlYjlkOWQ5MDFhMjdjY2RkZjA3YzQ2MDE3OTNlYWRkZThmMGVkZGFkZTQ1YjQwZGRmZWY3NDU2NjQyOHxORVd8"
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| media_id | string | Social account ID |
| bookmark | string | Cursor for retrieving the next page. An empty value indicates there are no more results. |
| boards | BoardInfo[] | List of boards |
| boards.id | string | Board ID |
| boards.name | string | Board name |
| boards.image_cover_url | string | Cover image URL |
| boards.description | string | Description |
| boards.privacy | string | Board privacy setting. Default: `PUBLIC`<br>Allowed values:<br>- `PUBLIC`: Public board.<br>- `PROTECTED`: Protected board.<br>- `SECRET`: Secret board.<br>> Note: When you create an ads-only board by setting is\_ads\_only to true, the privacy setting automatically becomes protected.<br>> <br>> |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "boards": [
            {
                "id": "xxxxxx",
                "name": "xxxxxx",
                "image_cover_url": "https://xxxxxx",
                "description": "",
                "privacy": "PUBLIC"
            },
            {
                "id": "xxxxxx",
                "name": "xxxxxx",
                "image_cover_url": "https://xxxxxx",
                "description": "",
                "privacy": "PUBLIC"
            }
        ],
        "bookmark": "",
        "media_id": "xxxxxx"
    }
}
```
