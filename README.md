# PosteAhora — Claude Code plugin

A [Claude Code](https://claude.com/claude-code) plugin marketplace for
[PosteAhora](https://posteahora.com). Install it to connect the **PosteAhora MCP
server** and a set of **posting skills** so Claude can plan, schedule and publish
social content across Instagram, X, LinkedIn, Threads, Facebook, TikTok and more —
right from your editor.

## Install

In Claude Code, add this marketplace and install the plugin:

```
/plugin marketplace add posteahora/plugin
/plugin install posteahora@posteahora
```

Then restart Claude Code when prompted.

## Set your connector

The plugin ships an MCP connector whose URL is read from an environment variable —
so you never edit plugin files, and it survives plugin updates:

1. In PosteAhora → **Settings → API & integrations**, generate your Connector URL
   (requires the API/MCP add-on). It looks like `https://mcp.posteahora.com/mcp/u_…`.
2. Set it as `POSTEAHORA_CONNECTOR_URL` and add it to your shell profile so it persists:

   ```bash
   export POSTEAHORA_CONNECTOR_URL="https://mcp.posteahora.com/mcp/u_…"
   ```

3. Reload Claude Code (`/reload-plugins` or restart). The connector picks up the URL
   automatically — the Connector URL is a secret, so keeping it in your env (not in
   any repo or plugin file) is exactly right.

Prefer a local key-based setup instead of the hosted connector? Use
[`@posteahora/mcp`](https://github.com/posteahora/mcp).

## What's included

**MCP connector** — `list_accounts`, `create_idea`, `create_post`, `schedule_post`,
`get_analytics`, `upload_media` and more.

**Skills**

| Skill | What it does |
|-------|--------------|
| `collect-post-ideas` | Brainstorm ideas straight into your Ideas board (never publishes) |
| `schedule-content` | Create, schedule and publish posts across connected channels |
| `analytics-report` | Summarize performance and seed follow-up ideas |

Just talk to Claude: *"schedule these 3 posts to Instagram and X for Tuesday
morning"* or *"how did my posts do last month?"*

## Security

The Connector URL is a capability URL — the secret is in the URL, so treat it like
a password. If it leaks, hit **Revoke** in Settings → API & integrations.

## Related

- MCP server (stdio / key-based): [`@posteahora/mcp`](https://github.com/posteahora/mcp)
- CLI: [`@posteahora/cli`](https://github.com/posteahora/cli)
- Docs: [posteahora.com/docs](https://posteahora.com/docs)

## License

MIT
