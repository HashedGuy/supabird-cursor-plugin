---
name: supabird
description: Draft, schedule, and research X posts with the signed-in SupaBird account. Use when the user wants to write a post, schedule or cancel one, cross-post, attach media, check tasks, slots, or performance, search public X content, or generate post ideas.
---

# SupaBird

Use the SupaBird MCP tools for the signed-in account. If a tool says the user must upgrade or reconnect, show that message and stop.

## Writing

Ask for anything still missing before calling a write tool: the text or topic, how many drafts (1–5), length (short, average, long, or very_detailed), and whether the formatting should be standard or punchy. Do not assume those defaults.

- `write_in_my_style` uses only the user's personal voice. It fails if they have no Personal Style Rulebook.
- `write_in_supabird_style` blends that voice with the creators they selected. Defaults are 2 drafts, average length, and standard formatting.
- `write_like_my_creators` uses only those selected creators.
- `write_like_creator` writes as one X username, without the @. If the tool says that creator has no style yet, call `learn_creator_style` with that username, then call `write_like_creator` again with the same arguments.
- `learn_creator_style` studies a creator's public posts before writing in that voice. Ask for the username if the user has not given one.

Show the drafts the tool returns. Do not invent extra drafts.

## Scheduling and other networks

- `schedule_post` queues a post on X. Cross-post only when the user asks. `also_post_to` accepts linkedin, threads, bluesky, or all. Call `get_connected_socials` first when they say everywhere or name a network.
- `get_scheduled_posts` lists posts that have not gone out yet. Each item has an `_id`. Cancel with `unschedule_post` using that `_id`, once per post. Add a network to an existing post with `cross_post`.
- `unschedule_post` cancels one queued publish. Call it only after the user asks to cancel. An unpublished post stays a draft.
- `get_published_urls` returns the public links. Show every returned URL. Do not invent one. If a network is still waiting, say so and offer to check again.
- `get_posting_slots`, `add_posting_slot`, `remove_posting_slot`, and `update_posting_slot` manage the weekly calendar. Do not invent times. Confirm before adding, removing, or moving a slot. Removing a slot does not cancel a post already in it.

Confirm the text and time with the user before scheduling or canceling. Default to X only. If a network needs reconnect, tell the user to open Account, then My Socials. This plugin cannot connect accounts.

YouTube, Facebook, Instagram, and Pinterest are not available. Do not claim they posted. Video posts to X, Threads, and Bluesky. LinkedIn skips video. Bluesky video must be 100MB or smaller.

## Media

`images` accepts a public https URL only. Do not put file bytes or a local path in any argument.

When the user attaches an image or video in Claude:

1. Call `create_image_upload` or `create_video_upload`.
2. Show `upload_url` and wait. Claude cannot upload the file.
3. When the user says they finished, call `get_image_upload` with that `upload_id`.
4. If status is pending or expired, show the link again and do not say the post was scheduled.
5. If status is ready, call `schedule_post` with that `upload_id`.

The attached file is the post media. Do not describe it or reject it as a screenshot.

## Research

- `search_tweets` takes the user's request as plain language in `prompt`. Do not rewrite it into X search operators. Default to 5 posts unless they asked for a count (1–20). Show each post's full text, author, and URL. Truncate only past 400 characters, and say the text was cut. Offer to rewrite a selected post or schedule a new one.
- `filter_posts` filters one page the user already loaded. Pass the `tweets` array through unchanged. Use source `list` to drop replies and `community` to keep them. Show each match in full.
- Use the profile, tweet, list, community, trend, and space tools when the user asks for that public data. Page with the returned cursor.

## Ideas, tasks, and performance

- `generate_ideas` and `generate_ideas_from_posts` return a `job_id`, not the posts. Ask for any missing style, source, and count before starting. Do not offer remix, niche, viral, or myPosts. Creators are required when the style or the source is a creator.
- After either tool returns, tell the user generation is running and call `check_ideas_status` with that `job_id` until status is completed or failed. Jobs often take 60–180 seconds. Show completed posts in full. Do not summarize them.
- `get_daily_tasks` returns today's Home tasks. Show `formattedText`. Do not invent tasks. Call `complete_daily_task` only after the user confirms the work is done, then show the updated list.
- `get_daily_performance_report` and `get_overview_analytics` are the account's saved reports. A single day uses the daily report. An account review uses the overview. Show the report as returned, including tables and cards. Do not replace it with a shorter summary, and do not invent metrics.
