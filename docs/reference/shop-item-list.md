# List Account Videos (Shop)

### Request URL

`https://www.upmee.cc/open_api/shop/item/list`

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
| page_size | Required | int | Items per page, up to `50` |
| team_ids | Optional | string[] | Filter by team ID |
| media_ids | Optional | string[] | Filter by account ID |
| media_types | Optional | int[] | Account type. Allowed values:<br>- `21`: TikTok Shop Creator<br>- `22`: TikTok Shop store |
| task_ids | Optional | string[] | Filter by task ID |
| item_ids | Optional | string[] | Filter by post ID |
| uids | Optional | string[] | Filter by publisher UID |
| privacy_state | Optional | int | Visibility. Allowed values:<br>- `1`: Public<br>- `2`: Unlisted<br>- `3`: Private |
| query | Optional | string | Keyword search |
| pub_time_filter | Optional | int | Preset publication time filter. Allowed values:<br>- `-1`: No limit<br>- `7`: Last 7 days<br>- `30`: Last 30 days<br>- `60`: Last 60 days<br>- `90`: Last 90 days<br>- `365`: Last 365 days<br>Default: If omitted or set to `0`, uses `-1`. If both `pub_start_time` and `pub_end_time` are provided, the custom range takes precedence. |
| pub_start_time | Optional | int64 | Start of the publication time range, in milliseconds. Provide it together with `pub_end_time`. If both `pub_start_time` and `pub_end_time` are provided, the custom range takes precedence. |
| pub_end_time | Optional | int64 | End of the publication time range, in milliseconds. Provide it together with `pub_start_time`. If both `pub_start_time` and `pub_end_time` are provided, the custom range takes precedence. |
| pub_video_filter | Optional | int | Publisher scope. Allowed values:<br>- `1`: All<br>- `2`: Team<br>- `3`: Current user<br>Default: If omitted or set to `0`, uses `1`. |
| orders | Optional | object[] | Sort |
| orders.by | Optional | string | Allowed values:<br>- `create_time`: Creation time<br>- `gmv`: GMV |
| orders.desc | Optional | bool | Allowed values:<br>- `true`: Descending<br>- `false`: Ascending<br>Default: `false` |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "media_ids": [
        "xxxxxx"
    ],
    "media_types": [
        21
    ],
    "pub_time_filter": -1,
    "pub_video_filter": 1,
    "business_type": 4,
    "orders": [
        {
            "by": "create_time",
            "desc": true
        }
    ],
    "page": 1,
    "page_size": 20
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
| data.list | object[] | List of Shop videos |
| data.list.item_id | string | Post ID |
| data.list.title | string | Title |
| data.list.desc | string | Description |
| data.list.cover | string | Cover URL |
| data.list.video | string | Video URL |
| data.list.media_id | string | Social account ID |
| data.list.media_type | int | Platform type, such as `21` or `22` |
| data.list.create_time | int64 | Publication timestamp in milliseconds |
| data.list.task_id | string | Associated task ID |
| data.list.team_id | string | Team ID |
| data.list.uid | string | Publisher user ID |
| data.list.gmv | float | Gross merchandise value (GMV) |
| data.list.gmv_currency | string | GMV currency |
| data.list.view | int64 | Views |
| data.list.like | int64 | Number of likes |
| data.list.share | int64 | Shares |
| data.list.comment | int64 | Comments |
| data.list.click | int64 | Product clicks |
| data.list.click_through_rate | float | Click-through rate |
| data.list.sku_orders | int64 | Number of paid SKU orders placed directly |
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
        "list": [],
        "page_info": {
            "page": 0,
            "page_size": 0,
            "total_size": 0,
            "total_page": 0
        }
    }
}
```
