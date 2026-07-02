# upmee OpenAPI Index

> This document is intended for AI Agent use.
>
> **Authentication**: Add `API-Key: {your_key}` to every request header.
>
> **Base URL**: `https://api.upmee.cc`
>
> **Common response format**: `{"code": 0, "msg": "OK", "data": {...}}` — `code` non-zero means error, `msg` contains the reason.
>
> **Usage**: When you need full parameter details for an endpoint, load the linked domain doc before constructing the request.

---

## Account Management (media)

| Description | Path | Requires team_id | Details |
| :--- | :--- | :---: | :--- |
| List bound social media accounts | `POST /open_api/media/list` | ✅ | [media.md](media.md#list-accounts) |
| Delete a bound account | `POST /open_api/media/delete` | ✅ | [media.md](media.md#delete-account) |
| Get platform OAuth authorization URL | `POST /open_api/media/oauth` | ✅ | [media.md](media.md#get-oauth-url) |
| List TikTok trending background music | `POST /open_api/media/popular_tracks/list` | ✅ | [media.md](media.md#trending-music) |

## Publishing Tasks (task)

| Description | Path | Requires team_id | Details |
| :--- | :--- | :---: | :--- |
| Publish video to multiple accounts (recommended) | `POST /open_api/media/task/create/v2` | ✅ | [task.md](task.md#publish-video-v2) |
| Publish video to a single account (legacy) | `POST /open_api/media/task/create` | ✅ | [task.md](task.md#publish-video-v1) |
| Publish image post to accounts | `POST /open_api/media/task/create/image` | ✅ | [task.md](task.md#publish-image-post) |
| List publishing tasks | `POST /open_api/media/task/list` | ✅ | [task.md](task.md#list-tasks) |
| List Bilibili categories (required before publishing to Bilibili) | `POST /open_api/media/task/bilibili/type/list` | ✅ | [task.md](task.md#bilibili-categories) |
| List Pinterest boards (required before publishing to Pinterest) | `POST /open_api/media/task/pinterest/boards/list` | ✅ | [task.md](task.md#pinterest-boards) |

## Comment Management (comment)

| Description | Path | Requires team_id | Details |
| :--- | :--- | :---: | :--- |
| List comments on a post | `POST /open_api/media/item/comment/list` | ✅ | [comment.md](comment.md#list-comments) |
| List replies to a comment | `POST /open_api/media/item/comment/reply/list` | ✅ | [comment.md](comment.md#list-comment-replies) |
| Reply to a comment | `POST /open_api/media/item/comment/reply` | ✅ | [comment.md](comment.md#reply-to-comment) |
| Delete a comment (FB/IG/YouTube/Threads/VK/TikTok/LinkedIn) | `POST /open_api/media/item/comment/del` | ✅ | [comment.md](comment.md#delete-comment) |

## Analytics (stat)

| Description | Path | Requires team_id | Details |
| :--- | :--- | :---: | :--- |
| Query content analytics with multi-dimensional grouping (requires login session) | `POST /open_api/stat/detail` | ✅ | [stat.md](stat.md#content-analytics) |

## Direct Messages (message)

| Description | Path | Requires team_id | Details |
| :--- | :--- | :---: | :--- |
| List conversations for an account (rate limit: 20/min) | `POST /open_api/instant_messages/conversation/list` | ✅ | [message.md](message.md#list-conversations) |
| List messages in a conversation (rate limit: 20/min) | `POST /open_api/instant_messages/message/list` | ✅ | [message.md](message.md#list-messages) |
| Send a direct message | `POST /open_api/instant_messages/message/send` | ✅ | [message.md](message.md#send-message) |
| Get unread message badge counts for accounts (rate limit: 120/min) | `POST /open_api/instant_messages/media/badge` | ✅ | [message.md](message.md#message-badge) |

## TikTok Shop (shop)

> For TikTok Shop Creator accounts only.

| Description | Path | Requires team_id | Details |
| :--- | :--- | :---: | :--- |
| Create a shop video task | `POST /open_api/shop/task/create` | ✅ | [shop.md](shop.md#create-shop-video-task) |
| Create a shop image post task | `POST /open_api/shop/task/create/image` | ✅ | [shop.md](shop.md#create-shop-image-task) |
| List shop tasks | `POST /open_api/shop/task/list` | ✅ | [shop.md](shop.md#list-shop-tasks) |
| List products in a shop account | `POST /open_api/shop/showcase_product/list` | ✅ | [shop.md](shop.md#list-shop-products) |

## File Upload (upload)

> ⚠️ Upload flow: **init (JSON) → upload parts (multipart/form-data, direct HTTP) → complete (JSON)**.
> The AI can call init and complete; the part upload step must be performed by the caller directly via HTTP.

| Description | Path | Requires team_id | Details |
| :--- | :--- | :---: | :--- |
| Initialize multipart upload, get upload_token | `POST /open_api/tool/s3/upload/v2/multipart/init` | - | [upload.md](upload.md#init-multipart-upload) |
| Upload a single part (⚠️ multipart/form-data, not JSON) | `POST /open_api/tool/s3/upload/v2/multipart` | - | [upload.md](upload.md#upload-part) |
| Complete multipart upload, get object_id | `POST /open_api/tool/s3/upload/v2/multipart/complete` | - | [upload.md](upload.md#complete-multipart-upload) |
| Single-file upload (⚠️ multipart/form-data, not JSON, max 50MB) | `POST /open_api/tool/s3/upload/v2/single` | - | [upload.md](upload.md#single-file-upload) |