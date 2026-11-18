# Query Performance Data (Shop)

### Request URL

`https://www.upmee.cc/open_api/stat/shop/detail`

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
| time_filter | Optional | string | Preset reporting period. Specify either this filter or the range defined by `start_time` and `end_time`.<br>- `unlimited`: All data<br>- `today`: Today<br>- `yesterday`: Yesterday<br>- `latest_7_days`: Last 7 days<br>- `latest_30_days`: Last 30 days |
| start_time | Optional | number | Start of the reporting period, as a timestamp in milliseconds. Applies when `time_filter` is empty. |
| end_time | Optional | number | End of the reporting period, as a timestamp in milliseconds. Applies when `time_filter` is empty. |
| page | Required | number | Page number. Minimum: 1. |
| page_size | Required | number | Items per page. Minimum: 1. |
| team_id | Optional | string | Team ID. Specifies the team whose data to query. |
| pub_time_filter | Required | number | Video publication time range filter.<br>- `-1`: All publication times<br>- `7`: Published in the last 7 days<br>- `30`: Published in the last 30 days |
| pub_start_time | Optional | number | Start of the video publication range, as a timestamp in milliseconds. Applies when `pub_time_filter` is empty. |
| pub_end_time | Optional | number | End of the video publication range, as a timestamp in milliseconds. Applies when `pub_time_filter` is empty. |
| pub_video_filter | Optional | number | Video scope filter.<br>- `1`: All videos<br>- `2`: Published by the team<br>- `3`: Published by the current user |
| media_ids | Optional | []string | List of account IDs to filter the data by account |
| media_types | Optional | []string | List of platform types as strings.<br>- `tiktok_shop_creator`: TikTok Shop creator account |
| task_ids | Optional | []string | List of task IDs to filter the data by task |
| item_ids | Optional | []string | List of video IDs to filter the data by video |
| groups | Optional | []number | Grouping dimensions. Multiple dimensions can be combined.<br>- `1`: Group by account<br>- `2`: Group by platform<br>- `3`: Group by task<br>- `4`: Group by video<br>- `5`: Group by time<br>- `16`: Group by user<br>- `17`: Group by product |
| orders | Optional | []object | List of sort rules |
| orders.by | Optional | string | Sort field. Supported values:<br>- `view`: Sort by views<br>- `click`: Sort by product clicks<br>- `click_rate`: Sort by click-through rate<br>- `gmv`: Sort by GMV |
| orders.desc | Optional | bool | Sort direction. `true` means descending and `false` means ascending. |

### Request Example

```json
{
    "time_filter": "unlimited",
    "pub_time_filter": -1,
    "page": 1,
    "page_size": 20,
    "team_id": "xxxxxx",
    "pub_video_filter": 1,
    "media_types": [
        "tiktok_shop_creator"
    ],
    "groups": [
        2
    ],
    "orders": [
        {
            "by": "view",
            "desc": false
        }
    ]
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| Stats | []object | List of analytics results |
| Stats.groups | []number | Grouping dimensions used for this record |
| Stats.media_id | string | Account ID. Returned when grouped by account. |
| Stats.media_name | string | Account name. Returned when grouped by account. |
| Stats.media_type | string | Platform type. Returned when grouped by platform. |
| Stats.task_id | string | Task ID. Returned when grouped by task. |
| Stats.task_title | string | Task name. Returned when grouped by task. |
| Stats.cover_id | string | Task cover image ID. Returned when grouped by task. |
| Stats.item_id | string | Video ID. Returned when grouped by video. |
| Stats.item_title | string | Video title. Returned when grouped by video. |
| Stats.time | number | Timestamp in milliseconds. Returned when grouped by time. |
| Stats.team_id | string | Team ID. Returned when grouped by team. |
| Stats.team_name | string | Team name. Returned when grouped by team. |
| Stats.uid | string | User ID. Returned when grouped by user. |
| Stats.user_name | string | Username. Returned when grouped by user. |
| Stats.user_avatar | string | User avatar. Returned when grouped by user. |
| Stats.user_email | string | User email address. Returned when grouped by user. |
| Stats.product_id | string | Product ID. Returned when grouped by product. |
| Stats.product_cover | string | Product cover image. Returned when grouped by product. |
| Stats.product_name | string | Product name. Returned when grouped by product. |
| Stats.product_commission_rate | string | Product commission rate. Returned when grouped by product. |
| Stats.product_price | string | Product price. Returned when grouped by product. |
| Stats.product_currency | string | Product currency. Returned when grouped by product. |
| Stats.stat | object | Metric data |
| Stats.stat.gmv | float | Total GMV |
| Stats.stat.gmv_currency | string | GMV currency |
| Stats.stat.view | number | Views |
| Stats.stat.like | number | Number of likes |
| Stats.stat.share | number | Shares |
| Stats.stat.comment | number | Comments |
| Stats.stat.click | number | Product clicks |
| Stats.stat.click_through_rate | float | Click-through rate |
| Stats.stat.like_rate | float | Like rate |
| Stats.stat.share_rate | float | Share rate |
| Stats.stat.comment_rate | float | Comment rate |
| Stats.stat.click_rate | float | Product click-through rate |
| Stats.stat.gmv_incr | float | Change in GMV from the previous period |
| Stats.stat.gmv_incr_rate | float | Percentage change in GMV from the previous period |
| Stats.stat.view_incr | number | Change in views from the previous period |
| Stats.stat.view_incr_rate | float | Percentage change in views from the previous period |
| Stats.stat.like_incr | number | Change in likes from the previous period |
| Stats.stat.like_incr_rate | float | Percentage change in likes from the previous period |
| Stats.stat.share_incr | number | Change in shares from the previous period |
| Stats.stat.share_incr_rate | float | Percentage change in shares from the previous period |
| Stats.stat.comment_incr | number | Change in comments from the previous period |
| Stats.stat.comment_incr_rate | float | Percentage change in comments from the previous period |
| Stats.stat.click_incr | number | Change in product clicks from the previous period |
| Stats.stat.click_incr_rate | float | Percentage change in product clicks from the previous period |
| page_info | object | Pagination information |
| page_info.page | number | Current page number |
| page_info.page_size | number | Items per page |
| page_info.total_size | number | Total number of records |
| page_info.total_page | number | Total pages |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "Stats": [
            {
                "groups": [
                    2
                ],
                "media_type": "tiktok_shop_creator",
                "stat": {
                    "gmv": 0,
                    "gmv_currency": "USD",
                    "view": 2486,
                    "like": 35,
                    "share": 0,
                    "comment": 0,
                    "click": 111,
                    "like_rate": 0.0141,
                    "share_rate": 0,
                    "comment_rate": 0,
                    "click_rate": 0.0447
                }
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
