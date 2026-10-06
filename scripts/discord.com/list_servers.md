# List Discord servers

Automatically list Discord servers on discord.com. The name and numeric ID of each server in your sidebar, in the order you have them arranged.

- Site: discord.com
- Address: `reduck/discord.com/list_servers`
- Updated: 2026-10-05 (v10)
- Author: Reduck AI (reduck)

## About

Searching a server's messages or listing its channels starts from its guildId, and Discord only gives those out one server at a time, as the first number after /channels/ in a channel's URL or through Copy Server ID once Developer Mode is on. Reading the sidebar gets you all of them in one go, each server's name next to its guildId. Say a Paper plugin author sits in 70 Discord servers, most of them Minecraft communities, and asks Claude where people reported a crash with the plugin this week. Claude lists the servers, picks out the eight plugin-support ones by name, and runs search_messages on each guildId, since that search covers one server per call. You get names and IDs only, no icons, member counts or roles. Only the account signed in to that browser is covered, and a second open Discord tab can make the run stop with an error, so queue Discord jobs one after another.

## Run it

Ask an AI agent connected to Reduck over MCP (`https://mcp.reduck.ai/mcp`) to run `reduck/discord.com/list_servers`, or run it from a terminal:

```bash
npx @reduck-ai/cli@latest run --script reduck/discord.com/list_servers
```

## Input

It takes no input.

## Output

- `count` (integer, required): Total advertised by Discord (aria-setsize on the sidebar).
- `servers` (array, required): Servers in sidebar order.

## Example output

Shape only: placeholder values generated from the output schema, not a real run.

```json
{
  "count": 3,
  "servers": [
    {
      "name": "Example",
      "guildId": "abc123"
    }
  ]
}
```

## FAQ

### What does "List Discord servers" do?

Lists the Discord servers the logged-in account has access to (name + guildId), read from the server sidebar. Requires being logged in.

### How do I automatically list Discord servers on discord.com?

Ask an AI agent connected to Reduck to run reduck/discord.com/list_servers, or run it from a terminal with the Reduck CLI: npx @reduck-ai/cli@latest run --script reduck/discord.com/list_servers

### Is there a discord.com API to list Discord servers?

You do not need one. "List Discord servers" drives the real discord.com pages in a browser, so it works whether or not discord.com offers an API for this.

### What information do I need to provide?

Nothing. It takes no input.

### What does it return?

It returns count, servers.

### Do I need to be logged in to discord.com?

Yes. It acts as you on discord.com: on your own Chrome it reuses your session, and on a Reduck-hosted browser it loads the discord.com cookies saved by the Reduck extension.

### Does it change anything on discord.com, or only read data?

It only reads. It looks things up on discord.com and changes nothing there.

### How do I run it?

Ask an AI agent connected to Reduck to run reduck/discord.com/list_servers, or run it from a terminal with the Reduck CLI: npx @reduck-ai/cli@latest run --script reduck/discord.com/list_servers

### Who maintains it?

It is part of Reduck's official curated catalogue.

### Can I see which servers another Discord user is in?

List Discord servers only reads the signed-in account's sidebar, so it shows that account's servers and nobody else's. The closest Discord offers for another person is the Mutual Servers tab on their profile, which shows only the servers the two of you share.

### Can it find public Discord servers to join?

List Discord servers returns only servers the account has already joined, so it will not help you find new ones. Public Community servers are browsed in Discord's Server Discovery, the compass icon at the bottom of the server list. Once you have an invite link, discord.com/join_server_via_invite joins the server and puts you on its member list.

### Will it return all my servers if I'm in a lot of them or use folders?

List Discord servers reads the sidebar as Discord has rendered it, without scrolling and without opening server folders, so servers inside a collapsed folder may be missing. With no folders, the count field should equal the number of servers returned; folders throw that comparison off, so expand them in Discord first when you need every server. For scale, an account can join 100 servers on a free or Nitro Basic plan and 200 on full Nitro.

Source: https://reduck.ai/explore/scripts/reduck/discord.com/list_servers
