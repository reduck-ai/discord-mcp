# Search Discord server messages

Automatically search Discord server messages on discord.com. Search one Discord server's message history with Discord's own search, as the signed-in account, newest first. Search by words (content), and narrow by authors, channels, mentioned users and content type, each given as ids: get user ids from discord.com/get_member_list and channel ids from discord.com/list_channels. Returns one page of up to 25 matching messages with their author, text, time and link, Discord's total count of matches, and next_offset to read the next page (null on the last one). Fails with a clear error when the browser is not signed in to Discord, when the account is not a member of the server or can see no text channel in it, or when Discord is still indexing the server. Direct messages are not searched.

- Site: discord.com
- Address: `reduck/discord.com/search_messages`
- Updated: 2026-10-19 (v33)
- Author: Reduck AI (reduck)

## Run it

Ask an AI agent connected to Reduck over MCP (`https://mcp.reduck.ai/mcp`) to run `reduck/discord.com/search_messages`, or run it from a terminal:

```bash
npx @reduck-ai/cli@latest run --script reduck/discord.com/search_messages
```

## Input

- `guildId` (string, required): Server id to search, from discord.com/list_servers.
- `has` (array, optional): Only messages that include this kind of content.
- `offset` (integer, optional): How many hits to skip: pass next_offset of the previous answer to read the next page.
- `content` (string, optional): Words the messages must contain (plain words; Discord operators such as from: or in: are rejected: use the filter arguments). Optional when a filter is given.
- `mentions` (array, optional): Only messages that mention these users (user ids).
- `authorIds` (array, optional): Only messages sent by these users (user ids, from discord.com/get_member_list).
- `channelIds` (array, optional): Only messages in these channels (channel ids, from discord.com/list_channels).

## Output

- `offset` (integer, required)
- `guildId` (string, required)
- `messages` (any, required)
- `count` (integer, optional)
- `complete` (boolean, optional): True when no hits remain after this page.
- `next_offset` (integer | null, optional): Pass as offset to read the next page; null on the last page.
- `total_results` (integer | null, optional): Discord's own count of matching messages.

## FAQ

### What does "Search Discord server messages" do?

Search one Discord server's message history with Discord's own search, as the signed-in account, newest first. Search by words (content), and narrow by authors, channels, mentioned users and content type, each given as ids: get user ids from discord.com/get_member_list and channel ids from discord.com/list_channels. Returns one page of up to 25 matching messages with their author, text, time and link, Discord's total count of matches, and next_offset to read the next page (null on the last one). Fails with a clear error when the browser is not signed in to Discord, when the account is not a member of the server or can see no text channel in it, or when Discord is still indexing the server. Direct messages are not searched.

### How do I automatically search Discord server messages on discord.com?

Ask an AI agent connected to Reduck to run reduck/discord.com/search_messages, or run it from a terminal with the Reduck CLI: npx @reduck-ai/cli@latest run --script reduck/discord.com/search_messages

### Is there a discord.com API to search Discord server messages?

You do not need one. "Search Discord server messages" drives the real discord.com pages in a browser, so it works whether or not discord.com offers an API for this.

### What information do I need to provide?

Required: guildId. Optional: has, offset, content, mentions, authorIds, channelIds.

### What does it return?

It returns count, offset, guildId, complete, messages, next_offset, total_results.

### Do I need to be logged in to discord.com?

Yes. It acts as you on discord.com: on your own Chrome it reuses your session, and on a Reduck-hosted browser it loads the discord.com cookies saved by the Reduck extension.

### Does it change anything on discord.com, or only read data?

It only reads. It looks things up on discord.com and changes nothing there.

### How do I run it?

Ask an AI agent connected to Reduck to run reduck/discord.com/search_messages, or run it from a terminal with the Reduck CLI: npx @reduck-ai/cli@latest run --script reduck/discord.com/search_messages

### Who maintains it?

It is part of Reduck's official curated catalogue.

Source: https://reduck.ai/explore/scripts/reduck/discord.com/search_messages
