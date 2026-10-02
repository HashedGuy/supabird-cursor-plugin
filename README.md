# SupaBird

Write, schedule, and research X posts from Claude or Cursor. This repository is the plugin. The SupaBird service stays on [supabird.io](https://supabird.io). The plugin only tells the app how to connect.

## Use it

Install the plugin, then connect SupaBird when asked and sign in with the account you want to post from. SupaBird Pro, or an active trial, is required. Some actions use account credits.

Ask for a draft in your voice, a search of public posts, today's growth tasks, or a post scheduled on X. Cross-posting to LinkedIn, Threads, or Bluesky works only for networks already connected in SupaBird.

## Data

The plugin sends post text, search requests, and account actions to the signed-in SupaBird account through `https://api.supabird.io/mcp`. It stores nothing itself. SupaBird stores drafts, scheduled posts, and task updates in that account. Sign-in is SupaBird OAuth. SupaBird does not ask for an X password.

## Connect

The server URL is `https://api.supabird.io/mcp`. Do not put an access token in this repo.

## Repository layout

```text
.claude-plugin/plugin.json   Claude plugin manifest
.mcp.json                    Hosted MCP server for Claude
.cursor-plugin/plugin.json   Cursor plugin manifest
mcp.json                     Hosted MCP server for Cursor
assets/logo.svg              Logo
skills/supabird/SKILL.md     How to use the tools
```
