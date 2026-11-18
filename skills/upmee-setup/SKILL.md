---
name: upmee-setup
description: Configure and verify local access to a UPMee team before using UPMee API workflows.
---

# Set up UPMee

1. Use the local runtime environment. Check whether `UPMEE_API_KEY` exists without printing its value. If unavailable, direct the user to configure it via their terminal or secret manager. Request the team ID if neither the current request nor `UPMEE_TEAM_ID` specifies it.
2. Use `https://www.upmee.cc` as the default API host. Keep the API key out of chat, command literals, debug traces, and version control. Do not send it to a documentation host or unrelated origin.
3. To verify team access, open **List Accounts** through the local `docs/api-index.md` and make a minimal read-only request to `POST /open_api/media/list` using the intended team. If the reference is unavailable, ask for its Markdown rather than guessing the request shape.
4. Treat a successful HTTP response with business `code: 0` as verified access. Report authentication, team access, API, and network errors separately. For an API failure, include `message` and `request_id` when present.
5. Summarize the team, API host, and verification result. Existing legacy configuration files are not needed for this setup.

## Check the latest online reference

If a request built from the bundled reference fails, consult the [live UPMee API documentation](https://www.upmee.cc/developers/document/). Use its directory to locate the same module and operation, select English, and read the latest method, URL, headers, request fields, required and conditional rules, types, enum values, and response structure. Use **Copy as Markdown** where available to load the complete reference.

Compare the live definition with the bundled file and adjust the request only where the current reference supports the change. For authentication, permissions, network errors, or rate limits, address the reported cause as well. Keep the existing rate limits and retry limits in effect.

For a failed read, retry the corrected request within the bounded retry policy. If a write timed out or its outcome is uncertain, reconcile it through a documented lookup before resubmitting. Report any remaining uncertainty. If the live reference cannot be accessed, ask the user for its Markdown and the redacted error response.

Summarize any contract differences that affected the call so the bundled reference can be updated.
