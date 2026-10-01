# List Discord direct messages

Automatically list Discord direct messages on discord.com. Lists the direct messages (DMs) of the signed-in Discord account, one-to-one and group DMs, most recent first, as the Direct Messages sidebar shows them: the conversation's name, its channelId and its url. Pass a conversation's url to discord.com/read_messages to read it. Requires being logged in.

- Site: discord.com
- Address: `reduck/discord.com/list_dms`
- Updated: 2026-10-01 (v6)
- Author: Reduck AI (reduck)

## Run it

Ask an AI agent connected to Reduck over MCP (`https://mcp.reduck.ai/mcp`) to run `reduck/discord.com/list_dms`, or run it from a terminal:

```bash
npx @reduck-ai/cli@latest run --script reduck/discord.com/list_dms
```

## Input

- `limit` (integer, optional): Return at most this many conversations, most recent first. Omit to list them all.

## Output

- `dms` (array, required): Most recent first, in sidebar order.
- `count` (integer, required)

## FAQ

### What does "List Discord direct messages" do?

Lists the direct messages (DMs) of the signed-in Discord account, one-to-one and group DMs, most recent first, as the Direct Messages sidebar shows them: the conversation's name, its channelId and its url. Pass a conversation's url to discord.com/read_messages to read it. Requires being logged in.

### How do I automatically list Discord direct messages on discord.com?

Ask an AI agent connected to Reduck to run reduck/discord.com/list_dms, or run it from a terminal with the Reduck CLI: npx @reduck-ai/cli@latest run --script reduck/discord.com/list_dms

### Is there a discord.com API to list Discord direct messages?

You do not need one. "List Discord direct messages" drives the real discord.com pages in a browser, so it works whether or not discord.com offers an API for this.

### What information do I need to provide?

Optional: limit.

### What does it return?

It returns dms, count.

### Do I need to be logged in to discord.com?

Yes. It acts as you on discord.com: on your own Chrome it reuses your session, and on a Reduck-hosted browser it loads the discord.com cookies saved by the Reduck extension.

### Does it change anything on discord.com, or only read data?

It only reads. It looks things up on discord.com and changes nothing there.

### How do I run it?

Ask an AI agent connected to Reduck to run reduck/discord.com/list_dms, or run it from a terminal with the Reduck CLI: npx @reduck-ai/cli@latest run --script reduck/discord.com/list_dms

### Who maintains it?

It is part of Reduck's official curated catalogue.

Source: https://reduck.ai/explore/scripts/reduck/discord.com/list_dms
