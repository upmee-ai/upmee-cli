# UPMee CLI (`upmee-cli`)

<p align="center">
  <img src="https://img.shields.io/badge/AI--Native-Agent%20Skill-botgreen?style=flat-for-the-badge" alt="AI-Native">
  <img src="https://img.shields.io/badge/Compatible-Claude%20Code%20%7C%20Cursor%20%7C%20Windsurf-blue?style=flat-for-the-badge" alt="Compatibility">
  <img src="https://img.shields.io/badge/License-MIT-yellow?style=flat-for-the-badge" alt="License">
</p>

> **Operate global social media channels using pure natural language.**
> `upmee-cli` bridges the gap between AI Agents and the UPMee API. No coding skills or API documentation drilling required. Simply describe what you want in plain text, and your AI assistant will handle complex matrix operations across TikTok, YouTube, and Instagram.

This repository ships with two custom **Claude Code** skill commands:
- `/upmee_setup`: One-time initialization. Securely saves your API Key locally and verifies server connectivity.
- `/upmee`: Core execution engine. Describe your task in natural language, and the AI autonomously orchestrates the required UPMee API calls.

---

## 🌟 Why UPMee?

**UPMee** is the most powerful AI-native, all-in-one global social media management and automation platform. Designed for cross-border e-commerce brands, digital marketing agencies, and global media matrices, UPMee consolidates fragmented operations into a unified workflow.

By leveraging **100% official API integrations**, UPMee guarantees compliance, eliminates account-banning risks, and slashes operational costs—allowing a single operator to flawlessly manage hundreds of international accounts.

### 🌐 Supported Global Platforms
Our API ecosystem provides cross-platform execution across all major global networks for maximum reach and visibility:
- **TikTok** & **TikTok Shop** (US, UK, SE Asia, etc.)
- **YouTube** (Shorts & Long-form)
- **Instagram** (Reels & Posts)
- **Facebook** (Pages & Groups)
- **Threads**
- **Pinterest**
- **LinkedIn**
- **Bluesky**
- **VK (VKontakte)**

### ⚡ Comprehensive Suite of Open API Capabilities
`upmee-cli` exposes the core backend power of the UPMee platform. You can programmatically command the AI Agent to execute any of the following newly opened API endpoints:
- 📤 **Social Content Publishing:** Seamlessly publish video posts and photo posts across all supported global social networks simultaneously.
- 🛍️ **Shopping Content Publishing:** Programmatically publish TikTok shopping videos and product-tagged photos to drive affiliate and e-commerce conversions.
- 📊 **Data Analytics & Queries:** Retrieve comprehensive metadata, views, likes, account growth metrics, and conversion data for both organic and shopping posts.
- 💬 **Comment Management:** Fetch live comment streams from your matrix accounts and push automated, contextual replies to maximize fan engagement.
- ✉️ **Direct Message (DM) Management:** Intercept incoming customer messages, track chat history, and instantly respond to high-value leads across channels.
- 📦 **Product & Inventory Management:** Automate e-commerce operations by bulk adding or removing products across various storefronts and creator accounts.
- 🚀 **Full Operational Coverage:** Gain extensible access to advertisements, team collaboration tools, and deep-layer system actions provisioned by UPMee.

---

## 🔑 Prerequisites

Before getting started, ensure you have the following components ready:

