# Update an Image Publishing Task (Social Media)

### Request URL

`https://www.upmee.cc/open_api/media/task/update/image`

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
| task_id | Required | string | ID of the task to update |
| team_id | Required | number | Team ID |
| media_ids | Required | number[] | List of social accounts |
| title | Required | string | Task title |
| is_independence | Optional | number | Multi-platform settings mode. 0: shared basic information. 1: separate settings. |
| img_text_list | Required | ImageData[] | Image data |
| img_text_list.key | Required | string | `object_id` returned after uploading the image |
| common_data | Required | ImageTaskCommonData | Common parameters |
| common_data.desc | Optional | string | Shared description. A platform-specific description takes precedence. |
| common_data.enable_first_comment | Optional | boolean | Whether to add a first comment |
| common_data.first_comment | Conditionally required | string | Text of the first comment. Required when enable\_first\_comment is true. |
| instagram_data | Optional | InstagramImageData | Object containing the parameters required to post to Instagram |
| instagram_data.collaborators | Optional | string[] | Collaborator tags. Add multiple usernames to make those users co-publishers of the content. |
| instagram_data.desc | Optional | string | Description. If provided, it overrides the value in `ImageTaskCommonData`. |
| facebook_page_data | Optional | FacebookImageData | Object containing the parameters required to post to Facebook Page |
| facebook_page_data.desc | Optional | string | Description. If provided, it overrides `desc` in `ImageTaskCommonData`. |
| tiktok_biz_data | Optional | TiktokImageData | Object containing the parameters required to post to TikTok |
| tiktok_biz_data.desc | Optional | string | Description. If provided, it overrides the value in `ImageTaskCommonData`. |
| tiktok_biz_data.privacy_level | Required | string | Visibility setting<br>- `PUBLIC_TO_EVERYONE`: Visible to all TikTok users.<br>- `MUTUAL_FOLLOW_FRIENDS`: Visible only to friends who follow each other.<br>- `FOLLOWER_OF_CREATOR`: Visible only to followers of the account.<br>- `SELF_ONLY`: Private, visible only to you. |
| tiktok_biz_data.title | Optional | string | Title |
| tiktok_biz_data.auto_add_music | Optional | bool | Whether to add music automatically<br>Default: `false` |
| tiktok_biz_data.disable_comment | Optional | bool | Whether comments are disabled<br>Default: `false` |
| tiktok_biz_data.location_id | Optional | string | Location ID |
| tiktok_biz_data.location_name | Optional | string | Location name |
| tiktok_biz_data.is_track_enabled | Optional | bool | Whether to enable music.<br>> Default: `false`<br>> <br>> |
| tiktok_biz_data.track_info | Conditionally required | object | Track information. Required when `is_track_enabled` is `true`. |
| tiktok_biz_data.track_info.track_id | Required | string | Track ID |
| pinterest_data | Optional | PinterestImageData | Object containing the parameters required to post to Pinterest |
| pinterest_data.title | Optional | string | Title |
| pinterest_data.desc | Optional | string | Description. If provided, it overrides the value in `ImageTaskCommonData`. |
| pinterest_data.link | Optional | string | URL |
| pinterest_data.boards | Required | map[string]PinterestBoard | Boards. Pass a `Map` with the social account ID as the `key` and a **`PinterestBoard`** as the `value`. |
| threads_data | Optional | ThreadsImageData | Object containing the parameters required to post to Threads |
| threads_data.desc | Optional | string | Post description. Maximum length: `5000` characters. |
| threads_data.tags | Optional | string[] | Tag. Threads currently supports only one tag. |
| linked_in_data | Optional | LinkedInImageData | Object containing the parameters required to post to LinkedIn |
| pub_time | Conditionally required | number | Scheduled publication time as a timestamp in milliseconds. If omitted, the default is to publish immediately. If provided, it must be in the future. |
| is_draft | Optional | bool | Whether to save as a draft. Defaults to false. |

#### LinkedinImageData

<!-- api-fields -->

| Field | Required <!-- api-tag --> | Type | Description |
| --- | --- | --- | --- |
| desc | Optional | string | Description |
| visibility | Required | string | Content visibility. Allowed values:<br>- `CONNECTIONS`: Visible to the owner's first-degree connections<br>- `PUBLIC`: Visible to everyone<br>- `LOGGED_IN`: Visible only to signed-in members<br>- `CONTAINER`: Visibility is delegated to the owner of the container entity. For example, for posts in a group, the group authorization API determines visibility. |

### Request Example

```json
{
    "task_id": "xxxxxx",
    "team_id": "xxxxxx",
    "media_ids": [
        "xxxxxx",
        "xxxxxx",
        "xxxxxx",
        "xxxxxx"
    ],
    "is_independence": 0,
    "is_draft": true,
    "title": "xxxxxx",
    "img_text_list": [
        {
            "key": "xxxxxx"
        }
    ],
    "common_data": {
        "desc": "xxxxxx"
    },
    "instagram_data": {
        "desc": "xxxxxx",
        "collaborators": []
    },
    "facebook_page_data": {
        "desc": "xxxxxx"
    },
    "tiktok_biz_data": {
        "desc": "xxxxxx",
        "privacy_level": "PUBLIC_TO_EVERYONE",
        "title": "xxxxxx",
        "auto_add_music": true,
        "disable_comment": true,
        "is_track_enabled": true,
        "track_info": {
            "track_id": "xxxxxx"
        }
    },
    "pinterest_data": {
        "desc": "xxxxxx",
        "title": "xxxxxx",
        "link": "",
        "boards": {
            "3240": {
                "account_name": "xxxxxx",
                "board_id": "xxxxxx",
                "board_name": "xxxxxx"
            }
        }
    },
    "threads_data": {
        "desc": "xxxxxx",
        "tags": [
            "xxxxxx"
        ]
    },
    "linked_in_data": {
        "desc": "xxxxxx",
        "visibility": "PUBLIC"
    }
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| code | int | `0` indicates success |
| message | string | Status message |
| request_id | string | Unique request ID |
| data | object | Response data |
| data.task_id | string | Task ID |

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
