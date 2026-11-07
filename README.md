# Fluent for Cursor

Your meetings and work conversations in Cursor.

[Fluent](https://becomefluent.io/) records the conversations that happen away from your laptop (in-person meetings, 1:1s, hallway conversations) on your iPhone or a supported pendant, and turns them into meeting notes, tasks, follow-ups and profiles of the people you work with. This plugin connects Cursor's agent to that context through Fluent's hosted MCP server, so you can ask what was decided, what you owe whom, or who someone is without leaving the editor.

## Setup

1. Install **Fluent** from the Cursor Marketplace.
2. The first time the agent uses a Fluent tool, Cursor opens Fluent's sign-in. Sign in with your Fluent account and approve access (OAuth 2.1). There are no API keys to paste.

You need a Fluent account with recorded conversations. Accounts are created in the Fluent iPhone app: [becomefluent.io](https://becomefluent.io/).

## What's included

### MCP server

`fluent` → `https://mcp.becomefluent.io` (streamable HTTP, OAuth 2.1 with dynamic client registration).

**Read tools**

- `search_conversations`: search conversations by what was said, titles and participants
- `list_memories`, `get_memory`: browse conversations by date or person, and open one
- `get_meeting_notes`: summary, decisions and action items for a meeting
- `list_people`, `get_person_context`: the people you work with and your recent interactions
- `get_my_day`, `get_daily_briefing`: your plan, open commitments both ways, and recent meeting briefs
- `list_tasks`, `get_recent_commitments`, `list_follow_ups`, `list_goals`
- `list_workspaces`, `list_team_folders`, `list_team_notes`, `get_team_note`: notes teammates shared with your team

**Write tools**

- `create_task`, `complete_task`
- `create_person`, `update_person_notes` (replaces the existing notes)
- `set_day_plan` (replaces that day's plan; version-checked so it never overwrites a newer one)

Fluent has no delete tool. The server also offers prompts: `prepare_for_meeting`, `draft_follow_up`, `weekly_review`, `visit_report`, `open_loops` and `decisions_since`.

### Skill

**fluent**: tells the agent when meeting context is relevant and which tool to use.

## Try it

- "What did we decide in the last team standup?"
- "Prep me for my 1:1 with Jordan tomorrow."
- "What did I commit to this week that's still open?"
- "Add a task: send Sarah the API spec by Friday."

## Privacy and data

The agent sees only your own Fluent account's data (and notes teammates shared with you), the same data you see in the app. Calls run with your own token against Fluent's API. To disconnect, remove Fluent in Cursor's MCP settings.

- Privacy policy: https://becomefluent.io/privacy/
- Terms: https://becomefluent.io/terms/
- Docs: https://becomefluent.io/help/mcp-server-setup/
- Support: support@becomefluent.io

## Develop locally

```bash
git clone https://github.com/Feral-Intelligence/fluent-cursor-plugin.git
mkdir -p ~/.cursor/plugins/local
cp -R fluent-cursor-plugin ~/.cursor/plugins/local/fluent
```

Reload Cursor (Developer: Reload Window) and open **Customize** to check the `fluent` MCP server and skill.

## License

MIT
