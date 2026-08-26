# Fluent for Cursor

A Cursor plugin that connects the [Fluent](https://becomefluent.io/) MCP server so agents can query your conversation history, recordings, relationships, and commitments.

This is a thin wrapper around Fluent's existing remote MCP. It does not ship a local server, API keys, or secrets. Auth is OAuth 2.1 — Cursor's connect card handles sign-in.

- **Plugin name:** `fluent`
- **Author:** Feral Intelligence
- **Homepage:** https://becomefluent.io/mcp/
- **Repository:** https://github.com/Feral-Intelligence/fluent-cursor-plugin
- **MCP server:** `https://mcp.becomefluent.io` (streamable HTTP at `/mcp`)

## What you get

After you install the plugin and complete OAuth, Cursor can:

- Search and list recordings / conversation memories
- Pull meeting notes and full transcripts
- Look up people and relationship context
- Surface tasks, commitments, follow-ups, goals, and the daily briefing

The included `fluent` skill tells the agent when to use those tools (today's recordings, meeting prep, conversation history).

## Install from this repo

Marketplace listing is a later step. Until then, load the plugin from a local checkout:

```bash
git clone https://github.com/Feral-Intelligence/fluent-cursor-plugin.git
cd fluent-cursor-plugin
mkdir -p ~/.cursor/plugins/local
ln -s "$(pwd)" ~/.cursor/plugins/local/fluent
```

Reload Cursor. Open **Customize** and enable the Fluent MCP server if it is not already on. When the connect card appears, sign in with your Fluent account (OAuth 2.1). There are no API tokens to paste.

You need a Fluent account and captured conversations for the tools to return data. Get started at [becomefluent.io](https://becomefluent.io/).

## Auth

Fluent uses OAuth 2.1 with dynamic client registration. This plugin does not declare API-token variables and does not put credentials in the repo.

If tools fail with an auth error, reconnect from the MCP connect card. Do not add bearer tokens to `mcp.json`.

## Layout

```
.cursor-plugin/plugin.json   # Cursor plugin manifest
mcp.json                     # Remote MCP server (OAuth via host)
skills/fluent/SKILL.md       # When to query Fluent
assets/logo.png              # Fluent app icon
assets/logo.svg              # Fluent mark from becomefluent.io
```

## Marketplace submit (later)

This plugin is **not** submitted yet. When you are ready:

1. Confirm `"repository"` in `.cursor-plugin/plugin.json` is this public GitHub URL.
2. Install from the local path above, complete OAuth, and run a real query (for example "what did I record today?").
3. Confirm the plugin name `fluent` is still unused on the marketplace.
4. Submit the public repo at [cursor.com/marketplace/publish](https://cursor.com/marketplace/publish).

See the [Cursor plugins reference](https://cursor.com/docs/reference/plugins) for the current checklist. Do not put secrets in the repo.
