# Upload a File Part

### Request URL

`https://www.upmee.cc/open_api/tool/s3/upload/v2/multipart`

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
| part_number | Required | int64 | Part number. Numbering starts at `1` and increases sequentially. The final number **must equal**`total_parts` |
| upload_token | Required | string | Upload token returned by the multipart upload initialization endpoint |
| file | Required | file | File part |

### Request Example

|Key||Value|
|---|---|---|
|Value|Type|Value|
|part\_number|text|1|
|upload\_token|text| xxxxxx |
|file|file||

```bash
curl --location 'https://xxxxxx' \
    --header 'API-KEY: xxxxxx' \
    --form 'upload_token="xxxxxx"' \
    --form 'part_number="1"' \
    --form 'file=@"xxxxxx"'
```

### Response Parameters

<!-- api-fields -->

| Field | Type | Description |
| --- | --- | --- |
| part_number | int64 | Part number |
| file_size | int64 | Part size |

### Response Example

```json
{
    "code": 0,
    "message": "OK",
    "request_id": "xxxxxx",
    "data": {
        "part_number": 1,
        "file_size": 10485760
    }
}
```
