# Account Management API

---

## List Accounts {#list-accounts}

**Path** `POST /open_api/media/list`
**Auth** `API-Key: {your_key}`
**team_id** Required

### Request Parameters

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| team_id | number | ✅ | Team ID |
| page | number | ✅ | Page number, starting from 1 |
| page_size | number | ✅ | Items per page, max 50 |
| team_ids | number[] | - | Filter by multiple team IDs |
| media_ids | number[] | - | Filter by specific account IDs |
| media_types | string[] | - | Filter by platform type: `tiktok_biz` / `youtube` / `instagram` / `facebook_page` / `bilibili` / `kuaishou` / `bluesky` / `threads` / `linkedin` / `vk` / `wechat_channels` / `pinterest` |
| name | string | - | Fuzzy search by account name |
| valid | boolean | - | Filter by auth status: `true` valid only / `false` invalid only / omit for all |
| need_upmee_stat | boolean | - | Include platform stats in response, default `false` |

### Response

| Field | Type | Description |
| :--- | :--- | :--- |
| page | number | Current page |
| page_size | number | Items per page |
| total_size | number | Total record count |
| total_page | number | Total pages |
| list | object[] | Account list |
| > media_id | number | Account ID — use this as `media_ids` in publish endpoints |
| > media_type | string | Platform type, e.g. `tiktok_biz` / `youtube` / `instagram` |
| > business_type | string | Business type: `creator` / `advertise` |
| > name | string | Display name |
| > username | string | Platform username |
| > gender | string | Gender |
| > avatar | string | Avatar URL |
| > country | string | Country |
| > province | string | Province / state |
| > city | string | City |
| > valid | boolean | Whether authorization is valid |
| > fans | number | Follower count |
| > remark | string | Notes |
| > currency | string | Currency (ad accounts only) |
| > ad_balance | number | Ad account balance (ad accounts only) |
| > create_time | number | Binding time (Unix ms) |

---

## Delete Account {#delete-account}

**Path** `POST /open_api/media/delete`
**Auth** `API-Key: {your_key}`
**team_id** Required

### Request Parameters

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| team_id | number | ✅ | Team ID |
| media_ids | number[] | ✅ | List of account IDs to delete |

### Response

No extra data — `code=0` means success.

---

## Get OAuth URL {#get-oauth-url}

**Path** `POST /open_api/media/oauth`
**Auth** `API-Key: {your_key}`
**team_id** Required

> Returns a platform OAuth URL. Direct the user to this URL to complete authorization; the account will be automatically bound to the team afterward.

### Request Parameters

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| team_id | number | ✅ | Team ID |
| media_type | string | ✅ | Target platform: `tiktok_biz` / `youtube` / `instagram` / `facebook_page` etc. |
| state_dev | string | - | Custom passthrough parameter, returned as-is in the OAuth callback |
| region | string | - | Region dial code, required by some platforms, e.g. `+1` (US) / `+44` (UK) / `+81` (JP) |
| qualification_location | string | - | Qualification region: `LOCAL` / `OTHER` |

### Response

| Field | Type | Description |
| :--- | :--- | :--- |
| oauth_url | string | OAuth authorization URL — present this to the user to click and authorize |

---

## Trending Music {#trending-music}

**Path** `POST /open_api/media/popular_tracks/list`
**Auth** `API-Key: {your_key}`
**team_id** Required

> Returns TikTok trending background music. Use the returned `track_id` in `tiktok_biz_data.track_info.track_id` when publishing a video.

### Request Parameters

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| team_id | number | ✅ | Team ID |
| genre | string | - | Music genre filter, e.g. `pop` / `hip_hop` |
| country_code | string | - | Country code, e.g. `US` / `JP` |
| date_range | string | - | Time range: `7` last 7 days / `30` last 30 days |

### Response

| Field | Type | Description |
| :--- | :--- | :--- |
| list | object[] | Trending music list |
| > name | string | Track name |
| > author | string | Artist name |
| > duration | number | Duration (seconds) |
| > track_id | string | Track ID — use in `tiktok_biz_data.track_info.track_id` |
| > preview_url | string | Preview audio URL (CDN) |
| > thumbnail_url | string | Cover image URL (CDN) |
| > source_preview_url | string | Original platform preview URL |
| > source_thumbnail_url | string | Original platform cover URL |