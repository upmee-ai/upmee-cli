# Check Media Accounts for Unread Messages

This endpoint allows **up to 120 requests per minute per API key** and returns only valid media accounts you have permission to access. If you poll to decide whether to show an unread indicator, follow these guidelines:

1. Set a polling interval of **at least 60 seconds**.

2. Stop polling after **more than 5 minutes of user inactivity** to avoid unnecessary requests and resource use.

### Request URL

`https://www.upmee.cc/open_api/instant_messages/media/badge`

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
| team_id | Required | string | Team ID |
| media_ids | Required | string[] | Media account IDs to check |

### Request Example

```bash
curl --location 'https://xxxxxx' \
    --header 'API-KEY: {xxxxxx}' \
    --header 'Content-Type: application/json' \
    --data '{
    "team_id": "{{team_id}}",
    "media_ids": [
        {{media_id_0}},
        {{media_id_1}},
        {{media_id_2}}
    ]
}'
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| media_badge | map\<string,bool\> | Result by media account ID.<br>- Key: Media account ID<br>- Value: Whether the account has unread messages |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "media_badge": {
            "1673527913": false,
            "1677653157": false,
            "5": false,
            "5782": true,
            "6": false
        }
    }
}
```
