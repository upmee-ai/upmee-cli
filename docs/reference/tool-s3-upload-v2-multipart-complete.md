# Complete a Multipart Upload

### Request URL

`https://www.upmee.cc/open_api/tool/s3/upload/v2/multipart/complete`

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
| upload_token | Required | string | Upload token returned by the multipart upload initialization endpoint |

### Request Example

```json
{
    "upload_token": "{upload_token}"
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| object_id | string | File ID |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "{request_id}",
    "data": {
        "object_id": "{object_id}"
    }
}
```
