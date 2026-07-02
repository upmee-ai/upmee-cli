---
name: upmee
description: upmee OpenAPI intelligent task execution — describe what you need in natural language, and the skill automatically calls the right endpoints to manage accounts, publish content (including video upload), handle comments, direct messages, analytics, and more.
---

# upmee Task Execution

## How to Use

```
/upmee <describe what you want to do in natural language>
```

Examples:
- `/upmee List all bound TikTok accounts`
- `/upmee Publish /Users/me/video.mp4 to TikTok with title "Summer Scenery"`
- `/upmee Check the status of publishing tasks from the last 7 days`
- `/upmee List comments on item_id xxx`

## Execution Principle

> The user describing a task implies authorization to execute it. **Complete all steps directly (read config, load docs, make HTTP requests) without asking "should I continue?" or "please confirm" mid-flow. Only pause if a required parameter is missing or an error occurs.**

---

## Step 1: Load Config

Read the local config file for the API Key and defaults:

**macOS / Linux**:
```bash
cat ~/.upmee/config.json
```

**Windows (PowerShell)**:
```powershell
Get-Content "$env:USERPROFILE\.upmee\config.json" | ConvertFrom-Json
```

**Windows (cmd)**:
```cmd
type %USERPROFILE%\.upmee\config.json
```

If the config file does not exist, tell the user to run `/upmee_setup <api_key>` first.

Extract from config:
- `api_key`: authentication credential for all requests
- `base_url`: defaults to `https://www.upmee.cc`
- `team_id`: default team ID (user-specified team_id in the prompt takes priority)
- `os`: operating system type, determines which HTTP tool to use

---

## Step 2: Understand Intent and Match Endpoint

Based on the user's natural language, determine which operation type applies:

| User intent keywords | Operation | Needs team_id |
|---|---|---|
| list accounts, bound accounts, account list | Account management → `media.md` | ✅ |
| delete account, unbind account | Account management → `media.md` | ✅ |
| get auth URL, authorize, bind new account | Account management → `media.md` | ✅ |
| trending music, background music | Account management → `media.md` | ✅ |
| publish video, publish image post, create task | Publishing → `task.md` (includes upload) | ✅ |
| check task, task status, publish history | Publishing → `task.md` | ✅ |
| Bilibili category | Publishing → `task.md` | ✅ |
| Pinterest board | Publishing → `task.md` | ✅ |
| comment list, view comments | Comment management → `comment.md` | ✅ |
| reply to comment | Comment management → `comment.md` | ✅ |
| delete comment | Comment management → `comment.md` | ✅ |
| analytics, stats, views, likes | Analytics → `stat.md` | ✅ |
| DM, conversation list, messages | Direct messages → `message.md` | ✅ |
| send DM, reply DM | Direct messages → `message.md` | ✅ |
| TikTok Shop, shop products | Shop tasks → `shop.md` | ✅ |

If the intent is unclear, ask the user:
> "What would you like to do? For example: list accounts, publish content, view comments, check messages, etc."

---

## Step 3: Load the Domain Doc

Read the doc from the repo's `docs/open_api_guide/` directory:

```
docs/open_api_guide/<domain>.md
```

**macOS / Linux**:
```bash
cat docs/open_api_guide/<domain>.md
```

**Windows (PowerShell)**:
```powershell
Get-Content "docs\open_api_guide\<domain>.md"
```

Domain to filename: `media` → `media.md`, `task` → `task.md`, etc.

If the file is not found, tell the user:
> "API docs not found. Make sure you launched Claude Code from the upmee-cli repo directory, then run `git pull` to ensure docs are up to date."

---

## Step 4: Collect Required Parameters

Check whether the user's description provides all required parameters per the domain doc:

**Already provided → use directly**

**Missing required parameter → ask the user**, for example:
- Missing team_id: ask for the team ID
- Missing media_ids: offer to list bound accounts first
- Missing file path: ask for the full local path to the video/image file

**Optional parameters with defaults → use defaults silently**

---

## Step 5: Execute HTTP Request

### Standard JSON request (most endpoints)

**macOS / Linux**:
```bash
curl -s -X POST "<base_url><path>" \
  -H "API-Key: <api_key>" \
  -H "Content-Type: application/json" \
  -d '<JSON body>'
```

**Windows (curl.exe)**:
```cmd
curl.exe -s -X POST "<base_url><path>" -H "API-Key: <api_key>" -H "Content-Type: application/json" -d "<JSON body (escape double quotes)>"
```

**Windows (PowerShell, when curl is unavailable)**:
```powershell
$body = '<JSON body>'
$resp = Invoke-RestMethod -Method POST -Uri "<base_url><path>" `
  -Headers @{"API-Key"="<api_key>"} `
  -Body $body -ContentType "application/json"
$resp | ConvertTo-Json -Depth 10
```

Parse the response JSON:
- `code=0`: success — extract and present the `data` field
- `code!=0`: failure — report the `msg` field as the error reason

---

## Step 6 (Upload + Publish flow): File Upload

