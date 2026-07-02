# TikTok Shop API

> All endpoints below apply to TikTok Shop Creator accounts.

---

## Create Shop Video Task {#create-shop-video-task}

**Path** `POST /open_api/shop/task/create`
**Auth** `API-Key: {your_key}`
**team_id** Required

> Creates a TikTok Shop Creator video publishing task for the bound shop accounts.

### Request Parameters

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| team_id | number | ✅ | Team ID |
| media_ids | number[] | ✅ | Target shop account ID list |
| video_id | string | ✅ | Uploaded video file ID (`object_id` — see upload.md) |
| title | string | - | Video title |
| common_data | object | - | Common publish data |
| > desc | string | - | Video description |
| > cover_id | string | - | Cover image file ID |
| tiktok_shop_creator_data | object | - | TikTok Shop Creator-specific parameters |
| > cover_id | string | - | Shop cover image file ID |
| > desc | string | - | Shop video description |
| > product_title | string | - | Product title |
| > mode | string | - | Review strategy |
| > is_track_enabled | boolean | - | Add background music |
| > track_info | object | - | Background music info |
| > > track_id | string | - | Track ID from [media.md](media.md#trending-music) |
| > media_product | object | - | Per-account product mapping — key is media_id, value is product info |
| > > id | string | - | Product ID from [shop.md](shop.md#list-shop-products) |

### Response

| Field | Type | Description |
| :--- | :--- | :--- |
| task_id | number | Created task ID |

---

## Create Shop Image Task {#create-shop-image-task}

**Path** `POST /open_api/shop/task/create/image`
**Auth** `API-Key: {your_key}`
**team_id** Required

> Creates a TikTok Shop Creator image post publishing task.

### Request Parameters

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| team_id | number | ✅ | Team ID |
| media_ids | number[] | ✅ | Target shop account ID list |
| img_text_list | object[] | ✅ | Image list |
| > key | string | ✅ | Image file ID (`object_id`) |
| title | string | - | Post title |
| common_data | object | - | Common publish data |
| > desc | string | - | Post description |
| > cover_id | string | - | Cover image file ID |
| tiktok_shop_creator_data | object | - | TikTok Shop Creator-specific parameters — same fields as the video task endpoint |

### Response

| Field | Type | Description |
| :--- | :--- | :--- |
| task_id | number | Created task ID |

---

## List Shop Tasks {#list-shop-tasks}

**Path** `POST /open_api/shop/task/list`
**Auth** `API-Key: {your_key}`
**team_id** Required

### Request Parameters

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| team_id | number | ✅ | Team ID |
| page | number | ✅ | Page number, starting from 1 |
| page_size | number | ✅ | Items per page, max 50 |
| team_ids | number[] | - | Filter by multiple team IDs |
| task_ids | number[] | - | Filter by specific task IDs, max 20 |
| pub_time_filter | number | - | Publish time range: `-1` all / `7` last 7d / `30` last 30d / `60` last 60d / `90` last 90d / `365` last year |
| title | string | - | Fuzzy search by title |
| task_type | number | - | Task type: `1` video / `2` image post |

### Response

| Field | Type | Description |
| :--- | :--- | :--- |
| page | number | Current page |
| page_size | number | Items per page |
| total_size | number | Total record count |
| total_page | number | Total pages |
| list | object[] | Task list |
| > task_id | number | Task ID |
| > state | string | Task status: `pending` / `processing` / `success` / `failed` |
| > audit_state | string | Review status |
| > task_type | string | Type: `video` / `image` |
| > pub_time | number | Publish time (Unix ms) |
| > create_time | number | Creation time (Unix ms) |
| > title | string | Task title |
| > video_id | string | Video file ID |
| > video | string | Video CDN URL |
| > cover_id | string | Cover file ID |
| > cover | string | Cover CDN URL |
| > medias | object[] | Per-account sub-task status |
| > > sub_task_id | number | Sub-task ID |
| > > media_id | number | Account ID |
| > > media_type | string | Platform type |
| > > name | string | Account name |
| > > state | string | Account status: `pending` / `processing` / `success` / `failed` |
| > > reason | string | Failure reason |
| > > error_msg | string | Detailed error message |
| > > item_id | string | Platform content ID after successful publish |
| > > pub_retryable | boolean | Whether retryable after failure |
| > tiktok_shop_creator_data | object | TikTok Shop Creator-specific data (see publish endpoint for field details) |

---

## List Shop Products {#list-shop-products}

**Path** `POST /open_api/shop/showcase_product/list`
**Auth** `API-Key: {your_key}`
**team_id** Required

> Lists products in a shop account. Use the returned product IDs when associating products in publishing tasks.

### Request Parameters

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| team_id | number | ✅ | Team ID |
| media_id | number | ✅ | Shop account's media_id |
| keyword | string | - | Fuzzy search by product name |
| status_filter | string | - | Status filter: `ALL` / `SHOPPABLE` / `HIDDEN` / `SOLD_OUT`, default `ALL` |
| order | string | - | Sort: `COMMISSION_RATE_ASC` / `COMMISSION_RATE_DESC` / `PRICE_ASC` / `PRICE_DESC` |
| cursor | string | - | Pagination cursor, empty on first call |
| count | number | - | Items per page |

### Response

| Field | Type | Description |
| :--- | :--- | :--- |
| cursor | string | Next page cursor — empty means no more data |
| has_more | boolean | Whether more data exists |
| list | object[] | Product list |
| > id | string | Product ID — use as `media_product.id` in publish tasks |
| > name | string | Product name |
| > status | string | Product status |
| > is_hidden | boolean | Whether hidden |
| > commission_rate | number | Commission rate as integer (e.g. `1234` = 12.34%) |
| > min_price | number | Minimum price |
| > max_price | number | Maximum price |
| > currency | string | Currency type |
| > cover_id | string | Cover image file ID |
| > cover | string | Cover image CDN URL |