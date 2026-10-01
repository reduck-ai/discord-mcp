# List Discord servers

Automatically list Discord servers on discord.com. Lists the Discord servers the logged-in account has access to (name + guildId), read from the server sidebar. Requires being logged in.

- Site: discord.com
- Address: `reduck/discord.com/list_servers`
- Updated: 2026-10-01 (v10)
- Author: Reduck AI (reduck)

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

Source: https://reduck.ai/explore/scripts/reduck/discord.com/list_servers
