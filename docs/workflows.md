# UPMee workflows

- **Account lookup.** Ask to list connected accounts for the selected team. Use the resulting account IDs in subsequent operations.
- **Video publishing.** Identify the destination and asset, upload the file using its documented flow, then submit a publishing task. Save the returned task ID and use the batching workflow below to check its status.
- **Affiliate orders.** List orders for the chosen time range. Follow the documented pagination fields and retrieve details for specific order IDs when needed.
- **AI content generation.** Select the relevant creation endpoint, validate model-specific constraints, submit the task, and use the returned task identifier to check the result.

Look up each operation in the [endpoint index](api-index.md) and load its current English contract before making requests.

## API best practices

- **Fetch every account page and match the account type.** When calling `POST /open_api/media/list` for a complete account list, follow the documented pagination through `total_page`. Match both `business_type` and `media_type` against the target endpoint. Use a social media account (`video`) for social video publishing and a supported shop account (`shop`) for Shop API operations. TikTok social accounts (`tiktok_business`), TikTok Shop creator accounts (`tiktok_shop_creator`), TikTok Shop store accounts (`tiktok_shop`), and TikTok ad accounts (`tiktok_advertise`, business type `advertise`) serve different endpoints.
- **Limit request rates.** Keep total API traffic across concurrent calls in the workflow at or below 5 requests per second (QPS) by default. Follow any stricter endpoint limit. Leave at least 10 seconds between publishing status requests.
- **Check publishing status in batches.** On successful submission, record the task ID and submission time. Once each task is at least 5 minutes old, group eligible IDs by team and module and pass them as `task_ids` to the Social Media or Shop publishing task list endpoint. Include multiple IDs per request, up to 20, and use the documented pagination settings to fit the batch results on one page where possible. If only one ID is eligible, hold it for a batch with another eligible ID in the same group. After the first check, queue only tasks still under review and wait at least another 5 minutes before rechecking. Check each ID at most twice. If a task is still under review after the second check, report its latest status and stop polling it.

## Data retrieval and sync

1. **Filter videos by publication time.** For routine video analytics and comment syncs, focus on videos published in the past four days. Where supported, pass that publication-time range in the request. Otherwise, identify eligible video IDs first and query them in batches. Widen the window for backfills or active monitoring of older videos.
2. **Batch video and task lookups.** Pass video IDs or task IDs explicitly. Group IDs by team and endpoint and send multiple IDs per request within the documented batch limit. Follow the publishing status workflow above for newly submitted tasks.
3. **Space analytics syncs more than 60 minutes apart.** UPMee updates analytics hourly. Schedule recurring syncs for the same scope more than 60 minutes apart. Share one sync job and reuse its results across consumers, prevent overlapping runs for the same scope, and stagger start times across teams.
4. **Fetch comments and direct messages incrementally.** Poll only the posts and conversations you need to monitor, and check inactive items less often. Use documented time filters or incremental sync options where available, and deduplicate by comment or message ID. Fetch replies or full conversation histories only when needed.
5. **Resume from the last successful checkpoint.** Save progress after processing each page or time window. Reuse cursors only when documented. If a cursor expires and time filtering is available, resume from the smallest relevant window. Schedule historical backfills separately from routine syncs.
6. **Limit request rates and retries.** Keep total API traffic at or below 5 QPS by default, including concurrent calls, and follow stricter endpoint limits. Fix invalid parameters, credentials, or permissions before retrying. For transient read failures, cap retries and increase delays with a small random offset. Honor any retry timing returned by the API.
7. **Verify uncertain write outcomes before resubmitting.** A publish, message, upload, or generation request may have been accepted even if it times out. Check through a documented lookup where available. If the outcome remains unknown, report it and stop automatic resubmission.
8. **Reuse uploaded assets and reference data.** Reuse valid file IDs where permitted. Cache account lists, boards, and categories within the relevant team or account scope. Refresh when authorization or configuration changes, or when the workflow needs current data.
9. **Set a stopping point for background monitoring.** Use the documented status lookup for AI generation and Spark Ads authorization tasks. Stop at a terminal state. Set a maximum number of checks or a time limit and report any tasks still pending at that limit.

## Check the latest online reference

If a request built from the bundled reference fails, consult the [live UPMee API documentation](https://www.upmee.cc/developers/document/). Use its directory to locate the same module and operation, select English, and read the latest method, URL, headers, request fields, required and conditional rules, types, enum values, and response structure. Use **Copy as Markdown** where available to load the complete reference.

Compare the live definition with the bundled file and adjust the request only where the current reference supports the change. For authentication, permissions, network errors, or rate limits, address the reported cause as well. Keep the existing rate limits and retry limits in effect.

For a failed read, retry the corrected request within the bounded retry policy. If a write timed out or its outcome is uncertain, reconcile it through a documented lookup before resubmitting. Report any remaining uncertainty. If the live reference cannot be accessed, ask the user for its Markdown and the redacted error response.

Summarize any contract differences that affected the call so the bundled reference can be updated.
