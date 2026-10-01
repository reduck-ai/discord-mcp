# Send Discord DM

Automatically send Discord DM on discord.com. Send a direct message to a Discord user, addressed by their username. Opens (or reuses) the one-to-one DM conversation and posts the message there. Returns sent, the created message's messageId, the DM channelId, timestamp, and the content as Discord stored it, plus the recipient's resolved handle so the message is provably not sent to a near-name match. This is a write and the recipient is notified: confirm the exact recipient and text with the user before running, and note that approval for one message does not carry over to another.

- Site: discord.com
- Address: `reduck/discord.com/send_dm`
- Updated: 2026-10-01 (v13)
- Author: Reduck AI (reduck)

## Run it

Ask an AI agent connected to Reduck over MCP (`https://mcp.reduck.ai/mcp`) to run `reduck/discord.com/send_dm`, or run it from a terminal:

```bash
npx @reduck-ai/cli@latest run --script reduck/discord.com/send_dm
```

## Input

- `userId` (string, required): The recipient's Discord user id, e.g. from discord.com/find_member_id or the author.id of discord.com/search_messages.
- `message` (string, required): The message text. Discord's own limit is 2000 characters.
- `expectedUsername` (string, required): The recipient's username, checked against the one Discord returns for that id before anything is typed. A mismatch stops the run without sending.
- `dry_run` (boolean, optional): When true, the recipient is checked and the conversation opened, then the run stops before typing: nothing is sent, sent comes back false.

## Output

- `sent` (boolean, required): False on a dry run.
- `channelId` (string, required): The one-to-one DM channel.
- `recipient` (string, required): The recipient's username as Discord returned it for that id, not echoed from the input.
- `content` (string | null, optional): The content as Discord stored it. Null on a dry run.
- `dry_run` (boolean, optional)
- `messageId` (string | null, optional): Null on a dry run.
- `timestamp` (string | null, optional)

## FAQ

### What does "Send Discord DM" do?

Send a direct message to a Discord user, addressed by their username. Opens (or reuses) the one-to-one DM conversation and posts the message there. Returns sent, the created message's messageId, the DM channelId, timestamp, and the content as Discord stored it, plus the recipient's resolved handle so the message is provably not sent to a near-name match. This is a write and the recipient is notified: confirm the exact recipient and text with the user before running, and note that approval for one message does not carry over to another.

### How do I automatically send Discord DM on discord.com?

Ask an AI agent connected to Reduck to run reduck/discord.com/send_dm, or run it from a terminal with the Reduck CLI: npx @reduck-ai/cli@latest run --script reduck/discord.com/send_dm

### Is there a discord.com API to send Discord DM?

You do not need one. "Send Discord DM" drives the real discord.com pages in a browser, so it works whether or not discord.com offers an API for this.

### What information do I need to provide?

Required: userId, expectedUsername, message. Optional: dry_run.

### What does it return?

It returns sent, content, dry_run, channelId, messageId, recipient, timestamp.

### Do I need to be logged in to discord.com?

Yes. It acts as you on discord.com: on your own Chrome it reuses your session, and on a Reduck-hosted browser it loads the discord.com cookies saved by the Reduck extension.

### Does it change anything on discord.com, or only read data?

It makes changes on discord.com, like sending, posting, booking or buying something.

### How do I run it?

Ask an AI agent connected to Reduck to run reduck/discord.com/send_dm, or run it from a terminal with the Reduck CLI: npx @reduck-ai/cli@latest run --script reduck/discord.com/send_dm

### Who maintains it?

It is part of Reduck's official curated catalogue.

Source: https://reduck.ai/explore/scripts/reduck/discord.com/send_dm
