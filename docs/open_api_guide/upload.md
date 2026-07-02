# File Upload API

## Upload Flow

**Multipart upload** (recommended, supports up to 2GB): init → upload parts → complete — yields an `object_id`.

**Single-file upload** (max 50MB): one request, yields an `object_id` directly.

> Use the `object_id` as `video_id` or an element of `picture_ids` in publishing endpoints.

---

## Init Multipart Upload {#init-multipart-upload}

**Path** `POST /open_api/tool/s3/upload/v2/multipart/init`
**Auth** `API-Key: {your_key}`
**team_id** Not required
**Content-Type** `application/json`

### Request Parameters

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| total_parts | number | ✅ | Total number of parts, range 1–10000. Recommended 10MB per part; minimum 5MB, maximum 20MB (last part may be smaller than 5MB) |

> The token expires in 1 hour — re-initialize if it times out.

### Response

| Field | Type | Description |
| :--- | :--- | :--- |
| upload_token | string | Upload session token — required for subsequent part uploads and the complete call |

---

## Upload Part {#upload-part}

**Path** `POST /open_api/tool/s3/upload/v2/multipart`
**Auth** `API-Key: {your_key}`
**team_id** Not required
**Content-Type** `multipart/form-data`

> ⚠️ This endpoint transmits binary data — request format is `multipart/form-data`, not JSON.

### Request Parameters (Form Fields)

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| upload_token | string | ✅ | Token from the init endpoint |
| part_number | number | ✅ | Part sequence number, starting from 1, must not exceed `total_parts` |
| file | binary | ✅ | Part binary data, 5MB–20MB; last part may be smaller than 5MB |

> Deduplication supported — re-uploading an identical part returns success immediately without re-storing.

### Response

| Field | Type | Description |
| :--- | :--- | :--- |
| part_number | number | Successfully uploaded part number |
| file_size | number | Part size (bytes) |

---

## Complete Multipart Upload {#complete-multipart-upload}

**Path** `POST /open_api/tool/s3/upload/v2/multipart/complete`
**Auth** `API-Key: {your_key}`
**team_id** Not required
**Content-Type** `application/json`

> Call after all parts have been uploaded. The server merges the file and returns the final file ID. Returns an error if any parts are missing.

### Request Parameters

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| upload_token | string | ✅ | Token from the init endpoint |

### Response

| Field | Type | Description |
| :--- | :--- | :--- |
| object_id | string | File storage ID, format: `bucket-name/openapi/video/uuid` — use as `video_id` in publish endpoints |

---

## Single-File Upload {#single-file-upload}

**Path** `POST /open_api/tool/s3/upload/v2/single`
**Auth** `API-Key: {your_key}`
**team_id** Not required
**Content-Type** `multipart/form-data`

> ⚠️ This endpoint transmits binary data — request format is `multipart/form-data`, not JSON. Suitable for cover images, image post pictures, and other small files.

### Request Parameters (Form Fields)

| Field | Type | Required | Description |
| :--- | :--- | :---: | :--- |
| type | string | ✅ | File type: `video` (max 40MB) / `cover` cover image (max 5MB) / `image` image post picture (max 50MB) |
| file | binary | ✅ | File binary data |

### Response

| Field | Type | Description |
| :--- | :--- | :--- |
| object_id | string | File storage ID — use as `video_id` or an element of `picture_ids` in publish endpoints |