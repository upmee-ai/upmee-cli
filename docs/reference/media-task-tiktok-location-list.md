# Search TikTok Post Locations

### Request URL

`https://www.upmee.cc/open_api/media/task/tiktok/location/list`

### HTTP Method

`POST`

### Request Headers

<!-- api-fields -->

| Field | Required <!-- api-tag --> | Type | Description |
| --- | --- | --- | --- |
| API-Key | Required | string | API key |
| Content-Type | Required | string | Request content type. Allowed format: `application/json`. |

### Request Parameters

<!-- api-fields -->

| Field | Required <!-- api-tag --> | Type | Description |
| --- | --- | --- | --- |
| team_id | Required | string | Team ID |
| search_query | Required | string | Keyword for finding locations that can be added to TikTok posts. Maximum length: 100 characters. |

> You can omit `media_id`. The server automatically selects an available TikTok business account from the current team and supplies the `business_id` and `Access-Token` required by TikTok.
> 
> 

### Request Example

```json
{
    "team_id": "xxxxxx",
    "search_query": "xxxxxx"
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| list | []object | List of locations |
| list.location_id | string | Location ID. Pass it as `tiktok_biz_data.location_id` when creating a video or photo post task. |
| list.location_name | string | Location name. When creating a task, pass it as `tiktok_biz_data.location_name` along with `location_id`. |
| list.location_address | string | Location address |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "list": [
            {
                "location_id": "xxxxxx",
                "location_name": "xxxxxx",
                "location_address": "xxxxxx"
            }
        ]
    }
}
```
