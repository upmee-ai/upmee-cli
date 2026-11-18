# Maintain the repository

Edit shared instructions under `skills/` first. Mirror them in `.agents/skills/` and `.claude/skills/`. The Claude Code setup copy uses `upmee_setup` in its directory and manifest to retain its existing command name. Review mirrors whenever shared instructions change.

Refresh the endpoint index from the current English API documentation. Keep the method and path exact. Verify that each workflow can locate its current parameter reference, and review the index for removed or renamed operations.

Before merging, check Markdown links, skill discovery in a fresh project session, and the read-only account lookup using a test team. Review public examples and screenshots for untranslated text and live credentials.

Refresh the linked files under `docs/reference/` from the published English references whenever the API contract changes. Verify that each indexed operation has a local file.
