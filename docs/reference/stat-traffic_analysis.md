# Query Traffic Reports (Social Media)

### Request URL

`https://www.upmee.cc/open_api/stat/traffic_analysis`

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
| page_size | Required | int | Items per page, up to `100` |
| media_types | Required | string[] | Platform type. Specify exactly one.<br>- `youtube`: YouTube<br>- `facebook_page`: Facebook Page<br>- `tiktok_business`: TikTok Business |
| pub_time_filter | Optional | int | Preset filter for publication time. If omitted or set to `0`, no time limit applies.<br>- `-1`: No limit<br>- `7`: Last 7 days<br>- `30`: Last 30 days<br>- `60`: Last 60 days<br>- `90`: Last 90 days<br>- `365`: Last 365 days |
| pub_start_time | Optional | int64 | Custom start of the publication time range, as a timestamp in milliseconds. Both `pub_start_time` and `pub_end_time` must be set. If `pub_time_filter` is also set, the custom range takes precedence. |
| pub_end_time | Optional | int64 | Custom end of the publication time range, as a timestamp in milliseconds. Both `pub_start_time` and `pub_end_time` must be set. If `pub_time_filter` is also set, the custom range takes precedence. |
| pub_video_filter | Optional | int | Video scope<br>- `1`: All videos<br>- `2`: Published by the team<br>- `3`: Published by the current user |
| media_ids | Optional | string[] | List of social account IDs |
| task_ids | Optional | string[] | List of task IDs |
| item_ids | Optional | string[] | List of post IDs |
| dimension_name | Optional | string | Breakdown dimension. Omit to retrieve metrics (aggregate metrics). Specify a value to retrieve dimension (audience data such as gender or age).<br>Breakdown dimensions:<br>- youtube<br>- `gender`: Gender distribution<br>- `age`: Age distribution<br>- `impression source`: Traffic source<br>- `country`: Geographic distribution<br>- `subscribed status`: Audience type<br>- `playback location`: Playback location<br>- `play device`: Playback device<br>- `operating system`: Operating system<br><br>- tiktok\_business<br>- `gender`: Gender distribution<br>- `impression source`: Traffic source<br>- `audience country`: Top regions<br>- `audience type`: Audience type<br><br>- facebook\_page<br>- `gender`: Gender distribution<br>- `distribution type`: Distribution by channel<br>- `age`: Age distribution<br>- `country`: Geographic distribution |
| Orders | Optional | object[] | Sort parameters |
| Orders.by | Optional | string | For metrics, the default sort is `create_time` in descending order.<br>For dimension, results are sorted by `create_time` and `item_id` in descending order, then by the supplied orders.<br>Sort field<br>- `share`: Shares<br>- `share_rate`: Share rate<br>- `comment`: Comments<br>- `comment_rate`: Comment rate<br>- `digg`: Number of likes<br>- `digg_rate`: Like rate<br>- `play`: Views<br>- `play_rate`: View rate<br>- `download`: Downloads<br>- `download_rate`: Download rate<br>- `forward`: Reposts<br>- `forward_rate`: Repost rate<br>- `favorite`: Saves<br>- `favorite_rate`: Save rate<br>- `dislike`: Dislikes<br>- `reach`: Reach<br>- `item_id`: Video ID<br>- `create_time`: Publication time<br>- `original_spend`: Original ad spend<br>- `base_spend`: Baseline ad spend<br>- `impressions`: Ad impressions<br>- `clicks`: Ad clicks<br>- `conversion`: Ad conversions<br>- `total_time_watched`: Total watch time<br>- `average_time_watched`: Average watch time<br>- `full_video_watched_rate`: Completion rate<br>- `full_video_watched`: Completed views<br>- `subscribers_gained`: Followers gained<br>- `subscribers_lost`: Followers lost<br>- `estimated_revenue`: Estimated total revenue<br>- `average_view_percentage`: Average percentage viewed<br>- `annotation_click_through_rate`: Annotation click-through rate<br>- `annotation_close_rate`: Annotation close rate<br>- `profile_view`: Profile visits<br>- `website_click`: Website clicks<br>- `phone_number_click`: Phone number clicks<br>- `lead_submission`: Lead submissions<br>- `app_download_click`: App download clicks<br>- `email_click`: Email clicks<br>- `address_click`: Address clicks |
| Orders.desc | Optional | bool | Sort direction. `true` means descending and `false` means ascending. Defaults to false. |

### Request Example

```json
{
    "page": 1,
    "page_size": 20,
    "media_types": [
        "facebook_page"
    ],
    "team_id": "xxxxxx",
    "pub_time_filter": -1,
    "pub_video_filter": 1
}
```

### Response Parameters

