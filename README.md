# UPMee CLI

**Run social media, creator commerce, and content workflows from your AI assistant.**

Ask Claude Code, Codex, or another AI coding assistant to check a TikTok publishing schedule, pull affiliate orders, or review recent Instagram comments. UPMee CLI provides Agent Skills that help your assistant find the right UPMee API operation, build the request, and report what happened.

[Explore UPMee](https://www.upmee.cc/) · [Get started](#quick-start) · [Browse the API index](docs/api-index.md)

## Why UPMee?

UPMee gives brands, agencies, and creator teams one platform for managing connected accounts and running recurring workflows across markets. Use the dashboard for day-to-day operations, or bring the same API workflows into the AI tool you already use.

Work with platforms such as TikTok, YouTube, Facebook Pages, Instagram, and TikTok Shop. Availability varies by platform, account type, and API operation.

## What you can do

| Workflow | What the API supports |
| --- | --- |
| **Social publishing** | Upload assets, create or update video and photo publishing tasks, and check publishing status. |
| **Audience engagement** | Read and reply to comments, review direct message conversations, and manage customer records. |
| **Creator commerce** | Manage showcase products, create shoppable content, and look up affiliate orders and commissions. |
| **Performance reporting** | Query social and shop analytics for reporting and campaign review. |
| **AI content generation** | Create video, image, and voice generation tasks and check results through the relevant endpoints. |
| **Automation and Spark Ads** | Manage comment and DM automation rules, knowledge bases, and TikTok Spark Ads authorization tasks. |

## Quick start

1. Sign in to [UPMee](https://www.upmee.cc/), create an API key, and identify the team you want to work with. Make the key available to your local execution environment as `UPMEE_API_KEY` and set `UPMEE_TEAM_ID` to your team ID. Keep the key out of chat and source control.
2. Clone the repository, then open it in your AI assistant.

   ```bash
   git clone https://github.com/upmee-ai/upmee-cli.git
   cd upmee-cli
   ```

3. Follow the setup guide for your assistant and try the read-only account lookup.

| Assistant | Verify access | List connected accounts |
| --- | --- | --- |
| [Claude Code](docs/setup/claude-code.md) | `/upmee_setup` | `/upmee List the connected accounts for my team` |
| [Codex](docs/setup/codex.md) | `$upmee-setup` | `$upmee List the connected accounts for my team` |
| [Other AI tools](docs/setup/other-ai-tools.md) | Ask the assistant to follow the shared setup skill. | Ask it to use the UPMee skill to list your team's connected accounts. |

## Try a workflow

- **Social team** — “Show this week's scheduled publishing tasks. Group them by account and flag any that failed.”
- **Creator commerce team** — “Summarize affiliate orders from the past seven days and show estimated and actual commissions separately.”
- **Community manager** — “List recent comments on this Instagram post and draft replies for my review.”
- **Content team** — “Check my recent AI image generation tasks and show which are complete.”

See [workflow examples](docs/workflows.md) for the inputs each task needs and what to check in the response.

## API best practices

Fetch every page when you need the full account list and select accounts by the types accepted by the target endpoint. Keep API traffic at or below 5 requests per second by default. After submitting publishing tasks, save their IDs and wait at least 5 minutes before checking status in batches. Send up to 20 IDs per batch and leave at least 10 seconds between status requests. Recheck tasks still under review once, at least 5 minutes later, for a maximum of two checks per ID.

[See how to apply these practices](docs/workflows.md#api-best-practices).

[Data retrieval and sync](docs/workflows.md#data-retrieval-and-sync) covers batching, publication-time filters for the past four days, hourly analytics updates, and incremental comment and message syncs.

## API reference

Use the [English endpoint index](docs/api-index.md) to find an operation and its request path. Open the linked local Markdown for request and response fields, examples, and limits. If your assistant cannot access the reference, use **Copy as Markdown** and provide the document in your session.

## Support

Report documentation issues through [GitHub Issues](https://github.com/upmee-ai/upmee-cli/issues). Include the endpoint, the behavior you observed, and the request ID if available. Remove API keys and account data before sharing logs.

See the [maintenance guide](docs/maintenance.md) for updating the skills and endpoint index.


## Online documentation fallback

If a call fails, use the [live API documentation](https://www.upmee.cc/developers/document/) directory to locate the endpoint and verify its latest parameters. Follow the [fallback workflow](docs/workflows.md#check-the-latest-online-reference) before retrying.
