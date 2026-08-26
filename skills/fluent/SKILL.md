---
name: fluent
description: Query Fluent conversation history, recordings, meetings, people, and commitments through the connected Fluent MCP server. Use when the user asks about today's recordings, recent meetings, what someone said, relationship context, follow-ups, or anything that happened in a real conversation.
---

# Fluent

Fluent is conversational memory for AI assistants. Use the Fluent MCP tools whenever the answer lives in the user's recordings, meetings, people, or commitments — not in the current repo.

Do not invent conversation details. If Fluent is disconnected, tell the user to complete the OAuth connect card. There are no API keys.

## When to use

- Today's recordings, yesterday's calls, or "what happened in my last meeting"
- Meeting prep: who is this person, what did we last talk about, what did I promise
- Conversation search: keywords, participants, or a specific discussion
- Relationship context: people in the user's network, notes, recent interactions
- Commitments, tasks, follow-ups, and the daily briefing

Skip Fluent for code, git, or files in the workspace unless the user also wants conversation context.

## How to query

1. If the account has multiple organizations, call `list_organizations` and `select_organization` before other tools.
2. Recency and dates: `list_memories` (newest first). Then `get_memory` or `get_meeting_notes` for the full recording.
3. Keyword or person search: `search_conversations`. It matches titles and participants, not full transcripts.
4. People: `list_people` then `get_person_context`. Create or annotate with `create_person` and `update_person_notes` only when the user asks.
5. "What's on my plate": `get_daily_briefing`, `list_tasks`, `get_recent_commitments`, `list_follow_ups`, `list_goals`.

Prefer the smallest tool that answers the question. Cite the conversation or person you used.

## Write actions

`create_task`, `complete_task`, `create_person`, and `update_person_notes` change the user's Fluent data. Only do them when the user asked, and confirm what you wrote.