| Requirement | Description & How to Obtain |
| :--- | :--- |
| **[Claude Code](https://claude.ai/code)** | Anthropic's official CLI agent. Install via `npm i -g @anthropic-ai/claude-code` and sign in. |
| **UPMee API Key** | Log in to the [UPMee Platform (https://www.upmee.cc/)](https://www.upmee.cc/) → **Developer Settings** → **API Key Management** → **Create Key**. |
| **Team ID** | Located in your [UPMee Platform](https://www.upmee.cc/) → **Team Settings** dashboard. |

---

## 🚀 Quick Start

### Step 1: Clone the Repository
```bash
git clone [https://github.com/upmee-ai/upmee-cli.git](https://github.com/upmee-ai/upmee-cli.git)
cd upmee-cli
```
> ⚠️ **Crucial Note:** Every time you use this tool, you must launch Claude Code from the root of this repository directory so that the custom skill definitions can be auto-discovered.

### Step 2: Launch Claude Code
```bash
claude
```

### Step 3: Initialize (One-Time Only)
Inside the interactive Claude Code chat interface, run the setup command to initialize your secure local config:
```text
/upmee_setup YOUR_UPMEE_API_KEY
```
If you already know your Team ID, you can pass it simultaneously:
```text
/upmee_setup YOUR_UPMEE_API_KEY 12345
```
Once you see the `"Setup complete!"` confirmation, initialization is finished. Your API key is permanently stored on your local machine.

### Step 4: Run Your First AI-Driven Command
```text
/upmee List all bound accounts for team_id 12345
```

---

## 💡 Matrix Automation Examples

### 📈 Account & Audit Management
```text
# Audit connected social media assets across platforms
/upmee List all bound accounts for team_id 12345

# Track programmatic publishing status over the past week
/upmee Show publishing tasks from the last 7 days, team_id 12345
```

### 🎥 Content & Video Distribution
```text
# Distribute video assets to TikTok with customized metadata
/upmee Publish /Users/me/Desktop/video.mp4 to TikTok with title "Summer Scenery", team_id 12345
```

### 💬 Engagement & Lead Conversion
```text
# Fetch comment stream from a specific piece of content
/upmee List comments on item_id 7xxx, team_id 12345

# Submit an automated, contextual reply to a fan comment
/upmee Reply to comment_id xxx on item_id 7xxx with "Thanks for the support!", team_id 12345

# Monitor active customer conversations and direct messages
/upmee List the latest conversations for media_id 888, team_id 12345
```

---

## 🔄 Daily Workflow

To keep the custom AI skills active, always navigate to this project folder in your terminal before launching Claude Code:
```bash
cd /path/to/upmee-cli
claude
```
No re-initialization needed—simply instruct the AI in plain English or Chinese to manage your social operations.

---

## 🤖 Using in Cursor / Windsurf

Since Cursor and Windsurf do not natively support `/` slash commands, you can achieve identical functionality by feeding the skill boundaries into their **AI Rules / Context Instructions** systems.

### Configuration
* **Cursor**: Go to `Cursor Settings` → `Rules` → `User Rules`
* **Windsurf**: Create a `.windsurfrules` file in the root of the project, or paste into Cascade Rules settings.

Add the following rule set:
```text
You are an expert UPMee API assistant.
1. When the user says "initialize upmee", read .claude/skills/upmee_setup/SKILL.md in the current directory and follow the steps.
2. When the user describes a UPMee task, read .claude/skills/upmee/SKILL.md in the current directory and follow the steps.
3. Execute all HTTP requests via curl in the IDE's built-in terminal.
```

Once configured, you **no longer need the `/upmee` prefix**. Simply use natural language directly in your AI chat panel:
```text
Initialize upmee with API Key sk-xxxxxxxx, team_id 12345
List all bound accounts
```

---

## ❓ FAQ

**Q: The `/upmee` command is not being recognized by Claude Code?**  
A: The skill payloads only execute when Claude Code is initialized directly inside this repository. You can verify that the skill definitions exist by running:
- *macOS / Linux:* `ls .claude/skills/upmee/SKILL.md`
- *Windows PowerShell:* `Test-Path ".\.claude\skills\upmee\SKILL.md"`
  If the files are verified but the command still fails, `exit` Claude Code and re-launch it from this directory.

**Q: The AI asks me to copy and run a command manually when publishing a video—is that normal?**  
A: **Yes, completely expected.** Video and rich media publishing involve heavy binary file transfers, which cannot be directly streamed through the text-based LLM chat context. The AI agent will dynamically compile the perfect `curl` or upload command customized to your local file path. You simply copy-paste it into your terminal, hit execute, and paste the server response back to the AI to continue tracking.

**Q: Where is my API Key saved? Is it secure?**  
A: Your credentials are safe. The setup script stores configurations purely on your local file system at `~/.upmee/config.json`. UPMee never intercepts, caches, or collects your secret tokens on external servers.

**Q: What should I do when UPMee rolls out API documentation updates?**  
A: Simply pull the latest changes from this repository:
```bash
git pull
```
This updates the underlying local skill prompt specifications. No re-initialization or key regeneration is required.

---

## 📂 Directory Structure

```text
upmee-cli/
└── .claude/
    └── skills/
        ├── upmee_setup/
        │   └── SKILL.md   # Initialization & secure authentication mechanics
        └── upmee/
            └── SKILL.md   # Core Natural-Language-to-API engine
```

---

✉️ **Need Assistance?**  
Visit the official [UPMee Website (https://www.upmee.cc/)](https://www.upmee.cc/) to explore full documentation, analytics dashboards, and platform features. For technical issues, feature requests, or enterprise scaling inquiries, please feel free to open a GitHub Issue or reach out to our global support team via the website.