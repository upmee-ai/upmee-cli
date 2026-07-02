# Publishing Task API

---

## Publish Video v2 {#publish-video-v2}

**Path** `POST /open_api/media/task/create/v2`
**Auth** `API-Key: {your_key}`
**team_id** Required

> Supports publishing to multiple accounts simultaneously — use this version. Obtain `media_id` from [media.md](media.md#list-accounts) first; video files must be uploaded beforehand to get a `video_id` (see [upload.md](upload.md)).

### Request Parameters

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| team_id | number | ✅ | Team ID |
| media_ids | number[] | ✅ | Target account ID list |
| video_id | string | ✅ | Uploaded video file ID (object_id) |
| pub_now | boolean | ✅ | `true` publish immediately / `false` scheduled (requires `pub_time`) |
| pub_time | number | - | Scheduled publish time (Unix ms) — required when `pub_now=false` |
| title | string | - | Common video title for all platforms |
| cover_id | string | - | Cover image file ID |
| common_data | object | - | Common publish data applied to all platforms |
| > desc | string | - | Common description / caption |
| > cover_id | string | - | Cover image file ID (platform-level override) |
| > tags | string[] | - | Common hashtag list |
| > enable_first_comment | boolean | - | Auto-post a first comment after publishing |
| > first_comment | string | - | First comment text — effective when `enable_first_comment=true` and non-empty |
| youtube_data | object | - | YouTube-specific parameters |
| > title | string | - | Video title |
| > desc | string | - | Video description |
| > tags | string[] | - | Tag list |
| > category_id | string | - | Category ID |
| > privacy_status | string | - | Visibility: `public` / `unlisted` / `private` |
| > license | string | - | License: `youtube` / `creativeCommon` |
| > embeddable | boolean | - | Allow embedding |
| > self_declared_made_for_kids | boolean | - | Made for kids |
| tiktok_biz_data | object | - | TikTok-specific parameters |
| > title | string | - | Video title |
| > privacy_level | string | - | Visibility level |
| > disable_comment | boolean | - | Disable comments |
| > disable_duet | boolean | - | Disable duet |
| > disable_stitch | boolean | - | Disable stitch |
| > is_brand_organic | boolean | - | Promoting own business |
| > is_branded_content | boolean | - | Third-party branded content |
| > is_ai_generated | boolean | - | AI-generated content |
| > is_track_enabled | boolean | - | Add background music |
| > track_info | object | - | Background music info |
| > > track_id | string | - | Track ID from [media.md](media.md#trending-music) |
| bilibili_data | object | - | Bilibili-specific parameters |
| > title | string | - | Video title |
| > tid | number | - | Category ID from [task.md](task.md#bilibili-categories) |
| > tags | string[] | - | Tag list |
| > desc | string | - | Video description |
| > copyright | number | - | Copyright: `1` original / `2` repost |
| instagram_data | object | - | Instagram-specific parameters |
| > share_to_feed | boolean | - | Share to feed (for Reels) |
| > collaborators | string[] | - | Collaborator account list |
| facebook_page_data | object | - | Facebook-specific parameters |
| > title | string | - | Video title |
| pinterest_data | object | - | Pinterest-specific parameters |
| > title | string | - | Pin title |
| > desc | string | - | Pin description |
| > link | string | - | Pin destination URL |
| > boards | object | - | Board mapping — key is media_id, value is board info from [task.md](task.md#pinterest-boards) |
| threads_data | object | - | Threads-specific parameters |
| > desc | string | - | Caption |
| kuaishou_data | object | - | Kuaishou-specific parameters |
| > desc | string | - | Video description |
| linked_in_data | object | - | LinkedIn-specific parameters |
| bluesky_data | object | - | Bluesky-specific parameters |
| vk_data | object | - | VK-specific parameters |
| wechat_channels_data | object | - | WeChat Channels-specific parameters |
| > title | string | - | Title |
| > desc | string | - | Description |
| > post_flag | number | - | Originality: `0` original / `2` non-original |

### Response

| Field | Type | Description |
| :--- | :--- | :--- |
| task_id | number | Created task ID — use to query publish status |

---

## Publish Video v1 {#publish-video-v1}

**Path** `POST /open_api/media/task/create`
**Auth** `API-Key: {your_key}`
**team_id** Required

> Legacy endpoint — publishes to a single account at a time. Use v2 instead.

### Request Parameters

Same as v2, but uses `media_id` (single number) instead of `media_ids` (array).

### Response

| Field | Type | Description |
| :--- | :--- | :--- |
| task_id | number | Created task ID |

---

## Publish Image Post {#publish-image-post}

**Path** `POST /open_api/media/task/create/image`
**Auth** `API-Key: {your_key}`
**team_id** Required

### Request Parameters

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| team_id | number | ✅ | Team ID |
| media_ids | number[] | ✅ | Target account ID list |
| picture_ids | string[] | ✅ | Uploaded image file ID list (supports multiple images) |
| pub_now | boolean | ✅ | `true` publish immediately / `false` scheduled |
| pub_time | number | - | Scheduled publish time (Unix ms) |
| title | string | - | Common title |
| common_data | object | - | Common publish data |
| > desc | string | - | Caption / description |
| > tags | string[] | - | Common hashtag list |
| instagram_data | object | - | Instagram-specific parameters |
| > collaborators | string[] | - | Collaborator account list |
| tiktok_biz_data | object | - | TikTok-specific parameters |
| > privacy_level | string | - | Visibility level |
| pinterest_data | object | - | Pinterest-specific parameters |
| > boards | object | - | Board mapping |
| facebook_page_data | object | - | Facebook-specific parameters |
| threads_data | object | - | Threads-specific parameters |
| linked_in_data | object | - | LinkedIn-specific parameters |

### Response

| Field | Type | Description |
| :--- | :--- | :--- |
| task_id | number | Created task ID |

---

## List Tasks {#list-tasks}

**Path** `POST /open_api/media/task/list`
**Auth** `API-Key: {your_key}`
**team_id** Required

### Request Parameters

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| team_id | number | ✅ | Team ID |
| page | number | ✅ | Page number, starting from 1 |
| page_size | number | ✅ | Items per page, max 50 |
| pub_video_filter | string | ✅ | Scope: `"team"` all tasks in team / `"self"` tasks by current API Key's user |
| task_ids | number[] | - | Filter by specific task IDs, max 20 |
| task_type | number | - | Task type: `1` video / `2` image post |
| pub_time_filter | number | - | Time range: `-1` all / `7` last 7d / `30` last 30d / `60` last 60d / `90` last 90d / `365` last year |

### Response

| Field | Type | Description |
| :--- | :--- | :--- |
| page | number | Current page |
| page_size | number | Items per page |
| total_size | number | Total record count |
| total_page | number | Total pages |
| list | object[] | Task list |
| > task_id | number | Task ID |
| > state | string | Overall status: `pending` / `processing` / `success` / `failed` / `partial_success` |
| > task_type | string | Type: `video` / `image` |
| > pub_time | number | Publish time (Unix ms) |
| > create_time | number | Creation time (Unix ms) |
| > title | string | Task title |
| > video_id | string | Video file ID |
| > video | string | Video CDN URL |
| > cover_id | string | Cover file ID |
| > cover | string | Cover CDN URL |
| > medias | object[] | Per-platform sub-task status |
| > > sub_task_id | number | Sub-task ID |
| > > media_id | number | Account ID |
| > > media_type | string | Platform, e.g. `tiktok` / `youtube` / `instagram` |
| > > name | string | Account name |
| > > state | string | Platform status: `pending` / `processing` / `success` / `failed` |
| > > reason | string | Failure reason |
| > > error_msg | string | Detailed error message |
| > > item_id | string | Platform content ID after successful publish |
| > > pub_retryable | boolean | Whether retryable after failure |

---

## Bilibili Categories {#bilibili-categories}

**Path** `POST /open_api/media/task/bilibili/type/list`
**Auth** `API-Key: {your_key}`
**team_id** Required

> Call before publishing to Bilibili to get the `tid` for `bilibili_data.tid`.

### Request Parameters

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| team_id | number | ✅ | Team ID |

### Response

| Field | Type | Description |
| :--- | :--- | :--- |
| list | object[] | Bilibili category list |
| > tid | number | Category ID |
| > name | string | Category name |

---

## Pinterest Boards {#pinterest-boards}

**Path** `POST /open_api/media/task/pinterest/boards/list`
**Auth** `API-Key: {your_key}`
**team_id** Required

> Call before publishing to Pinterest to get board info for `pinterest_data.boards`.

### Request Parameters

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| team_id | number | ✅ | Team ID |
| media_id | number | ✅ | Pinterest account's media_id |
| page_size | number | - | Items per page, default 25 |
| bookmark | string | - | Pagination cursor — empty on first call, use `bookmark` from previous response |

### Response

| Field | Type | Description |
| :--- | :--- | :--- |
| media_id | number | Requested account ID |
| bookmark | string | Next page cursor — empty means no more data |
| boards | object[] | Board list |
| > id | string | Board ID |
| > name | string | Board name |