# Search Trending TikTok Music

### Request URL

`https://www.upmee.cc/open_api/media/popular_tracks/search`

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
| team_id | Required | number | Team ID. Used only to validate the authorization context. It does not affect which account is queried. |
| media_type | Required | string | Account type. Currently supported values:<br>- `tiktok_business`: TikTok Business ad account<br>- `tiktok_shop_creator`: TikTok Shop creator account |
| genre | Optional | string | Music genre<br>Supported only for `tiktok_business`. |
| country_code | Optional | string | Country code<br>> Supported only for `tiktok_business`.<br>> <br>> |
| date_range | Optional | string | Date range<br>> Supported only for `tiktok_business`.<br>> <br>> |
| search_id | Optional | string | When paginating, pass the `search_id` from the previous response.<br>> Supported only for `tiktok_shop_creator` and required when `media_type` is `tiktok_shop_creator`.<br>> <br>> |
| keyword | Conditionally required | string | Search keyword<br>> Supported only for `tiktok_shop_creator` and required when `media_type` is `tiktok_shop_creator`.<br>> <br>> |
| region | Optional | string | Region filter<br>> Supported only for `tiktok_shop_creator` and required when `media_type` is `tiktok_shop_creator`.<br>> <br>> |
| language | Optional | string | Language filter<br>> Supported only for `tiktok_shop_creator` and required when `media_type` is `tiktok_shop_creator`.<br>> <br>> |
| cursor | Optional | string | Pagination cursor. Pass an empty string on the first request, then pass the `cursor` from the previous response. |
| count | Optional | number | Items per page. Defaults to `20` if omitted or `<=0`. |
| after | Optional | string | Pagination direction marker. Pass it through from the previous response. |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "media_type": "xxxxxx",
    "country_code": "xxxxxx",
    "search_id": "xxxxxx",
    "keyword": "xxxxxx",
    "cursor": "xxxxxx"
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| list | []object | List of tracks |
| list.name | string | Track name |
| list.author | string | Artist name |
| list.duration | number | Duration (seconds) |
| list.preview_url | string | Preview playback URL |
| list.thumbnail_url | string | Thumbnail URL |
| list.track_id | string | Track ID on the external platform |
| list.source_preview_url | string | Original playback URL from the provider |
| list.source_thumbnail_url | string | Original thumbnail URL from the provider |
| search_id | string | Pass this value as `search_id` in the next request when paginating (TikTok Business). |
| cursor | string | Cursor for the next page (TikTok Shop creator account) |
| has_more | bool | Whether more results are available |
| after | string | Pagination direction marker |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "list": [
            {
                "name": "xxxxxx",
                "author": "xxxxxx",
                "duration": 10,
                "preview_url": "https://xxxxxx",
                "thumbnail_url": "https://xxxxxx",
                "track_id": "xxxxxx",
                "source_preview_url": "https://xxxxxx",
                "source_thumbnail_url": "https://xxxxxx"
            }
        ],
        "search_id": "xxxxxx",
        "cursor": "xxxxxx",
        "has_more": true,
        "after": "xxxxxx"
    }
}
```
