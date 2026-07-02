# upmee-open-agent

Call upmee APIs using natural language — no code, no API knowledge required.

This repo ships two Claude Code skill commands:

- `/upmee_setup`: one-time initialization — saves your API Key and verifies connectivity
- `/upmee`: describe what you need in natural language, and the AI handles the API calls

---

## What You Need

| Item | How to Get |
|---|---|
| [Claude Code](https://claude.ai/code) | Install and sign in |
| upmee API Key | Log in to upmee → Developer Settings → API Key Management → Create |
| team_id | Log in to upmee → Team Settings |

---

## Quick Start

### Step 1: Clone the repo

```bash
git clone https://github.com/dreamerainc/upmee-open-agent.git
cd upmee-open-agent
```

> Every time you use this tool, launch Claude Code from this directory so the skill commands are available.

### Step 2: Start Claude Code

```bash
claude
```

### Step 3: Initialize (one time only)

In the Claude Code chat, run:

```
/upmee_setup your-API-Key
```

If you already know your team ID, pass it too:

```
/upmee_setup your-API-Key 12345
```

When you see "Setup complete!", initialization is done. Your API Key is saved permanently on your machine — no need to re-run this.

### Step 4: Start using

```
/upmee List all bound accounts for team_id 12345
```

---

## Usage Examples

### List accounts

```
/upmee List all bound accounts for team_id 12345
```

### Publish a video

```
/upmee Publish /Users/me/Desktop/video.mp4 to TikTok with title "Summer Scenery", team_id 12345
```

### Check publishing task status

```
/upmee Show publishing tasks from the last 7 days, team_id 12345
```

### View and reply to comments

```
/upmee List comments on item_id 7xxx, team_id 12345
/upmee Reply to comment_id xxx on item_id 7xxx with "Thanks for the support!", team_id 12345
```

### Check direct messages

```
/upmee List the latest conversations for media_id 888, team_id 12345
```

---

## Daily Use

Each time you open a terminal, navigate to this repo before starting Claude Code:

```bash
cd upmee-open-agent
claude
```

No re-initialization needed — just describe your task.

---

## FAQ

**Q: `/upmee` command not recognized?**

The skill commands only work when Claude Code is launched from this repo directory. Verify:

```bash
# macOS / Linux
ls .claude/skills/upmee/SKILL.md

# Windows PowerShell
Test-Path ".\.claude\skills\upmee\SKILL.md"
```

If the file exists but the command is still not recognized, exit Claude Code and relaunch it from this directory.

---

**Q: `/upmee_setup` says my API Key is invalid?**

1. Make sure the key was copied in full with no extra spaces
2. Log in to upmee and confirm the key is active
3. Re-run `/upmee_setup your-new-API-Key`

---

**Q: Do I need to re-run `/upmee_setup` every time?**

No. Setup runs once; the config is saved permanently at `~/.upmee/config.json`.

---

**Q: The AI asks me to run a command manually when publishing a video — is that normal?**

Yes. Video uploads involve binary file transfer. The AI generates the full command; you copy it to your terminal, run it, then paste the output back. That's the only manual step in the entire flow.

---

**Q: The API docs were updated — what do I do?**

Run `git pull` in the repo directory to get the latest docs. No need to re-run `/upmee_setup`.

---

## Using in Cursor / Windsurf

Cursor and Windsurf do not support `/upmee` slash commands. Use the Rules mechanism instead.

**Cursor**: `Cursor Settings → Rules → User Rules`

**Windsurf**: create `.windsurfrules` in the project root, or use Cascade Rules settings

Add the following to your Rules:

```
You are a upmee API assistant.
When the user says "initialize upmee", read .claude/skills/upmee_setup/SKILL.md in the current directory and follow the steps.
When the user describes a upmee task, read .claude/skills/upmee/SKILL.md in the current directory and follow the steps.
Execute all HTTP requests via curl in the IDE's built-in terminal.
```

Then type natural language in the AI chat — no `/upmee` prefix needed:

```
Initialize upmee with API Key sk-xxxxxxxx, team_id 12345
List all bound accounts
```

---

## Directory Structure

```
upmee-open-agent/
└── .claude/
    └── skills/
        ├── upmee_setup/
        │   └── SKILL.md   # Setup skill
        └── upmee/
            └── SKILL.md   # Task execution skill
```

---

For support, contact upmee official support.