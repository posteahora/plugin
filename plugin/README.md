# PosteAhora plugin for Claude (Cowork / claude.ai)

Bundles the PosteAhora **MCP connector** + **Skills** so Claude can plan content,
collect post ideas into your kanban, and publish across your connected social
platforms.

## What's inside
- `.mcp.json` — the hosted PosteAhora MCP server (remote, no-auth capability URL).
- `skills/collect-post-ideas/` — brainstorm post ideas straight into your Ideas board.

## Setup
1. In PosteAhora → **Settings → API & integrations**, generate your **Connector URL**
   (requires the API/MCP add-on). It looks like
   `https://mcp.posteahora.com/mcp/u_…`.
2. Edit `.mcp.json` and replace `REPLACE_WITH_YOUR_CONNECTOR_TOKEN` with your URL.
3. Install the plugin in Claude (Cowork → Customize → install) or add the MCP URL
   directly via Settings → Connectors.

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
