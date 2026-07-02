# Analytics API

---

## Content Analytics {#content-analytics}

**Path** `POST /open_api/stat/detail`
**Auth** `API-Key: {your_key}` plus account login session (Session Cookie)
**team_id** Passed via `item_filter.team_id`

> Supports multi-dimensional grouping — aggregate stats by account, platform type, task, content item, time, team, etc.

### Request Parameters

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| start_time | number | - | Stats start time (Unix ms) — use with `end_time` instead of `time_filter` |
| end_time | number | - | Stats end time (Unix ms) |
| time_filter | object | - | Preset time range — alternative to `start_time`/`end_time` |
| media_types | string[] | - | Filter by platform type: `tiktok_biz` / `youtube` / `instagram` etc. |
| item_filter | object | - | Content dimension filters |
| > team_id | number | - | Team ID |
| > pub_time_filter | number | - | Content publish time range: `-1` all / `7` last 7d / `30` last 30d / `60` last 60d / `90` last 90d / `365` last year |
| > pub_start_time | number | - | Content publish start time (Unix ms) |
| > pub_end_time | number | - | Content publish end time (Unix ms) |
| > media_ids | number[] | - | Filter by account IDs |
| > task_ids | number[] | - | Filter by task IDs |
| > item_ids | string[] | - | Filter by platform content IDs |
| page | number | - | Page number, starting from 1 |
| page_size | number | - | Items per page |
| groups | object[] | - | Grouping dimensions — each item specifies a `by` field (e.g. `media_id`, `media_type`, `task_id`, `item_id`, `time`) |
| orders | object[] | - | Sort rules — each item has `by` (sort field) and `desc` (boolean, descending) |

### Response

| Field | Type | Description |
| :--- | :--- | :--- |
| page_info | object | Pagination info (page, page_size, total_size, total_page) |
| Stats | object[] | Aggregated result list — each item is one grouped result |
| > groups | object[] | Grouping dimensions for this result row |
| > media_id | number | Present when grouped by account — account ID |
| > media_name | string | Present when grouped by account — account name |
| > media_type | string | Present when grouped by platform type |
| > task_id | number | Present when grouped by task |
| > task_title | string | Present when grouped by task — task title |
| > cover_id | string | Present when grouped by task — cover file ID |
| > item_id | string | Present when grouped by content — platform content ID |
| > item_title | string | Present when grouped by content — content title |
| > time | number | Present when grouped by time (Unix ms) |
| > team_id | number | Present when grouped by team |
| > team_name | string | Present when grouped by team — team name |
| > stat | object | Aggregated metrics for this group (views, likes, comments, shares, etc.) |