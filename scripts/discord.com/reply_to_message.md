# Reply to a Discord message

Automatically reply to a Discord message on discord.com. Reply to a specific Discord message, addressed by its own url. Unlike discord.com/post_message, this creates a proper reply — visible as a reference to the original message rather than a plain new post in the channel. Returns the new message's id, channel id, timestamp and content, plus the id of the message it replied to.

- Site: discord.com
- Address: `reduck/discord.com/reply_to_message`
- Updated: 2026-10-01 (v7)
- Author: Reduck AI (reduck)

## Run it

Ask an AI agent connected to Reduck over MCP (`https://mcp.reduck.ai/mcp`) to run `reduck/discord.com/reply_to_message`, or run it from a terminal:

```bash
npx @reduck-ai/cli@latest run --script reduck/discord.com/reply_to_message
```

## Input

- `message` (string, required): The reply text. Discord's own limit is 2000 characters.
- `messageUrl` (string, required): Full url of the message to reply to, e.g. https://discord.com/channels/<guildId>/<channelId>/<messageId>. discord.com/read_messages or discord.com/search_messages return the ids to build one.

## Output

- `sent` (boolean, required)
- `channelId` (string, required)
- `repliedTo` (string, required): The id of the message this replied to, as Discord's own response records it.
- `content` (string | null, optional)
- `messageId` (string | null, optional)
- `timestamp` (string | null, optional)

## FAQ

### What does "Reply to a Discord message" do?

Reply to a specific Discord message, addressed by its own url. Unlike discord.com/post_message, this creates a proper reply — visible as a reference to the original message rather than a plain new post in the channel. Returns the new message's id, channel id, timestamp and content, plus the id of the message it replied to.

### How do I automatically reply to a Discord message on discord.com?

Ask an AI agent connected to Reduck to run reduck/discord.com/reply_to_message, or run it from a terminal with the Reduck CLI: npx @reduck-ai/cli@latest run --script reduck/discord.com/reply_to_message

### Is there a discord.com API to reply to a Discord message?

You do not need one. "Reply to a Discord message" drives the real discord.com pages in a browser, so it works whether or not discord.com offers an API for this.

### What information do I need to provide?

Required: messageUrl, message.

### What does it return?

It returns sent, content, channelId, messageId, repliedTo, timestamp.

### Do I need to be logged in to discord.com?

Yes. It acts as you on discord.com: on your own Chrome it reuses your session, and on a Reduck-hosted browser it loads the discord.com cookies saved by the Reduck extension.

### Does it change anything on discord.com, or only read data?

It makes changes on discord.com, like sending, posting, booking or buying something.

### How do I run it?

Ask an AI agent connected to Reduck to run reduck/discord.com/reply_to_message, or run it from a terminal with the Reduck CLI: npx @reduck-ai/cli@latest run --script reduck/discord.com/reply_to_message

### Who maintains it?

It is part of Reduck's official curated catalogue.

Source: https://reduck.ai/explore/scripts/reduck/discord.com/reply_to_message
