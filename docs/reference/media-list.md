# List Accounts

### Request URL

`https://www.upmee.cc/open_api/media/list`

### HTTP Method

`POST`

### Request Headers

<!-- api-fields -->

| Field | Required <!-- api-tag --> | Type | Description |
| --- | --- | --- | --- |
| API-Key | Required | string | API key |
| Content-Type | Required | string | Request content type.<br>Allowed format:`application/json`. |

### Request Parameters

<!-- api-fields -->

| Field | Required <!-- api-tag --> | Type | Description |
| --- | --- | --- | --- |
| page | Required | number | Current page.<br>Default:1.<br>Range:≥ 1 |
| page_siz | Required | number | Page size<br>Default:10.<br>Range:1\-20 |
| team_id | Required | string | Required team ID |
| media_ids | Required | string[] | Optional account filter. Specify up to 20 account IDs. |

### Request Example

```json
{
    "page": 1,
    "page_size": 1,
    "team_id": "xxxxxx",
    "media_types": [],
    "name": "",
    "valid": true
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| page | number | Page number of the returned results, usually starting at `1`  |
| page_size | number | Number of results per page. For example, `10` means 10 results per page. |
| total_size | number | Total number of results across all pages. For example, `100` means 100 results in total. |
| total_page | number | Total number of pages. For example, `10` means results extend through page 10. |
| list | MediaView[] | List containing multiple `MediaView` objects. Each entry represents a video or media record. |
| list.media_id | string | Media ID |
| list.media_type | MediaType | Media type<br>Social media<br>- `kuaishou`: Kuaishou<br>- `bilibili`: BiliBili<br>- `youtube`: YouTube<br>- `instagram`: Instagram<br>- `facebook_page`: Facebook<br>- `tiktok_business`: TikTok<br>- `linked_in`: LinkedIn<br>- `vk`: VK<br>- `thread`: Threads<br>- `pinterest`: Pinterest<br>- `bluesky`: Bluesky<br><br>&nbsp;<br>Shop<br>- `tiktok_shop_creator`: TikTok Shop creator account<br>- `tiktok_shop`: TikTok Shop seller account<br><br>&nbsp;<br>Advertising<br>- `tiktok_advertise`: TikTok advertising account |
| list.business_type | BusinessType | Account type<br>- `video `: Video account<br>- ` advertise `: Advertising account<br>- ` shop`: E-commerce or shop account |
| list.name | string | Nickname on the platform |
| list.username | string | Username on the platform |
| list.gender | string | Gender<br>- `male `: Male<br>- ` female `: Female<br>- ` unknown`: Other |
| list.avatar | string | Avatar URL |
| list.country | string | Country |
| list.province | string | Province |
| list.city | string | City |
| list.valid | bool | Whether the account is valid |
| list.fans | number | Follower count |
| list.remark | string | Remarks |
| list.create_time | number | Account linking timestamp\(milliseconds\) |

**MediaType**
Media type values

|Value|Description|
|---|---|
|kuaishou|Kuaishou|
|bilibili|BiliBili|
|youtube|YouTube|
|instagram|Instagram|
|facebook\_page|Facebook Page|
|tiktok\_business|TikTok|
|linked\_in|LinkedIn|
|vk|VK|
|thread|Threads|
|pinterest|Pinterest|
|bluesky|Bluesky|
|tiktok\_shop|TikTok Shop seller account|
|tiktok\_shop\_creator|TikTok Shop creator account|
|tiktok\_advertise|TikTok advertising account|

**BusinessType**

Account type

|Value|Description|
|---|---|
|video|Video account|
|advertise|Advertising account|
|shop|E-commerce or shop account|

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "page": 1,
        "page_size": 1,
        "total_size": 14,
        "total_page": 14,
        "list": [
            {
                "media_id": "xxxxxx",
                "media_type": "youtube",
                "business_type": "video",
                "name": "xxxxxx",
                "username": "",
                "gender": "unknown",
                "avatar": "https://xxxxxx",
                "country": "",
                "province": "",
                "city": "",
                "valid": true,
                "fans": 1,
                "ad_balance": 0,
                "create_time": 1719300000
            }
        ]
    }
}
```
