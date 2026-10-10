# List Discord channels

Automatically list Discord channels on discord.com. You get the categories and channels your sidebar shows, top to bottom, with channel IDs and URLs.

- Site: discord.com
- Address: `reduck/discord.com/list_channels`
- Updated: 2026-10-09 (v11)
- Author: Reduck AI (reduck)

## About

Discord's developer API hands a server's channel list to a bot added to that server, and adding one takes the Manage Server permission. Without that, the list to work from is your own sidebar as your signed-in account sees it, scrolled to the bottom, since Discord only keeps the rows near the scroll position on the page. Say you are a plain member of a 120-channel modding server for a city-builder game and only care about #releases and the three channels under "Bug Reports". Grab the guildId from list_servers and run this once. A filter on category plus #releases leaves four URLs to feed read_messages every morning. If one of them is a forum, it needs list_forum_posts instead, and the output will not flag it because there is no channel type field. Folded categories are where people get caught out: Discord removes their already-read channels, so a category with collapsed true comes back short. Unfold it first.

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

## Example output

Shape only: placeholder values generated from the output schema, not a real run.

```json
{
  "guildId": "abc123",
  "channels": [
    {
      "url": "https://example.com/item/123",
      "name": "Example",
      "category": "…",
      "channelId": "abc123"
    }
  ],
  "categories": [
    {
      "name": "Example",
      "channelId": "abc123",
      "collapsed": true
    }
  ]
}
```

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

### Why are some channels missing from the result?

Only channels in your own sidebar come back. A folded category (collapsed true) returns just its unread channels, and with Hide Muted Channels switched on for that server the muted ones are not there either. On servers with Community Onboarding, channels you never picked stay out of your list until you add them under Channels & Roles > Browse Channels.

### Can I export a Discord server's channel list to a spreadsheet?

The channels array is already flat, one row per channel with channelId, name, category and url, so it goes into a CSV or a sheet as it is. Categories come in a second array with their own channelId and the collapsed flag. Row order is sidebar order; there is no position number, and topics, permissions, channel types and unread counts are not included.

### Can I tell text, announcement and forum channels apart in the result?

The output has no type field, so text, announcement and forum channels look the same; only voice and stage channels stand out, with url null because clicking one joins the call instead of opening a page. Forums have to be picked out by name and sent to list_forum_posts, since read_messages does not read a forum channel. Threads are skipped altogether.

### How do I get the IDs of all channels in a Discord server at once?

Discord's own way is to turn on Developer Mode under User Settings > Advanced, then right-click each channel and choose Copy Channel ID, one at a time. List Discord channels returns the channelId of every channel and category in your sidebar in one run. Each channel URL ends with that same ID.

Source: https://reduck.ai/explore/scripts/reduck/discord.com/list_channels