**Only execute this step when the user wants to publish a video or images.**

### 6.1 Get file info

**macOS / Linux**:
```bash
stat -c%s "<file_path>"    # Linux
stat -f%z "<file_path>"    # macOS
```

**Windows (PowerShell)**:
```powershell
(Get-Item "<file_path>").Length
```

### 6.2 Calculate part count

Recommended part size: 10MB (10485760 bytes).

```
parts = ceil(file_size / 10485760)
If file_size ≤ 50MB → single-file upload is also available
If file_size > 50MB → must use multipart upload
```

### 6.3a Multipart upload (file > 50MB or preferred method)

**Step 1: Init (JSON — AI can call directly)**

```bash
curl -s -X POST "<base_url>/open_api/tool/s3/upload/v2/multipart/init" \
  -H "API-Key: <api_key>" \
  -H "Content-Type: application/json" \
  -d '{"total_parts": <part_count>}'
```

Save the returned `upload_token`.

**Step 2: Upload parts (multipart/form-data — user must run in terminal)**

> ⚠️ Part uploads involve binary file splitting and must be run in the user's local terminal. Show the following commands and ask the user to run each one.

**macOS / Linux (per part)**:
```bash
dd if="<file_path>" bs=10485760 skip=$((N-1)) count=1 2>/dev/null | \
curl -s -X POST "<base_url>/open_api/tool/s3/upload/v2/multipart" \
  -H "API-Key: <api_key>" \
  -F "upload_token=<upload_token>" \
  -F "part_number=<N>" \
  -F "file=@-;type=application/octet-stream"
```

**Windows (PowerShell, per part)**:
```powershell
$chunkSize = 10485760
$offset = ($N - 1) * $chunkSize
$bytes = [System.IO.File]::ReadAllBytes("<file_path>")
$chunk = $bytes[$offset..([Math]::Min($offset + $chunkSize - 1, $bytes.Length - 1))]
$tmpFile = "$env:TEMP\upmee_chunk_$N.bin"
[System.IO.File]::WriteAllBytes($tmpFile, $chunk)
curl.exe -s -X POST "<base_url>/open_api/tool/s3/upload/v2/multipart" `
  -H "API-Key: <api_key>" `
  -F "upload_token=<upload_token>" `
  -F "part_number=<N>" `
  -F "file=@$tmpFile"
Remove-Item $tmpFile
```

If the part count is large (> 5 parts), generate a complete script file for the user to run all parts at once.

**Step 3: Complete (JSON — AI can call directly)**

```bash
curl -s -X POST "<base_url>/open_api/tool/s3/upload/v2/multipart/complete" \
  -H "API-Key: <api_key>" \
  -H "Content-Type: application/json" \
  -d '{"upload_token": "<upload_token>"}'
```

Save the returned `object_id`.

### 6.3b Single-file upload (file ≤ 50MB)

> ⚠️ Also binary upload — show the command and ask the user to run it.

**macOS / Linux**:
```bash
curl -s -X POST "<base_url>/open_api/tool/s3/upload/v2/single" \
  -H "API-Key: <api_key>" \
  -F "type=<video|cover|image>" \
  -F "file=@<file_path>"
```

**Windows (curl.exe)**:
```cmd
curl.exe -s -X POST "<base_url>/open_api/tool/s3/upload/v2/single" -H "API-Key: <api_key>" -F "type=<video|cover|image>" -F "file=@<file_path>"
```

Save the returned `object_id`.

### 6.4 Create publish task with object_id

```bash
curl -s -X POST "<base_url>/open_api/media/task/create/v2" \
  -H "API-Key: <api_key>" \
  -H "Content-Type: application/json" \
  -d '{
    "team_id": <team_id>,
    "media_ids": [<media_id1>, <media_id2>],
    "video_id": "<object_id>",
    "pub_now": true,
    "title": "<title>",
    "common_data": {"desc": "<description>"}
  }'
```

---

## Step 7: Present Results

Summarize the API response in a clear, user-friendly way in the same language the user used.

On success: confirm the operation succeeded and highlight the key data returned (e.g. account count and names, task ID, publish target, etc.).

On failure: report the error from the `msg` field and suggest next steps where possible.

For paginated data: show the current page results and ask whether to load the next page if more data exists.

---

## Special Handling

**team_id not in config**:
1. Extract from user's description if mentioned (e.g. "team 123", "team_id 456")
2. If not provided, ask the user to provide it
3. After a successful task, ask if they want to save it as the default team_id

**Multi-account publishing**:
- If no accounts specified, list bound accounts first so the user can choose
- Confirm target accounts before publishing

**Binary upload note**:
- Multipart and single-file uploads require the user to run commands in their local terminal
- Generate the complete commands; the user copies them to the terminal and pastes the output back
- If the AI has Bash tool access and the file path is accessible, execute directly without user intervention

**Windows path compatibility**:
- Windows paths use backslashes (`\`), which PowerShell usually handles fine
- When passing paths to curl in cmd, wrap paths containing spaces in double quotes
- Recommend using forward slashes (`/`) or quoting paths