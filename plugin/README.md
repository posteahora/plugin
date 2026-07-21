# PosteAhora plugin for Claude (Cowork / claude.ai)

Bundles the PosteAhora **MCP connector** + **Skills** so Claude can plan content,
collect post ideas into your kanban, and publish across your connected social
platforms.

## What's inside
- `.mcp.json` — the hosted PosteAhora MCP server; its URL is read from the
  `POSTEAHORA_CONNECTOR_URL` environment variable (nothing to edit).
- `skills/` — `collect-post-ideas`, `schedule-content`, `analytics-report`.

## Setup
1. In PosteAhora → **Settings → API & integrations**, generate your **Connector URL**
   (requires the API/MCP add-on). It looks like
   `https://mcp.posteahora.com/mcp/u_…`.
2. Set it as an environment variable so the plugin picks it up automatically:
   ```bash
   export POSTEAHORA_CONNECTOR_URL="https://mcp.posteahora.com/mcp/u_…"
   ```
   Add it to your shell profile (`~/.zshrc`, `~/.bashrc`) to persist it.
3. Install the plugin, then reload Claude Code.

A Connector URL is **bound to one workspace** (the one active when you generated
it): the tools act on that workspace's accounts, posts and ideas only. For
another workspace, generate a Connector URL there. A viewer-role connector can
read but not create or publish.

## Using it
- "Brainstorm 8 post ideas about Mulu, tag them eng" → the `collect-post-ideas`
  skill drops them into your Ideas board (Unassigned).
- "Show my connected accounts" / "create a draft post …" → MCP tools
  (`list_accounts`, `create_post`, `schedule_post`, …).

## Tools exposed by the MCP server
`list_accounts`, `list_ideas`, `create_idea`, `create_post`, `schedule_post`,
`list_posts`, `get_post_status`, `upload_media`.

## Security
The connector URL is a capability URL — the secret is in the URL. Treat it like a
password; if it leaks, hit **Revoke** in Settings and a new one replaces it.
