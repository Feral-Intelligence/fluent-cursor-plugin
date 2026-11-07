---
name: fluent
description: Look up the user's meetings and work conversations in Fluent. Use when the user asks what was discussed or decided in a meeting, what they or someone else committed to, who a person is before a meeting, what is on their plate today, or ties the current task to something agreed in a conversation. Do not use for routine coding, git or workspace questions that have no meeting or conversation reference.
---

# Fluent

Fluent records the user's in-person meetings, 1:1s and calls and turns them into notes, tasks, follow-ups and profiles of the people they work with. Use the Fluent MCP tools when the answer lives in those conversations, not in the repo.

Never invent conversation details. If the Fluent tools are not connected, tell the user to connect Fluent from Cursor's MCP settings and sign in with their Fluent account. There are no API keys.

## Which tool

- **What was said or decided:** `search_conversations` (searches transcripts, note summaries, titles and participant names), then `get_meeting_notes` for summary, decisions and action items, or `get_memory` for the full conversation.
- **Recent or by date:** `list_memories` (newest first, filter by date range or person, paged with a cursor).
- **A person:** `list_people`, then `get_person_context` for their profile and recent interactions.
- **What's on my plate:** `get_my_day` for the whole day; `get_daily_briefing`, `list_tasks`, `get_recent_commitments`, `list_follow_ups` and `list_goals` for one slice.
- **Team notes:** `list_workspaces`, `list_team_folders`, `list_team_notes`, `get_team_note` for notes teammates shared. Attribute them to the teammate.

Prefer the smallest tool that answers the question. Cite the meeting (title and date) or person you used.

## Write actions

`create_task`, `complete_task`, `create_person`, `update_person_notes` and `set_day_plan` change the user's Fluent data. Use them only when the user asks, and say what you wrote. `update_person_notes` replaces the existing notes and `set_day_plan` replaces that day's plan, so read first and confirm before overwriting. Fluent has no delete tool.
