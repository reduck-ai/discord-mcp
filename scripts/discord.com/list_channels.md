# List Discord channels

Automatically list Discord channels on discord.com. Lists a Discord server's channels and categories from its sidebar (name, channelId, category, channel URL). Takes a guildId. Requires being logged in.

- Site: discord.com
- Address: `reduck/discord.com/list_channels`
- Updated: 2026-10-01 (v7)
- Author: Reduck AI (reduck)

## Run it

Ask an AI agent connected to Reduck over MCP (`https://mcp.reduck.ai/mcp`) to run `reduck/discord.com/list_channels`, or run it from a terminal:

```bash
npx @reduck-ai/cli@latest run --script reduck/discord.com/list_channels
```

## Input

- `guildId` (string, required): Server id, e.g. from discord.com/list_servers.

## Output

- `guildId` (string, required)
- `channels` (array, required): Channels in sidebar order. The sidebar is scrolled top to bottom to cover rows the page renders lazily. Threads are not listed (a channel's thread rows are skipped).
- `categories` (array, required): Categories in sidebar order.

## FAQ

### What does "List Discord channels" do?

Lists a Discord server's channels and categories from its sidebar (name, channelId, category, channel URL). Takes a guildId. Requires being logged in.

### How do I automatically list Discord channels on discord.com?

Ask an AI agent connected to Reduck to run reduck/discord.com/list_channels, or run it from a terminal with the Reduck CLI: npx @reduck-ai/cli@latest run --script reduck/discord.com/list_channels

### Is there a discord.com API to list Discord channels?

You do not need one. "List Discord channels" drives the real discord.com pages in a browser, so it works whether or not discord.com offers an API for this.

### What information do I need to provide?

Required: guildId.

### What does it return?

It returns guildId, channels, categories.

### Do I need to be logged in to discord.com?

Yes. It acts as you on discord.com: on your own Chrome it reuses your session, and on a Reduck-hosted browser it loads the discord.com cookies saved by the Reduck extension.

### Does it change anything on discord.com, or only read data?

It only reads. It looks things up on discord.com and changes nothing there.

### How do I run it?

Ask an AI agent connected to Reduck to run reduck/discord.com/list_channels, or run it from a terminal with the Reduck CLI: npx @reduck-ai/cli@latest run --script reduck/discord.com/list_channels

### Who maintains it?

It is part of Reduck's official curated catalogue.

Source: https://reduck.ai/explore/scripts/reduck/discord.com/list_channels
