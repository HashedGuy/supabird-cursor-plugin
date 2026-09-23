# SupaBird for Cursor

Write, schedule, and research X posts from Cursor. This repository is the public plugin. The SupaBird service stays on [supabird.io](https://supabird.io); this repo only tells Cursor how to connect to it.

## What you can do

- Write drafts in your voice, in the style of creators you follow, or as one specific creator.
- Schedule posts on X, review the queue, and cancel a scheduled post.
- Cross-post a queued post to LinkedIn, Threads, or Bluesky when those accounts are connected.
- Check today's growth tasks, posting slots, and performance.
- Search public posts, profiles, trends, lists, and communities.
- Generate post ideas from your own content or from posts you supply.

SupaBird MCP is available on the Pro plan and during an active trial. Some actions use account credits.

## Connect

1. Install this plugin in Cursor.
2. Open **Customize → MCPs** and authenticate SupaBird when Cursor asks. Sign in with the SupaBird account you want to post from.
3. Ask the agent to draft, schedule, or look something up.

The plugin points at `https://api.supabird.io/mcp`. Cursor completes OAuth itself. Do not put an access token in this repo or in `mcp.json`.

## Repository layout

```text
.cursor-plugin/plugin.json   Plugin manifest
mcp.json                     Hosted MCP server
assets/logo.svg              Logo
skills/supabird/SKILL.md     When to use each tool
```
