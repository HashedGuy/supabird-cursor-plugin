---
name: supabird
description: Draft, schedule, and research X posts with the signed-in SupaBird account. Use when the user wants to write a post, schedule or cancel one, cross-post, check tasks, slots, or performance, search public X content, or generate post ideas.
---

# SupaBird

Use the SupaBird MCP tools for the signed-in account. If a tool says the user must upgrade or reconnect, show that message and stop.

## Writing

Ask for anything still missing before calling a write tool: the text or topic, how many drafts (1–5), length (short, average, long, or very_detailed), and whether the formatting should be standard or punchy.

- `write_in_my_style` uses only the user's personal voice. It fails if they have no Personal Style Rulebook.
- `write_in_supabird_style` blends that voice with the creators they selected.
- `write_like_my_creators` uses only those selected creators.
- `write_like_creator` writes as one X username, without the @.
- `learn_creator_style` studies a creator's public posts before writing in that voice.

Show the drafts the tool returns. Do not invent extra drafts.

## Scheduling and other networks

- `schedule_post` queues a post on X. Cross-posting to LinkedIn, Threads, or Bluesky is optional and only for accounts the user has connected.
- `get_scheduled_posts` lists posts that have not gone out yet. Each item has an `_id`.
- `unschedule_post` cancels one queued post. Call it once per `_id`.
- `cross_post` sends an existing queued post to a connected network. Use `get_connected_socials` when the user is unsure which accounts are linked.
- `get_posting_slots`, `add_posting_slot`, `remove_posting_slot`, and `update_posting_slot` manage the weekly calendar.

Confirm the text and time with the user before scheduling or canceling.

## Research

- `search_tweets` takes the user's request as plain language in `prompt`. Do not rewrite it into X search operators. Default to 5 posts unless they asked for a count (1–20). Show each post's full text, author, and URL. Truncate only past 400 characters, and say the text was cut.
- Use the profile, tweet, list, community, trend, and space tools when the user asks for that public data. Page with the returned cursor.

## Ideas, tasks, and performance

- `generate_ideas` and `generate_ideas_from_posts` start idea jobs. `check_ideas_status` reads the result.
- `get_daily_tasks` and `complete_daily_task` are today's Home tasks.
- `get_daily_performance_report` and `get_overview_analytics` are the account's saved reports. Show report output as returned, including tables and cards. Do not replace a report with a shorter summary, and do not invent metrics.
