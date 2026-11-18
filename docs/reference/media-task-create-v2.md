# Create a Video Publishing Task (Social Media)

### Request URL

`https://www.upmee.cc/open_api/media/task/create/v2`

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
| media_ids | Required | []number | List of social accounts |
| title | Required | string | Task title |
| video_id | Required | string | object\_id returned by the upload endpoint |
| is_independence | Optional | number | Multi-platform settings mode. 0: shared basic information. 1: separate settings. |
| common_data | Required | TaskCommonData | Common parameters |
| common_data.desc | Optional | string | Video description |
| common_data.cover_id | Optional | string | Cover ID. Use the object\_id returned by the upload endpoint. |
| common_data.enable_first_comment | Optional | boolean | Whether to add a first comment |
| common_data.first_comment | Conditionally required | string | Text of the first comment. Required when enable\_first\_comment is true. |
| youtube_data | Optional | YoutubeData | Object containing the parameters required to post to YouTube |
| youtube_data.title | Required | string | User-defined title that describes the video |
| youtube_data.tags | Required | string[] | Keywords that help users find the video, for example `["technology", "AI", "tutorial"]` |
| youtube_data.category_id | Required | string | Predefined YouTube category ID. For example, `22` represents People and Blogs.<br>- `1`: Film and animation<br>- `2`: Autos and other vehicles<br>- `10`: Music<br>- `15`: Pets and animals<br>- `17`: Sports<br>- `19`: Travel and events<br>- `20`: Gaming<br>- `22`: People and blogs<br>- `23`: Comedy<br>- `24`: Entertainment<br>- `25`: News and politics<br>- `26`: How-to and style<br>- `27`: Education<br>- `28`: Science and technology |
| youtube_data.license | Required | string | Video license. Allowed values: `youtube` (standard YouTube license) and `creativeCommon` (license that permits others to reuse the video in their own creations). |
| youtube_data.embeddable | Required | bool | Whether to allow embedding on other sites. `true` allows embedding. With `false`, the video plays only on YouTube. |
| youtube_data.self_declared_made_for_kids | Required | bool | Whether the video is made for kids. `true` indicates it is made for kids and `false` indicates it is suitable for all ages. |
| youtube_data.privacy_status | Required | string | Video visibility. Allowed values: `public` (visible to everyone), `unlisted` (visible to anyone with the link), and `private` (visible only to the owner). |
| youtube_data.desc | Optional | string | Description |
| youtube_data.cover_id | Optional | string | Cover image `object_id`. If set, it overrides cover\_id in `TaskCommonData`. |
| instagram_data | Optional | InstagramData | Object containing the parameters required to post to Instagram |
| instagram_data.share_to_feed | Required | bool | Whether to share the content to the feed. `true` posts to the feed and `false` limits sharing to other methods. |
| instagram_data.collaborators | Optional | string[] | Collaborator tags. Add multiple usernames to make those users co-publishers of the content. |
| instagram_data.desc | Optional | string | Description |
| instagram_data.cover_id | Optional | string | Cover image `object_id`. If set, it overrides cover\_id in `TaskCommonData`. |
| facebook_page_data | Optional | FacebookPageData | Object containing the parameters required to post to Facebook Page |
| facebook_page_data.title | Required | string | Title |
| facebook_page_data.desc | Optional | string | Description |
| facebook_page_data.collaborator | Optional | int64 | Collaborator tag. Pass the collaborator's ID. |
| facebook_page_data.cover_id | Optional | string | Cover image `object_id`. If set, it overrides cover\_id in `TaskCommonData`. |
| tiktok_biz_data | Optional | TiktokBizData | Object containing the parameters required to post to TikTok |
| tiktok_biz_data.disable_comment | Required | bool | Whether to disable comments. `true` disables comments and `false` allows them. |
| tiktok_biz_data.disable_duet | Required | bool | Whether to disable Duet for this video. `true` disables Duet and `false` allows it. |
| tiktok_biz_data.disable_stitch | Required | bool | Whether to disable Stitch for this video. `true` disables Stitch and `false` allows it. |
| tiktok_biz_data.is_brand_organic | Required | bool | Default: `false`。<br>Set this field to `true` to identify the video as content promoting yourself or your business. The video displays the "Promotional content" label. |
| tiktok_biz_data.is_branded_content | Required | bool | Whether to enable the branded content setting for the video.<br>Default: `false`。Set this field to `true` to identify the video as branded content sponsored by a partner brand. The video displays the "Paid partnership" label. |
| tiktok_biz_data.is_ai_generated | Required | bool | Whether to label the post as AI-generated content.<br>If enabled, the published post displays the **Creator labeled as AI\-generated** label, which cannot be changed after publication. The label indicates that the content was fully generated by AI or substantially edited with AI.<br>Allowed values:  `true`，`false`。<br>Default:  `false`。 |
| tiktok_biz_data.is_ads_only | Required | bool | Whether to make the post visible only as an ad.<br>Allowed values: `true`，`false`。 Default: `false`。 |
| tiktok_biz_data.desc | Optional | string | Description |
| tiktok_biz_data.cover_id | Optional | string | Cover image `object_id`. If set, it overrides cover\_id in `TaskCommonData`. |
| tiktok_biz_data.location_id | Optional | string | Location ID |
| tiktok_biz_data.location_name | Optional | string | Location name |
| tiktok_biz_data.is_track_enabled | Optional | bool | Whether to enable music.<br>> Default: `false`<br>> <br>> |
| tiktok_biz_data.track_info | Conditionally required | object | Track information. Required when `is_track_enabled` is `true`. |
| tiktok_biz_data.track_info.track_id | Required | string | Track ID |
| bilibili_data | Optional | BilibiliData | Object containing the parameters required to post to BiliBili |
| bilibili_data.cover_id | Optional | string |  |
| bilibili_data.title | Required | string | Video title. Maximum length: `80` characters. |
| bilibili_data.tid | Required | integer | Video category ID |
| bilibili_data.no_reprint | Required | integer | Whether reposting is allowed<br>- `0`: Allow<br>- `1`: Disallow |
| bilibili_data.desc | Optional | string | Video description. Maximum length: `250` characters. |
| bilibili_data.tags | Required | string[] | Video tags |
| bilibili_data.copyright | Required | integer | - `1`: Original content<br>- `2`: Reposted content |
| bilibili_data.source | Conditionally required | string | - Source of the repost. Required when `copyright` is `2`. |
| threads_data | Optional | ThreadData | Object containing the parameters required to post to Threads |
| threads_data.desc | Optional | string | Post description. Maximum length: `5000` characters. |
| threads_data.tags | Optional | string[] | Tags |
| pinterest_data | Optional | PinterestData | Object containing the parameters required to post to Pinterest |
| pinterest_data.title | Optional | string | Title |
| pinterest_data.desc | Optional | string | Description |
| pinterest_data.link | Optional | string | URL |
| pinterest_data.boards | Required | map[string]PinterestBoard | Boards. Pass a `Map` with the social account ID as the `key` and a **`PinterestBoard`** as the `value`. |
| pinterest_data.boards.Key |  | string | Social account ID |
| pinterest_data.boards.Value |  | PinterestBoard | Board information |
| pinterest_data.boards.Value.board_id | Required | string | Board ID. Obtain it from the board list endpoint. |
| pinterest_data.boards.Value.board_name | Optional | string | Board name. Obtain it from the board list endpoint. **This parameter is stored for display only.** |
| pinterest_data.boards.Value.account_name | Optional | string | Account name. Obtain it from the board list endpoint. **This parameter is stored for display only.** |
| pinterest_data.cover_id | Optional |  | Cover image `object_id`. If set, it overrides cover\_id in `TaskCommonData`. |
| vk_data | Optional | VKData | Object containing the parameters required to post to VK |
| vk_data.title | Required | string | Title |
| vk_data.desc | Optional | string | Description |
| vk_data.privacy_view | Required | string | Privacy settings<br>- `all`: Everyone<br>- `friends`: Friends<br>- `only_me`: Only me |
| vk_data.no_comments | Required | string | - `0`: Keep comments enabled<br>- `1`: Disable comments |
| vk_data.wallpost | Required | string | - `0`: Do not post the video on the wall<br>- `1`: Post the video on the wall |
| bluesky_data | Optional | BlueskyData | Object containing the parameters required to post to Bluesky |
| bluesky_data.desc | Optional | string | Description |
| bluesky_data.langs | Optional | string[] | Language of the post. Use a **BCP\-47** language code such as `"th"` or `"en-US"`. |
| kuaishou_data | Optional | KuaiShouData | Object containing the parameters required to post to Kuaishou |
| kuaishou_data.desc | Optional | string | Description |
| kuaishou_data.cover_id | Optional | string | Cover image `object_id`. If set, it overrides cover\_id in `TaskCommonData`. |
| pub_time | Conditionally required | number | Scheduled publication time as a timestamp in milliseconds. If omitted, the default is to publish immediately. If provided, it must be in the future. |
| is_draft | Optional | bool | Whether to save as a draft. Defaults to false. |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "media_ids": [
        "xxxxxx"
    ],
    "title": "xxxxxx",
    "video_id": "xxxxxx",
    "is_independence": 0,
    "common_data": {
        "cover_id": "xxxxxx",
        "desc": "xxxxxx"
    },
    "youtube_data": {
        "title": "xxxxxx",
        "category_id": "xxxxxx",
        "self_declared_made_for_kids": false,
        "tags": [
            "xxxxxx"
        ],
        "license": "youtube",
        "tname": "xxxxxx",
        "privacy_status": "public",
        "embeddable": true
    },
    "instagram_data": {
        "share_to_feed": false,
        "collaborators": []
    },
    "facebook_page_data": {
        "title": "xxxxxx"
    },
    "tiktok_biz_data": {
        "thumbnail_offset": 0,
        "disable_comment": false,
        "disable_duet": false,
        "disable_stitch": false,
        "is_brand_organic": false,
        "is_branded_content": false,
        "is_ai_generated": true,
        "is_ads_only": false,
        "is_track_enabled": true,
        "track_info": {
            "track_id": "xxxxxx"
        }
    },
    "bilibili_data": {
        "title": "xxxxxx",
        "tid": 0,
        "no_reprint": 0,
        "tags": [
            "xxxxxx"
        ],
        "copyright": 1,
        "source": "xxxxxx"
    },
    "threads_data": {
        "tags": [
            "xxxxxx"
        ],
        "topic": "xxxxxx"
    },
    "pinterest_data": {
        "title": "xxxxxx",
        "link": "",
        "boards": {
            "{media_id}": {
                "account_id": "xxxxxx",
                "account_name": "xxxxxx",
                "board_id": "xxxxxx",
                "board_name": "xxxxxx"
            }
        }
    },
    "vk_data": {
        "title": "xxxxxx",
        "desc": "",
        "privacy_view": "all",
        "no_comments": "0",
        "wallpost": "1"
    },
    "bluesky_data": {
        "langs": [
            "zh-CN"
        ],
        "desc": "xxxxxx"
    },
    "kuaishou_data": {
        "desc": "xxxxxx",
        "cover_id": "xxxxxx"
    }
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| task_id | string | Task ID |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "task_id": "xxxxxx"
    }
}
```
