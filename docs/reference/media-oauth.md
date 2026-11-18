# Generate an Authorization URL

### Request URL

`https://www.upmee.cc/open_api/media/oauth`

### HTTP Method

`POST`

### Request Headers

<!-- api-fields -->

| Field | Required <!-- api-tag --> | Type | Description |
| --- | --- | --- | --- |
| API-Key | Required | string | API key |
| Content-Type | Required | string | Request content type. The allowed format is `application/json`. |

### Request Parameters

<!-- api-fields -->

| Field | Required <!-- api-tag --> | Type | Description |
| --- | --- | --- | --- |
| team_id | Required | string | Team ID |
| media_type | Required | string | Media type to authorize. Select one value:<br>- `tiktok_business `: TikTok Business<br>- ` youtube `: YouTube<br>- ` facebook_page `: Facebook Page<br>- ` instagram `: Instagram<br>- ` linked_in `: LinkedIn<br>- ` thread `: Threads<br>- ` pinterest `: Pinterest<br>- ` vk `: VK<br>- ` bluesky `: Bluesky<br>- ` bilibili `: BiliBili<br>- ` tiktok_shop_creator `: TikTok Shop creator account<br>- ` tiktok_shop`: TikTok Shop seller account |
| state_dev | Optional | string | Custom parameter that can contain a user ID from your platform. It is included in the authorization URL and returned on success to identify the user who granted access. |

### Request Example

```json
{
    "team_id": "xxxxxx",
    "media_type": "instagram",
    "state_dev": "xxxxxx"
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| oauth_url | string | Full authorization URL |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "oauth_url": "https://xxxxxx"
    }
}
```

### Handle Authorization Callbacks

After authorization, the browser redirects to the callback URL configured in the dashboard with the following URL parameters.

| Parameter | Example Value | Description |
| --- | --- | --- |
| media_ids | `["22xxxxx"]` | Returned on success. A URL-encoded array of media IDs, for example `["22xxxxx"]`.Platforms such as Facebook can return multiple IDs, for example `["11xxx","22xxx"]`. |
| media_type | `tiktok_business` | Media type. |
| state_dev | `xxxxxx` | URL-encoded custom parameter. |
| error_code | `SYSTEM_ERROR ` | Returned when authorization fails.` SYSTEM_ERROR ` indicates a system error. Contact your administrator.` NO_AVAILABLE_MEDIA` indicates that no media account is available for authorization. |

#### Successful Authorization Redirect Example

```text
https://xxxxxx
```

After successful authorization, use `state_dev ` and ` media_ids` to link the new media account to the user. Then call List Accounts to retrieve details such as avatar, name, and follower count.

#### Failed Authorization Redirect Example

```text
https://xxxxxx
```

If authorization fails, use `error_code` to show the user an error and guide them through retrying authorization.
