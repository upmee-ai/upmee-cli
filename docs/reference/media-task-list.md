# List Publishing Tasks (Social Media)

### Request URL

`https://www.upmee.cc/open_api/media/task/list`

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
| page | Required | number | Current page number.<br>Default: 1.<br>Range: 1 or greater |
| page_size | Required | number | Page size<br>Default: 10.<br>Range: 1–50 |
| team_id | Required | number | Team ID |
| task_ids | Required | string[] | Optional list of task IDs. Pass up to 20 IDs per request. |
| pub_time_filter | Optional | number | Publication time range filter<br>- `-1`: No filter<br>- `7`: Videos published in the last 7 days<br>- `30`: Videos published in the last 30 days<br>- `90`: Videos published in the last 90 days<br>- `365`: Videos published in the last 365 days |
| pub_video_filter | Optional | string | Publication scope filter<br>- `all`: All tasks<br>- `team`: Tasks published by the team<br>- `self`: Tasks published by the current user |

### Request Example

```json
{
    "page": 1,
    "page_size": 1,
    "team_id": "xxxxxx",
    "pub_time_filter": -1,
    "pub_video_filter": "team"
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| page | number | Current page |
| page_size | number | Current page size |
| total_size | number | Total items |
| total_page | number | Total pages |
| list | TaskView[] |  |
| list.task_id | string | Task ID |
| list.team_id | string | Team ID |
| list.state | string | Task status<br>- `wait`: Pending publication<br>- `publishing`: Publishing<br>- `publish_success`: Published successfully<br>- `publish_fail`: Publication failed<br>- `draft`: Draft<br>- `part_publish_success`: Partially published<br>- `part_publish_fail`: Partial publication failure |
| list.audit_state | string | Review status<br>- `none`: Review has not started<br>- `auditing`: Under review<br>- `part_success`: Partially approved<br>- `success`: Fully approved<br>- `part_fail`: Partially rejected<br>- `fail`: Fully rejected |
| list.task_type | string | Task type<br>- `video`: Video<br>- `picture`: Image |
| list.pub_time | number | Publication timestamp (milliseconds) |
| list.medias | SubTaskView |  |
| list.medias.sub_task_id | string | Subtask ID |
| list.medias.media_id | string | Platform type |
| list.medias.media_type | MediaType | Platform type |
| list.medias.avatar | string | Avatar URL |
| list.medias.name | string | Name |
| list.medias.state | string | Subtask status<br>- `publish`: Published<br>- `publish_failed`: Publication failed<br>- `audit`: Under review<br>- `success`: Published successfully<br>- `audit_failed`: Review failed |
| list.medias.privacy_state | string | Video visibility. YouTube supports three options. Other platforms support public and private visibility.<br>- `public`: Public<br>- `unlisted`: Visible to anyone with the link<br>- `private`: Private |
| list.medias.reason | string | Client error message |
| list.medias.error_msg | string | Error message |
| list.medias.error_code | string | Error code |
| list.medias.pub_retryable | bool | Whether the post can be published again |
| list.medias.item_id | string | Video ID |
| list.medias.cover | string | Cover URL |
| list.medias.video | string | Video URL on the external platform |
| list.medias.has_permission | bool | Whether access to the social account is authorized |
| list.medias.is_virtual | bool | false |
| list.title | string | Task title |
| list.cover | string | Cover URL |
| list.cover_id | string | Cover ID |
| list.video | string | Video URL |
| list.video_id | string | Video ID |
| list.is_virtual | bool | false |
| list.common_data | TaskCommonData |  |
| list.youtube_data | YoutubeData |  |
| list.instagram_data | InstagramData |  |
| list.facebook_page_data | FacebookPageData |  |
| list.tiktok_biz_data | TiktokBizData |  |
| list.bilibili_data | BilibiliData | Object containing the parameters required to post to BiliBili |
| list.threads_data | ThreadData | Object containing the parameters required to post to Threads |
| list.pinterest_data | PinterestData | Object containing the parameters required to post to Pinterest |
| list.vk_data | VKData | Object containing the parameters required to post to VK |
| list.bluesky_data | BlueskyData | Object containing the parameters required to post to Bluesky |
| list.kuaishou_data | KuaiShouData | Object containing the parameters required to post to Kuaishou |
| list.create_time | number | Task creation timestamp (milliseconds) |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "page": 1,
        "page_size": 1,
        "total_size": 98,
        "total_page": 98,
        "list": [
            {
                "task_id": "xxxxxx",
                "team_id": 0,
                "upmee_id": 0,
                "upmee_name": "",
                "state": "publish_success",
                "audit_state": "success",
                "task_type": "video",
                "pub_time": 1755766281000,
                "medias": [
                    {
                        "sub_task_id": "xxxxxx",
                        "media_id": "xxxxxx",
                        "media_type": "tiktok_business",
                        "avatar": "{avatar_url}",
                        "name": "xxxxxx",
                        "state": "success",
                        "privacy_state": "public",
                        "reason": "",
                        "pub_retryable": true,
                        "item_id": "xxxxxx",
                        "cover": "{cover_url}",
                        "video": "{channel_video_url}",
                        "has_permission": true,
                        "is_virtual": false
                    }
                ],
                "title": "xxxxxx",
                "cover": "{task_cover_url}",
                "cover_id": "xxxxxx",
                "video": "{task_video_url}",
                "video_id": "xxxxxx",
                "is_virtual": false,
                "common_data": {
                    "desc": "xxxxxx",
                    "cover_id": "xxxxxx",
                    "cover": "{cover_url}"
                },
                "kuaishou_data": {},
                "bilibili_data": {
                    "copyright": 1
                },
                "youtube_data": {
                    "category_id": "xxxxxx",
                    "license": "youtube",
                    "embeddable": true,
                    "self_declared_made_for_kids": false,
                    "privacy_status": "public",
                    "public_stats_viewable": false
                },
                "instagram_data": {
                    "share_to_feed": false,
                    "collaborators": []
                },
                "facebook_page_data": {
                    "node": 1
                },
                "tiktok_biz_data": {
                    "disable_comment": false,
                    "disable_duet": false,
                    "disable_stitch": false,
                    "thumbnail_offset": 0,
                    "privacy_level": "PUBLIC_TO_EVERYONE",
                    "auto_add_music": true,
                    "title": "",
                    "is_brand_organic": false,
                    "is_branded_content": false,
                    "is_ai_generated": false,
                    "is_ads_only": false,
                    "cover_id": "",
                    "cover": ""
                },
                "threads_data": {
                    "is_quote_post": false,
                    "desc": "",
                    "tags": [
                        ""
                    ]
                },
                "pinterest_data": {
                    "title": "",
                    "desc": "",
                    "link": "",
                    "boards": {},
                    "cover": "",
                    "cover_id": ""
                },
                "vk_data": {
                    "title": "",
                    "desc": "",
                    "privacy_view": "all",
                    "no_comments": "0",
                    "wallpost": "1"
                },
                "bluesky_data": {
                    "desc": "",
                    "langs": []
                },
                "create_time": 1755766268000
            }
        ]
    }
}
```
