# List Account Videos (Social Media)

### Request URL

`https://www.upmee.cc/open_api/media/item/list`

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
| page | Required | int | Page number, starting at `1` |
| page_size | Required | int | Items per page, from `1` to `50`. |
| media_ids | Optional | string[] | List of social account IDs |
| pub_time_filter | Optional | int | Preset filter for publication time. If omitted or set to `0`, no time limit applies.<br>- `-1`: No limit<br>- `7`: Last 7 days<br>- `30`: Last 30 days<br>- `60`: Last 60 days<br>- `90`: Last 90 days<br>- `365`: Last 365 days |
| pub_start_time | Optional | int64 | Custom start of the publication time range, as a timestamp in milliseconds. Both `pub_start_time` and `pub_end_time` must be set. If `pub_time_filter` is also set, the custom range takes precedence. |
| pub_end_time | Optional | int64 | Custom end of the publication time range, as a timestamp in milliseconds. Both `pub_start_time` and `pub_end_time` must be set. If `pub_time_filter` is also set, the custom range takes precedence. |
| pub_video_filter | Optional | int | Video scope. Defaults to `1` if omitted.<br>- `1`: All videos<br>- `2`: Published by the team<br>- `3`: Published by the current user |
| item_ids | Optional | string[] | List of post IDs |
| task_ids | Optional | string[] | List of task IDs |
| query | Optional | string | Keyword to search in the title or description |
| privacy_state | Optional | int | Visibility<br>- `1`: Public<br>- `2`: Visible to anyone with the link<br>- `3`: Private |
| order_by | Optional | string | Sort field. Defaults to `create_time` if omitted.<br>- `create_time`: Publication time<br>- `play`: Views<br>- `digg`: Number of likes<br>- `comment`: Comments<br>- `share`: Shares<br>- `download`: Downloads<br>- `forward`: Reposts<br>- `update_time`: Last updated time |
| order_desc | Optional | bool | Whether to sort in descending order. Defaults to `true` when `order_by` is omitted. |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "media_ids": [
        "xxxxxx",
        "xxxxxx"
    ],
    "page": 1,
    "page_size": 20,
    "order_by": "create_time",
    "order_desc": true
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| code | int | Application status code. `0` indicates success. |
| message | string | Status message |
| request_id | string | Unique request ID |
| data | object | Response data |
| data.list | object[] | List of videos |
| data.list.item_id | string | Post ID |
| data.list.title | string | Title |
| data.list.desc | string | Description |
| data.list.cover | string | Cover URL |
| data.list.video | string | Video URL |
| data.list.media_id | string | Social account ID |
| data.list.media_type | int | Platform type. Uses the same values as the request field `media_types`. |
| data.list.create_time | int64 | Publication timestamp in milliseconds |
| data.list.task_id | string | Associated task ID |
| data.list.team_id | string | Team ID |
| data.list.uid | string | Publisher user ID |
| data.list.play | int64 | Views |
| data.list.digg | int64 | Number of likes |
| data.list.comment | int64 | Comments |
| data.list.share | int64 | Shares |
| data.list.download | int64 | Downloads |
| data.list.forward | int64 | Reposts |
| data.list.favorite | int64 | Saves |
| data.list.reach | int64 | Reach |
| data.page_info | object | Pagination information |
| data.page_info.page | int | Current page number |
| data.page_info.page_size | int | Items per page |
| data.page_info.total_size | int | Total items |
| data.page_info.total_page | int | Total pages |

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
                "title": "xxxxxx",
                "desc": "xxxxxx",
                "cover": "https://xxxxxx",
                "video": "xxxxxx",
                "media_id": "xxxxxx",
                "media_type": 8,
                "create_time": 1788158166000,
                "team_id": "xxxxxx",
                "uid": "xxxxxx",
                "ad_operation_status": false,
                "share": 128,
                "comment": 356,
                "digg": 4820,
                "download": 42,
                "play": 128600,
                "forward": 96,
                "favorite": 710,
                "dislike": 18,
                "reach": 98000,
                "total_time_watched": 1543200.5,
                "full_video_watched_rate": 0.186,
                "full_video_watched": 23920,
                "average_time_watched": 12
            },
            {
                "item_id": "xxxxxx",
                "title": "xxxxxx",
                "desc": "xxxxxx",
                "cover": "https://xxxxxx",
                "video": "xxxxxx",
                "media_id": "xxxxxx",
                "media_type": 8,
                "create_time": 1787898966000,
                "team_id": "xxxxxx",
                "uid": "xxxxxx",
                "ad_operation_status": false,
                "share": 64,
                "comment": 188,
                "digg": 2105,
                "download": 19,
                "play": 56200,
                "forward": 41,
                "favorite": 320,
                "dislike": 7,
                "reach": 41000,
                "total_time_watched": 618200,
                "full_video_watched_rate": 0.152,
                "full_video_watched": 8542,
                "average_time_watched": 11
            }
        ],
        "page_info": {
            "page": 1,
            "page_size": 20,
            "total_size": 2,
            "total_page": 1
        }
    }
}
```