#### metrics (`dimension_name` is empty)

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| code | int | Application status code. `0` indicates success. |
| message | string | Status message |
| request_id | string | Unique request ID |
| data | object | Response data |
| data.stats | object[] | List of post metrics |
| data.stats.groups | int[] | Fixed at `[4]` (group by post) |
| data.stats.item_id | string | Post ID |
| data.stats.item_title | string | Post title |
| data.stats.item_cover | string | Cover image |
| data.stats.item_video | string | Video URL |
| data.stats.item_create_time | int64 | Publication time (milliseconds) |
| data.stats.create_time | int64 | Publication time (milliseconds) |
| data.stats.media_id | string | Social account ID |
| data.stats.media_type | int | Platform type |
| data.stats.stat | object | Metrics. All platforms use the same field structure. Fields with no data are omitted. |
| data.stats.stat.play | int64 | Views |
| data.stats.stat.digg | int64 | Number of likes |
| data.stats.stat.comment | int64 | Comments |
| data.stats.stat.share | int64 | Shares |
| data.stats.stat.download | int64 | Downloads |
| data.stats.stat.forward | int64 | Reposts |
| data.stats.stat.favorite | int64 | Saves |
| data.stats.stat.coin | int64 | Coin count (primarily BiliBili) |
| data.stats.stat.danmaku | int64 | On-screen comment count (primarily BiliBili) |
| data.stats.stat.dislike | int64 | Dislikes |
| data.stats.stat.reach | int64 | Reach |
| data.stats.stat.play_rate | float | View rate (the current select value is fixed at `null`) |
| data.stats.stat.digg_rate | float | Like rate |
| data.stats.stat.comment_rate | float | Comment rate |
| data.stats.stat.share_rate | float | Share rate |
| data.stats.stat.download_rate | float | Download rate |
| data.stats.stat.forward_rate | float | Repost rate |
| data.stats.stat.favorite_rate | float | Save rate |
| data.stats.stat.coin_rate | float | Coin rate |
| data.stats.stat.danmaku_rate | float | On-screen comment rate |
| data.stats.stat.dislike_rate | float | Dislike rate |
| data.stats.stat.reach_rate | float | Reach rate |
| data.stats.stat.total_time_watched | float | Total watch time (seconds) |
| data.stats.stat.full_video_watched_rate | float | Completion rate |
| data.stats.stat.full_video_watched | int64 | Completed views |
| data.stats.stat.average_time_watched | float | Average watch time (seconds) |
| data.stats.stat.subscribers_gained | int64 | Followers gained |
| data.stats.stat.subscribers_lost | int64 | Followers lost |
| data.stats.stat.estimated_revenue | float | Estimated revenue |
| data.stats.stat.annotation_click_through_rate | float | Annotation click-through rate |
| data.stats.stat.annotation_close_rate | float | Annotation close rate |
| data.stats.stat.post_video_complete_views_organic | int64 | Completed views (organic) |
| data.stats.stat.post_video_complete_views_organic_unique | int64 | Viewers who watched to completion (organic) |
| data.stats.stat.profile_view | int64 | Profile visits |
| data.stats.stat.website_click | int64 | Website clicks |
| data.stats.stat.phone_number_click | int64 | Phone clicks |
| data.stats.stat.lead_submission | int64 | Lead submissions |
| data.stats.stat.app_download_click | int64 | App download clicks |
| data.stats.stat.email_click | int64 | Email clicks |
| data.stats.stat.address_click | int64 | Address clicks |
| data.stats.stat.average_view_percentage | float | Average percentage viewed |
| data.page | int | Current page number |
| data.page_size | int | Items per page |
| data.total_size | int | Total items |
| data.total_page | int | Total pages |

#### dimension (`dimension_name` is supplied)

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| code | int | Application status code. `0` indicates success. |
| message | string | Status message |
| request_id | string | Unique request ID |
| data | object | Response data |
| data.stats | object[] | List of breakdown details |
| data.stats.metric_name | string | Dimension value, such as country name or gender |
| data.stats.item_id | string | Post ID |
| data.stats.stat | object | Metrics for this dimension. Fields vary by platform. |
| data.stats.stat.views | int64 | Views (YouTube) |
| data.stats.stat.views_percentage | float | View share (TikTok) |
| data.stats.stat.viewer_percentage | float | Audience share (YouTube) |
| data.stats.stat.estimated_secondes_watched | int64 | Total watch time in seconds (YouTube / Facebook) |
| data.items | map\<string, object\> | Map of post information. Each key is the post’s `item_id` and each value contains its details. |
| data.items.item_id | string | Post ID |
| data.items.item_title | string | Title |
| data.items.media_id | string | Social account ID |
| data.items.media_type | int | Platform type |
| data.items.item_cover | string | Cover image |
| data.items.item_video | string | Video URL |
| data.items.item_create_time | int64 | Publication time (milliseconds) |
| data.page | int | Current page number |
| data.page_size | int | Items per page |
| data.total_size | int | Total items |
| data.total_page | int | Total pages |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "stats": [
            {
                "groups": [
                    4
                ],
                "media_id": "xxxxxx",
                "media_type": 7,
                "item_id": "xxxxxx",
                "item_title": "xxxxxx",
                "item_cover": "https://xxxxxx",
                "item_create_time": 1787985366000,
                "item_video": "xxxxxx",
                "create_time": 1787985366000,
                "stat": {
                    "share": 88,
                    "comment": 150,
                    "digg": 1760,
                    "download": 0,
                    "play": 42100,
                    "forward": 60,
                    "favorite": 240,
                    "dislike": 5,
                    "reach": 35000,
                    "total_time_watched": 8420,
                    "full_video_watched_rate": 0.14,
                    "full_video_watched": 5894,
                    "average_time_watched": 0.2,
                    "share_rate": 0.0021,
                    "comment_rate": 0.0036,
                    "digg_rate": 0.0418,
                    "download_rate": 0,
                    "forward_rate": 0.0014,
                    "favorite_rate": 0.0057,
                    "reach_rate": 0.8314,
                    "dislike_rate": 0.0001
                }
            }
        ],
        "page": 1,
        "page_size": 20,
        "total_size": 1,
        "total_page": 1
    }
}
```
