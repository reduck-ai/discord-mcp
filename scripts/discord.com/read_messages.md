# Read Discord messages

Automatically read Discord messages on discord.com. Reads the most recent messages of a Discord channel or direct message (author, timestamp, text), newest first, scrolling up to load more until the requested count. Requires being logged in. A DM or group DM is read the same way: pass its url from discord.com/list_dms. It also reads a thread or a forum post, since both are channels in their own right: pass the post's url (from discord.com/list_forum_posts) and you get its replies plus the opening post, newest first — there is no separate thread-reading script. To list the posts of a forum channel rather than its messages, use discord.com/list_forum_posts instead.

- Site: discord.com
- Address: `reduck/discord.com/read_messages`
- Updated: 2026-10-01 (v12)
- Author: Reduck AI (reduck)

## Run it

Ask an AI agent connected to Reduck over MCP (`https://mcp.reduck.ai/mcp`) to run `reduck/discord.com/read_messages`, or run it from a terminal:

```bash
npx @reduck-ai/cli@latest run --script reduck/discord.com/read_messages
```

## Input

- `channelUrl` (string, required): Full channel URL: https://discord.com/channels/<guildId>/<channelId> for a server channel, or https://discord.com/channels/@me/<channelId> for a direct message (from discord.com/list_dms).
- `limit` (integer, optional): How many messages to return, newest first. Fewer come back when the channel is shorter.

## Output

- `count` (integer, required)
- `messages` (array, required): Newest first.
- `channelId` (string | null, required)

## FAQ

### What does "Read Discord messages" do?

Reads the most recent messages of a Discord channel or direct message (author, timestamp, text), newest first, scrolling up to load more until the requested count. Requires being logged in. A DM or group DM is read the same way: pass its url from discord.com/list_dms. It also reads a thread or a forum post, since both are channels in their own right: pass the post's url (from discord.com/list_forum_posts) and you get its replies plus the opening post, newest first — there is no separate thread-reading script. To list the posts of a forum channel rather than its messages, use discord.com/list_forum_posts instead.

### How do I automatically read Discord messages on discord.com?

Ask an AI agent connected to Reduck to run reduck/discord.com/read_messages, or run it from a terminal with the Reduck CLI: npx @reduck-ai/cli@latest run --script reduck/discord.com/read_messages

### Is there a discord.com API to read Discord messages?

You do not need one. "Read Discord messages" drives the real discord.com pages in a browser, so it works whether or not discord.com offers an API for this.

### What information do I need to provide?

Required: channelUrl. Optional: limit.

### What does it return?

It returns count, messages, channelId.

### Do I need to be logged in to discord.com?

Yes. It acts as you on discord.com: on your own Chrome it reuses your session, and on a Reduck-hosted browser it loads the discord.com cookies saved by the Reduck extension.

### Does it change anything on discord.com, or only read data?

It only reads. It looks things up on discord.com and changes nothing there.

### How do I run it?

Ask an AI agent connected to Reduck to run reduck/discord.com/read_messages, or run it from a terminal with the Reduck CLI: npx @reduck-ai/cli@latest run --script reduck/discord.com/read_messages

### Who maintains it?

It is part of Reduck's official curated catalogue.

Source: https://reduck.ai/explore/scripts/reduck/discord.com/read_messages
