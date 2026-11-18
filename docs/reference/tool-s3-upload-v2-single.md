# Upload a Single File

Use this endpoint to upload smaller files, such as covers or videos under 40 MB, without splitting them into parts.

### Request URL

`https://www.upmee.cc/open_api/tool/s3/upload/v2/single`

### HTTP Method

`POST`

### Request Headers

<!-- api-fields -->

| Field | Required <!-- api-tag --> | Type | Description |
| --- | --- | --- | --- |
| API-Key | Required | string | API key |
| Content-Type | Required | string | Form data content type. Allowed value:<br>`multipart/form-data` |

### Request Parameters

<!-- api-fields -->

| Field | Required <!-- api-tag --> | Type | Description |
| --- | --- | --- | --- |
| type | Required | text | File type<br>- `video `: Video asset for a video post<br>- ` cover `: Cover image for a video<br>- ` image `: Image asset for a photo post<br>> Endpoint notes<br>><br>><br>Single-file uploads have the following limits:<br>- Maximum video size **40MB**，Allowed formats:` mp4` ` mov ` ` webm `<br>- Maximum cover size **5MB**,Allowed formats: ` png ` ` jpeg ` ` jpg` |
| file | Required | file | Video or cover file |

### Request Example

|Key||Value|
|---|---|---|
|type|Text|video|
|file|File|xxxxxx|

```bash
curl --location 'https://xxxxxx' \
    --header 'API-KEY: xxxxxx' \
    --form 'type="video"' \
    --form 'file=@"xxxxxx"'
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| object_id | string | Object ID (`object_id`) of the uploaded video or cover. Use this ID in subsequent calls. |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "object_id": "xxxxxx"
    }
}
```
