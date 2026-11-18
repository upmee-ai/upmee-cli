# Initialize a Multipart Upload

Use multipart upload for videos over 40 MB. Initialize the upload with this endpoint to obtain an upload_token, then pass that token to Upload a File Part. Each video must be no larger than 2 GB.

### Request URL

`https://www.upmee.cc/open_api/tool/s3/upload/v2/multipart/init`

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
| total_parts | Required | string | Number of parts<br>> Parameter notes<br>> <br>> <br>Part size limits: each part must be between **5 MB** and **20 MB**, with **up to 10,000 parts**.<br>- Use a consistent part size of 10 MB for video uploads, except for the last part.<br>- Keep the parts the same size except for the final part. For example, for four parts the sizes must satisfy `1=2=3>4` |

### Request Example

```json
{
    "total_parts": 3
}
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| upload_token | string | Upload token used to upload parts, complete a multipart upload, or upload a single file |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "upload_token": "xxxxxx"
    }
}
```
