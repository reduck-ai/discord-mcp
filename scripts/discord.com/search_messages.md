# Search Discord server messages

Automatically search Discord server messages on discord.com. Search a Discord server's message history, newest first, using Discord's own search, as the signed-in account: it reaches every server that account is in, with no bot to invite. The query accepts Discord's search syntax (plain words, or filters like from:, in:, has:, before:, during:), so scoping to a channel or author is done in the query itself. Returns per hit: messageId, channelId, url, author (id, handle, name), content, timestamp, plus total_results as Discord reports it and complete, which is false when more hits exist beyond the page read. Discord returns search hits with surrounding context messages; only the hits themselves are returned. It searches one server at a time; for direct messages (DMs), list the conversations with discord.com/list_dms and read one with discord.com/read_messages.

- Site: discord.com
- Address: `reduck/discord.com/search_messages`
- Updated: 2026-10-01 (v9)
- Author: Reduck AI (reduck)

## Run it

Ask an AI agent connected to Reduck over MCP (`https://mcp.reduck.ai/mcp`) to run `reduck/discord.com/search_messages`, or run it from a terminal:

```bash
npx @reduck-ai/cli@latest run --script reduck/discord.com/search_messages
```

## Input

- `query` (string, required): What to search for. Discord's own search syntax works here, e.g. 'deploy', 'from:someone deploy', 'in:general has:link'. Always use the English keywords (from:/in:/has:/mentions:) regardless of the signed-in account's Discord display language -- the script translates them internally.
- `guildId` (string, required): Server id to search, e.g. from discord.com/list_servers.
- `limit` (integer, optional): How many hits to return, newest first. Discord serves 25 per page and this reads one page, so 25 is the maximum; total_results tells you how many exist.

## Output

- `count` (integer, required)
- `query` (string, required)
- `guildId` (string, required)
- `messages` (array, required)
- `complete` (boolean, optional): True when every hit Discord reported was returned; false when more exist beyond this page.
- `total_results` (integer | null, optional): Discord's own count of matching messages, which can exceed the number returned.

## FAQ

### What does "Search Discord server messages" do?

Search a Discord server's message history, newest first, using Discord's own search, as the signed-in account: it reaches every server that account is in, with no bot to invite. The query accepts Discord's search syntax (plain words, or filters like from:, in:, has:, before:, during:), so scoping to a channel or author is done in the query itself. Returns per hit: messageId, channelId, url, author (id, handle, name), content, timestamp, plus total_results as Discord reports it and complete, which is false when more hits exist beyond the page read. Discord returns search hits with surrounding context messages; only the hits themselves are returned. It searches one server at a time; for direct messages (DMs), list the conversations with discord.com/list_dms and read one with discord.com/read_messages.

### How do I automatically search Discord server messages on discord.com?

Ask an AI agent connected to Reduck to run reduck/discord.com/search_messages, or run it from a terminal with the Reduck CLI: npx @reduck-ai/cli@latest run --script reduck/discord.com/search_messages

### Is there a discord.com API to search Discord server messages?

You do not need one. "Search Discord server messages" drives the real discord.com pages in a browser, so it works whether or not discord.com offers an API for this.

### What information do I need to provide?

Required: guildId, query. Optional: limit.

### What does it return?

It returns count, query, guildId, complete, messages, total_results.

### Do I need to be logged in to discord.com?

Yes. It acts as you on discord.com: on your own Chrome it reuses your session, and on a Reduck-hosted browser it loads the discord.com cookies saved by the Reduck extension.

### Does it change anything on discord.com, or only read data?

It only reads. It looks things up on discord.com and changes nothing there.

### How do I run it?

Ask an AI agent connected to Reduck to run reduck/discord.com/search_messages, or run it from a terminal with the Reduck CLI: npx @reduck-ai/cli@latest run --script reduck/discord.com/search_messages

### Who maintains it?

It is part of Reduck's official curated catalogue.

Source: https://reduck.ai/explore/scripts/reduck/discord.com/search_messages
