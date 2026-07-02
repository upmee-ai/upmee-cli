---
name: upmee_setup
description: upmee OpenAPI one-time initialization — saves your API Key to a local config file and verifies connectivity. After setup, use /upmee to execute any task.
---

# upmee Setup

## How to Use

```
/upmee_setup <your-API-Key> [team_id]
```

- `API-Key`: required — obtain from upmee platform → Developer Settings → API Key Management → Create
- `team_id`: optional — default team ID, can be updated later

---

## Execution Principle

> Running `/upmee_setup` implies authorization to complete all initialization steps. **Execute all steps directly without asking "should I continue?" or "should I save this?" — only pause if an error occurs.**

## Steps

### Step 1: Detect OS and Tools

Run the following command to detect the current environment:

```bash
uname -s 2>/dev/null || echo "Windows"
```

- Output contains `Darwin` → macOS
- Output contains `Linux` → Linux
- Command fails or outputs `Windows` → Windows

Also check whether curl is available:

```bash
curl --version 2>&1 | head -1
```

- **macOS / Linux**: use system `curl`
- **Windows**: Windows 10+ ships with `curl.exe`, available in both PowerShell and cmd. If unavailable, use PowerShell's `Invoke-RestMethod`

Record the detected results for use in later steps.

---

### Step 2: Create Config Directory and File

**macOS / Linux**:
```bash
mkdir -p ~/.upmee
```

**Windows (PowerShell)**:
```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\.upmee"
```

Write the following to the config file:

- macOS/Linux path: `~/.upmee/config.json`
- Windows path: `%USERPROFILE%\.upmee\config.json`

```json
{
  "api_key": "<user-provided API Key>",
  "team_id": <user-provided team_id or null>,
  "base_url": "https://www.upmee.cc",
  "os": "<detected OS>",
  "setup_time": "<current time>"
}
```

**Write command (macOS/Linux)**:
```bash
cat > ~/.upmee/config.json << 'EOF'
{content}
EOF
```

**Write command (Windows PowerShell)**:
```powershell
'{content}' | Out-File -FilePath "$env:USERPROFILE\.upmee\config.json" -Encoding UTF8
```

---

### Step 3: Verify API Key

Send a minimal account list request (page_size=1) to verify the key is valid.

**macOS / Linux**:
```bash
curl -s -w "\n%{http_code}" \
  -X POST https://www.upmee.cc/open_api/media/list \
  -H "API-Key: <api_key>" \
  -H "Content-Type: application/json" \
  -d '{"page":1,"page_size":1,"team_id":0}'
```

**Windows (curl.exe)**:
```cmd
curl.exe -s -w "\n%{http_code}" -X POST https://www.upmee.cc/open_api/media/list -H "API-Key: <api_key>" -H "Content-Type: application/json" -d "{\"page\":1,\"page_size\":1,\"team_id\":0}"
```

**Windows (PowerShell, when curl is unavailable)**:
```powershell
$resp = Invoke-RestMethod -Method POST -Uri "https://www.upmee.cc/open_api/media/list" `
  -Headers @{"API-Key"="<api_key>"} `
  -Body '{"page":1,"page_size":1,"team_id":0}' `
  -ContentType "application/json"
$resp | ConvertTo-Json
```

**Interpret the result**:
- HTTP 200 and `code=0` → API Key valid, initialization successful
- HTTP 200 and `code!=0` (e.g. team not found) → API Key itself is valid; team_id can be confirmed later
- HTTP 401 → API Key invalid — check if it was copied correctly
- Connection failure → network issue — check connectivity

---

### Step 4: Show Completion Summary

Display the following to the user:

```
Setup complete!

Config:
  API Key:   <first 8 chars>**** (saved securely)
  Base URL:  https://www.upmee.cc
  OS:        <detected OS>
  Config:    <config file path>
  API Docs:  bundled in this repo at docs/open_api_guide/

You can now use /upmee to run tasks, for example:
  "List all bound accounts"
  "Publish a video to TikTok"
  "Check recent publishing task status"

To get the latest API docs, run: git pull
```

If `team_id` was not provided:
```
Note: No default team_id set. For endpoints that require one, include it in your request description, e.g.:
  "List accounts for team_id 12345"
```

---

## Notes

- The API Key is stored in plain text in the local config file — do not share it
- To replace the API Key, re-run `/upmee_setup <new-key>` to overwrite
- The config file stays on your machine and is never uploaded to any server
- API docs are included in this repo — run `git pull` to get updates