# Query Performance Data (Social Media)

### Request URL

`https://www.upmee.cc/open_api/stat/detail`

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
| time_filter | Conditionally required | string | Preset reporting period. If supplied, it takes precedence over `start_time` and `end_time`. Specify either `time_filter` or the `start_time` and `end_time` range.<br>- `unlimited`: All data<br>- `today`: Today’s data<br>- `yesterday`: Yesterday’s data<br>- `latest_7_days`: Data for the last 7 days<br>- `latest_30_days`: Data for the last 30 days<br>- `latest_90_days`: Data for the last 90 days<br>- `latest_365_days`: Data for the last 365 days |
| start_time | Conditionally required | integer | Timestamp for the start of the reporting period, in `milliseconds`. If `time_filter` is also supplied, `time_filter` takes precedence. |
| end_time | Conditionally required | integer | Timestamp for the end of the reporting period, in `milliseconds`. If `time_filter` is also supplied, `time_filter` takes precedence. |
| pub_time_filter | Conditionally required | integer | Preset filter for publication time. If omitted or set to `0`, no time limit applies.<br>- `-1`: No limit<br>- `7`: Last 7 days<br>- `30`: Last 30 days<br>- `60`: Last 60 days<br>- `90`: Last 90 days<br>- `365`: Last 365 days |
| pub_start_time | Conditionally required | integer | Timestamp for the start of the publication time range, in `milliseconds`. Applies only when both `pub_start_time` and `pub_end_time` are specified. |
| pub_end_time | Conditionally required | integer | Timestamp for the end of the publication time range, in `milliseconds`. Applies only when both `pub_start_time` and `pub_end_time` are specified. |
| pub_video_filter | Required | integer | Filter by who published the video<br>- `1`: All videos<br>- `2`: Published by the team<br>- `3`: Published by the current user |
| media_ids | Optional | string[] | List of social account IDs to filter by |
| media_types | Optional | integer[] | List of platform types to filter by<br>- `2`: Kuaishou<br>- `3`: BiliBili<br>- `5`: YouTube<br>- `6`: Instagram<br>- `7`: Facebook<br>- `8`: TikTok<br>- `11`: LinkedIn<br>- `13`: VK<br>- `15`: Threads<br>- `17`: Pinterest<br>- `19`: Bluesky |
| task_ids | Optional | string[] | Filter by task list |
| item_ids | Optional | string[] | Filter by video ID |
| groups | Required | integer[] | Grouping dimensions. Specify up to two. Supported values:<br>- `1`: Group by media\_id<br>- `2`: Group by media\_type<br>- `3`: Group by task\_id<br>- `4`: Group by item\_id<br>- `5`: Group by time<br>- `16`: Group by user |
| orders | Optional | object[] | Sorting options. Fields are listed below.<br>- `by` `string` Sort field<br>- `desc` `bool` Whether to sort in descending order |
| page | Required | integer | Page number |
| page_size | Required | integer | Page size |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "pub_time_filter": -1,
    "pub_video_filter": 1,
    "task_ids": [],
    "media_ids": [],
    "media_types": [
        "tiktok_business",
        "youtube",
        "facebook_page",
        "instagram",
        "pinterest",
        "tiktok_advertise",
        "thread",
        "bluesky",
        "bilibili",
        "douyin",
        "linked_in"
    ],
    "time_filter": "unlimited",
    "groups": [
        4
    ],
    "orders": [
        {
            "by": "play",
            "desc": true
        }
    ],
    "page": 1,
    "page_size": 1
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| Stats | GroupStat | Data |
| Stats.groups | integer[] | List of groups |
| Stats.media_id | string | The media\_id value when grouped by MediaID |
| Stats.media_name | string | The media\_name value when grouped by MediaID |
| Stats.media_type | string | The media\_type value when grouped by MediaType |
| Stats.task_id | string | The task\_id value when grouped by TaskID |
| Stats.item_id | string | The item\_id value when grouped by ItemID |
| Stats.time | string | Time value when grouped by time |
| Stats.uid | string | User ID. Returned when grouped by user. |
| Stats.user_name | string | Username. Returned when grouped by user. |
| Stats.user_avatar | string | User avatar. Returned when grouped by user. |
| Stats.user_email | string | User email address. Returned when grouped by user. |
| Stats.stat | Stat | Result data. May be null when grouped by time. |
| Stats.stat.share | integer | Shares |
| Stats.stat.share_rate | float | Share rate |
| Stats.stat.share_incr | integer | Change in share count from the previous period |
| Stats.stat.share_incr_rate | float | Percentage change in share count from the previous period |
| Stats.stat.comment | integer | Comments |
| Stats.stat.comment_rate | float | Comment rate |
| Stats.stat.comment_incr | integer | Change in comment count from the previous period |
| Stats.stat.comment_incr_rate | float | Percentage change in comment count from the previous period |
| Stats.stat.digg | integer | Number of likes |
| Stats.stat.digg_rate | float | Like rate |
| Stats.stat.digg_incr | integer | Change in like count from the previous period |
| Stats.stat.digg_incr_rate | float | Percentage change in like count from the previous period |
| Stats.stat.download | integer | Downloads |
| Stats.stat.download_rate | float | Download rate |
| Stats.stat.download_incr | integer | Change in download count from the previous period |
| Stats.stat.download_incr_rate | float | Percentage change in download count from the previous period |
| Stats.stat.play | integer | Views |
| Stats.stat.play_rate | float | View rate |
| Stats.stat.play_incr | integer | Change in view count from the previous period |
| Stats.stat.play_incr_rate | float | Percentage change in view count from the previous period |
| Stats.stat.forward | integer | Reposts |
| Stats.stat.forward_rate | float | Repost rate |
| Stats.stat.forward_incr | integer | Change in repost count from the previous period |
| Stats.stat.forward_incr_rate | float | Percentage change in repost count from the previous period |
| Stats.stat.favorite | integer | Saves |
| Stats.stat.reach | integer | Number of viewers |
| Stats.stat.total_time_watched | float | Total watch time (seconds) |
| Stats.stat.average_time_watched | float | Average playback time (seconds) |
| Stats.stat.full_video_watched | integer | Completed video views |
| Stats.stat.full_video_watched_rate | float | Percentage of completed video views |
| page_info | object | Pagination information<br>- `page` `integer` Current page number <br>- `page_size` `integer` Page size<br>- `total_size` `integer` Total number of records<br>- `total_page` `integer` Total pages |

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
                    4
                ],
                "media_id": "xxxxxx",
                "media_type": "tiktok_business",
                "item_id": "xxxxxx",
                "item_title": "{item_title}",
                "stat": {
                    "share": 366,
                    "comment": 141,
                    "digg": 17593,
                    "play": 1163108,
                    "favorite": 1356,
                    "reach": 1072228,
                    "total_time_watched": 211125.37,
                    "average_time_watched": 0.2,
                    "share_rate": 0.0003,
                    "comment_rate": 0.0001,
                    "digg_rate": 0.0151,
                    "favorite_rate": 0.0012,
                    "reach_rate": 0.9219
                }
            }
        ],
        "page_info": {
            "page": 1,
            "page_size": 1,
            "total_size": 1710,
            "total_page": 1710
        }
    }
}
```
