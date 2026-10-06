# Read Discord messages

Automatically read Discord messages on discord.com. Pull the latest messages of a Discord channel, DM or thread you can open, newest first, up to a count you set.

- Site: discord.com
- Address: `reduck/discord.com/read_messages`
- Updated: 2026-10-05 (v12)
- Author: Reduck AI (reduck)

## About

Point it at any Discord channel, DM, group DM or thread your account can open and you get its latest messages back, newest first, as many as you ask for. Discord's own API route is a bot that a server admin has to add, and that bot also needs the Message Content intent before it sees any text. This reads as the account you are already signed in with, so it sees what you see in the app and nothing more. A typical run: a volunteer mod on a 3,000-member indie game server pulls the last 150 messages from a bug reports channel each morning, has Claude group the repeated crash reports, then works through the worst ones by hand. Text arrives as Discord stores it, so mentions stay as <@id>. Image-only posts come back with empty text, and reactions and reply links are not returned.

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

## Example output

Shape only: placeholder values generated from the output schema, not a real run.

```json
{
  "count": 3,
  "messages": [
    {
      "author": "…",
      "content": "…",
      "messageId": "abc123",
      "timestamp": "…",
      "authorDisplayName": "…"
    }
  ],
  "channelId": "abc123"
}
```

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

### How many messages can I read from a Discord channel in one run?

You set a count with limit, 20 by default, and messages come back newest first. Older history loads by scrolling the channel up, and the run stops at the start of the channel or after 40 scroll rounds, so a very long backlog can come back shorter than asked. There is no date filter, so it always starts from the newest message. Run Discord scripts one at a time on the same account, because parallel runs can end in a signed-out or other-tab error even when you are signed in.

### Can I read a Discord DM, group DM, thread or forum post?

Discord treats a DM, a group DM, a thread and a forum post each as a channel with its own url, so any of them reads like a normal channel. Copy the link from the address bar, or use Copy Link on a thread (DMs look like discord.com/channels/@me/<id>). The one thing it refuses is a forum channel's front page, which is a list of posts rather than messages: get the post urls from discord.com/list_forum_posts and read them one at a time. Voice channel chats have not been tested.

### What happens if I read a Discord server I have not joined?

Reading a server you have not joined, or a channel your roles hide, stops with a No access error, because it only sees what the signed-in account sees in Discord. A mistyped channel id is caught too: you get an error instead of whichever channel Discord quietly falls back to.

### How do I turn the <@id> mentions in Discord messages into names?

Mentions come back as raw ids like <@123456789>, and the display name returned for each author is the account's global one, not the nickname a member set on that server. Nothing in this run maps ids to people, so you have to resolve them yourself, for example by matching them against authors who appear elsewhere in the same batch.

Source: https://reduck.ai/explore/scripts/reduck/discord.com/read_messages
