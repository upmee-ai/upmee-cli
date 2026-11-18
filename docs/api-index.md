# UPMee API endpoint index

Each operation links to its bundled English API reference. Check the [live API documentation](https://www.upmee.cc/developers/document/) for changes since this snapshot.

## Basics - Account Authorization

| Operation | Method | Path |
| --- | --- | --- |
| [Generate an Authorization URL](reference/media-oauth.md) | `POST` | `/open_api/media/oauth` |
| [Unlink Media Accounts](reference/media-delete.md) | `POST` | `/open_api/media/delete` |

## Basics - Account Management

| Operation | Method | Path |
| --- | --- | --- |
| [List Accounts](reference/media-list.md) | `POST` | `/open_api/media/list` |

## Basics - File Management

| Operation | Method | Path |
| --- | --- | --- |
| [Initialize a Multipart Upload](reference/tool-s3-upload-v2-multipart-init.md) | `POST` | `/open_api/tool/s3/upload/v2/multipart/init` |
| [Upload a File Part](reference/tool-s3-upload-v2-multipart.md) | `POST` | `/open_api/tool/s3/upload/v2/multipart` |
| [Complete a Multipart Upload](reference/tool-s3-upload-v2-multipart-complete.md) | `POST` | `/open_api/tool/s3/upload/v2/multipart/complete` |
| [Upload a Single File](reference/tool-s3-upload-v2-single.md) | `POST` | `/open_api/tool/s3/upload/v2/single` |

## Social Media - Content Management

| Operation | Method | Path |
| --- | --- | --- |
| [Create a Video Publishing Task (Social Media)](reference/media-task-create-v2.md) | `POST` | `/open_api/media/task/create/v2` |
| [Update a Video Publishing Task (Social Media)](reference/media-task-update.md) | `POST` | `/open_api/media/task/update` |
| [Create an Image Publishing Task (Social Media)](reference/media-task-create-image.md) | `POST` | `/open_api/media/task/create/image` |
| [Update an Image Publishing Task (Social Media)](reference/media-task-update-image.md) | `POST` | `/open_api/media/task/update/image` |
| [List Publishing Tasks (Social Media)](reference/media-task-list.md) | `POST` | `/open_api/media/task/list` |
| [List Account Videos (Social Media)](reference/media-item-list.md) | `POST` | `/open_api/media/item/list` |
| [List Trending TikTok Music](reference/media-popular_tracks-list.md) | `POST` | `/open_api/media/popular_tracks/list` |
| [Search Trending TikTok Music](reference/media-popular_tracks-search.md) | `POST` | `/open_api/media/popular_tracks/search` |
| [Search TikTok Post Locations](reference/media-task-tiktok-location-list.md) | `POST` | `/open_api/media/task/tiktok/location/list` |
| [List Pinterest Boards](reference/media-task-pinterest-boards-list.md) | `POST` | `/open_api/media/task/pinterest/boards/list` |
| [Get BiliBili Category IDs](reference/media-task-bilibili-type-list.md) | `POST` | `/open_api/media/task/bilibili/type/list` |

## Social Media - Comment Management

| Operation | Method | Path |
| --- | --- | --- |
| [List Comments](reference/media-item-comment-list.md) | `POST` | `/open_api/media/item/comment/list` |
| [List Comment Replies](reference/media-item-comment-reply-list.md) | `POST` | `/open_api/media/item/comment/reply/list` |
| [Reply to a Comment](reference/media-item-comment-reply.md) | `POST` | `/open_api/media/item/comment/reply` |
| [Delete a Comment](reference/media-item-comment-del.md) | `POST` | `/open_api/media/item/comment/del` |

## Social Media - Direct Message Management

| Operation | Method | Path |
| --- | --- | --- |
| [List Direct Message Conversations](reference/instant_messages-conversation-list.md) | `POST` | `/open_api/instant_messages/conversation/list` |
| [List Messages in a Conversation](reference/instant_messages-message-list.md) | `POST` | `/open_api/instant_messages/message/list` |
| [Send a Direct Message](reference/instant_messages-message-send.md) | `POST` | `/open_api/instant_messages/message/send` |
| [Check Media Accounts for Unread Messages](reference/instant_messages-media-badge.md) | `POST` | `/open_api/instant_messages/media/badge` |

## Social Media - Customer Management

| Operation | Method | Path |
| --- | --- | --- |
| [Create a Customer](reference/customer-create.md) | `POST` | `/open_api/customer/create` |
| [Update Customer Information](reference/customer-update.md) | `POST` | `/open_api/customer/update` |
| [List Customers](reference/customer-list.md) | `POST` | `/open_api/customer/list` |

## Social Media - Analytics

| Operation | Method | Path |
| --- | --- | --- |
| [Query Performance Data (Social Media)](reference/stat-detail.md) | `POST` | `/open_api/stat/detail` |
| [Query Traffic Reports (Social Media)](reference/stat-traffic_analysis.md) | `POST` | `/open_api/stat/traffic_analysis` |

## Shop - Product Management

| Operation | Method | Path |
| --- | --- | --- |
| [List Showcase Products](reference/shop-showcase_product-list.md) | `POST` | `/open_api/shop/showcase_product/list` |
| [Add Products to a Showcase](reference/shop-product-add.md) | `POST` | `/open_api/shop/product/add` |
| [Remove Products from a Showcase](reference/shop-product-remove.md) | `POST` | `/open_api/shop/product/remove` |
| [Get Product Details](reference/shop-product-detail.md) | `POST` | `/open_api/shop/product/detail` |
| [List Products in Shops Linked to Official or Marketing Accounts](reference/shop-product-list-shop.md) | `POST` | `/open_api/shop/product/list/shop` |
| [List Product Marketplace Products](reference/shop-product-list-open_collaboration.md) | `POST` | `/open_api/shop/product/list/open_collaboration` |
| [Look Up Products by ID in Bulk](reference/shop-product-list-open_collaboration-by_ids.md) | `POST` | `/open_api/shop/product/list/open_collaboration/by_ids` |

## Shop - Content Management

| Operation | Method | Path |
| --- | --- | --- |
| [Create a Shoppable Video Task (Shop)](reference/shop-task-create.md) | `POST` | `/open_api/shop/task/create` |
| [Update a Shoppable Video Task (Shop)](reference/shop-task-update.md) | `POST` | `/open_api/shop/task/update` |
| [Create a Shoppable Photo Post Task (Shop)](reference/shop-task-create-image.md) | `POST` | `/open_api/shop/task/create/image` |
| [Update a Shoppable Photo Post Task (Shop)](reference/shop-task-update-image.md) | `POST` | `/open_api/shop/task/update/image` |
| [List Publishing Tasks (Shop)](reference/shop-task-list.md) | `POST` | `/open_api/shop/task/list` |
| [List Account Videos (Shop)](reference/shop-item-list.md) | `POST` | `/open_api/shop/item/list` |

## Shop - Order Management

| Operation | Method | Path |
| --- | --- | --- |
| [List Affiliate Orders](reference/shop-affiliate-order-list.md) | `POST` | `/open_api/shop/affiliate/order/list` |
| [Get Affiliate Order Details](reference/shop-affiliate-order-info.md) | `POST` | `/open_api/shop/affiliate/order/info` |

## Shop - Analytics

| Operation | Method | Path |
| --- | --- | --- |
| [Query Performance Data (Shop)](reference/stat-shop-detail.md) | `POST` | `/open_api/stat/shop/detail` |

## Social Media - Spark Ads Authorization Management

| Operation | Method | Path |
| --- | --- | --- |
| [List TikTok Spark Ads Authorization Tasks](reference/media-post-authorize-task-list.md) | `POST` | `/open_api/media/post/authorize/task/list` |
| [Create a TikTok Spark Ads Authorization Task](reference/media-post-authorize-task-create.md) | `POST` | `/open_api/media/post/authorize/task/create` |
| [Delete a TikTok Spark Ads Authorization Task](reference/media-post-authorize-task-delete.md) | `POST` | `/open_api/media/post/authorize/task/delete` |

## Tools - AI Content Generation

| Operation | Method | Path |
| --- | --- | --- |
| [List AI Generation Tasks](reference/ai-generation-task-list.md) | `POST` | `/open_api/ai/generation/task/list` |
| [Create an AI Video Generation Task](reference/ai-generation-task-create-video.md) | `POST` | `/open_api/ai/generation/task/create/video` |
| [Create an AI Image Generation Task](reference/ai-generation-task-create-image.md) | `POST` | `/open_api/ai/generation/task/create/image` |
| [Create a Viral Video Replication Task](reference/ai-generation-task-create-video_replicate.md) | `POST` | `/open_api/ai/generation/task/create/video_replicate` |
| [Create a Viral Cover Image Generation Task](reference/ai-generation-task-create-hot_cover.md) | `POST` | `/open_api/ai/generation/task/create/hot_cover` |
| [Create an Image Background Removal Task](reference/ai-generation-task-create-background_remove.md) | `POST` | `/open_api/ai/generation/task/create/background_remove` |
| [Create an Image Upscaling Task](reference/ai-generation-task-create-image_upscale.md) | `POST` | `/open_api/ai/generation/task/create/image_upscale` |
| [Create an Image-to-SVG Task](reference/ai-generation-task-create-image_to_svg.md) | `POST` | `/open_api/ai/generation/task/create/image_to_svg` |
| [Create a Text-to-Speech Task](reference/ai-generation-task-create-text_to_speech.md) | `POST` | `/open_api/ai/generation/task/create/text_to_speech` |
| [List Voices](reference/ai-generation-voice-list.md) | `POST` | `/open_api/ai/generation/voice/list` |

## Tools - Automation

| Operation | Method | Path |
| --- | --- | --- |
| [Create a Knowledge Base](reference/ai-knowledge_base-create.md) | `POST` | `/open_api/ai/knowledge_base/create` |
| [Update a Knowledge Base](reference/ai-knowledge_base-update.md) | `POST` | `/open_api/ai/knowledge_base/update` |
| [Delete a Knowledge Base](reference/ai-knowledge_base-delete.md) | `POST` | `/open_api/ai/knowledge_base/delete` |
| [List Knowledge Bases](reference/ai-knowledge_base-list.md) | `POST` | `/open_api/ai/knowledge_base/list` |
| [Get Knowledge Base Details](reference/ai-knowledge_base-detail.md) | `POST` | `/open_api/ai/knowledge_base/detail` |
| [Create a Comment Auto-Reply Rule](reference/comment-reply-strategy-create.md) | `POST` | `/open_api/comment/reply/strategy/create` |
| [Update a Comment Auto-Reply Rule](reference/comment-reply-strategy-update.md) | `POST` | `/open_api/comment/reply/strategy/update` |
| [Delete a Comment Auto-Reply Rule](reference/comment-reply-strategy-delete.md) | `POST` | `/open_api/comment/reply/strategy/delete` |
| [List Comment Auto-Reply Rules](reference/comment-reply-strategy-list.md) | `POST` | `/open_api/comment/reply/strategy/list` |
| [Create a Comment Auto-Delete Rule](reference/comment-delete-strategy-create.md) | `POST` | `/open_api/comment/delete/strategy/create` |
| [Update a Comment Auto-Delete Rule](reference/comment-delete-strategy-update.md) | `POST` | `/open_api/comment/delete/strategy/update` |
| [Delete a Comment Auto-Delete Rule](reference/comment-delete-strategy-delete.md) | `POST` | `/open_api/comment/delete/strategy/delete` |
| [List Comment Auto-Delete Rules](reference/comment-delete-strategy-list.md) | `POST` | `/open_api/comment/delete/strategy/list` |
| [Create a Direct Message Auto-Reply Rule](reference/private_message-auto-reply-strategy-create.md) | `POST` | `/open_api/private_message/auto-reply/strategy/create` |
| [Update a Direct Message Auto-Reply Rule](reference/private_message-auto-reply-strategy-update.md) | `POST` | `/open_api/private_message/auto-reply/strategy/update` |
| [Delete a Direct Message Auto-Reply Rule](reference/private_message-auto-reply-strategy-delete.md) | `POST` | `/open_api/private_message/auto-reply/strategy/delete` |
| [List Direct Message Auto-Reply Rules](reference/private_message-auto-reply-strategy-list.md) | `POST` | `/open_api/private_message/auto-reply/strategy/list` |
