# Bento MCP for Cursor

Connect Cursor to Bento's hosted MCP server. The plugin exposes Bento tools for subscriber management, tags, fields, events, broadcasts, automations, email templates, analytics, delivery troubleshooting, and Bento Chat workflows.

## Install

Install `Bento MCP` from the Cursor Marketplace, then open the plugin's configuration and provide:

- **Bento publishable key** — your Bento API publishable key
- **Bento secret key** — your Bento API secret key
- **Bento site UUID** — the Bento site UUID for the account to use

Cursor substitutes these values into request headers at runtime. This repository contains only variable names; never commit real credentials here.

After configuration, enable the `bento-mcp` server in Cursor's Customize page and start a new Agent conversation.

## Grok Bot

Grok Bot can use MCP servers and packaged connectors from its desktop **Settings → Plugins** surface. If this plugin is available in its Marketplace, install it there, enable `bento-mcp`, and complete the three plugin variables when prompted.

The plugin declares these secret-backed variables:

```text
BENTO_PUBLISHABLE_KEY
BENTO_SECRET_KEY
BENTO_SITE_UUID
```

Grok Bot may show a secure secret request or browser takeover for supported connections. This Bento MCP currently authenticates with Bento-specific headers rather than OAuth, so a three-field auth card is controlled by Grok Bot's plugin UI and is not guaranteed for every account or rollout. Never send credentials in ordinary Bot chat or commit them to this repository.

For Grok Bot Team or Enterprise, an administrator may need to enable the plugin in the Cursor team Plugins page, enter its variables, and allowlist `https://mcp.bentonow.com/mcp`. MCP authentication is shared between Cursor and Grok Bot in that setup.

Start with a read-only Bot request such as: “List my latest Bento broadcasts.”

## Local testing

Cursor discovers local plugins from `~/.cursor/plugins/local`. Copy the package there:

```bash
mkdir -p ~/.cursor/plugins/local
cp -R /absolute/path/to/bento-cursor-sdk ~/.cursor/plugins/local/bento-mcp
```

Cursor 3.18.9 rejects symlink targets outside this directory, so use a copy for local testing.

Restart Cursor or run **Developer: Reload Window**, then configure the plugin from **Customize → Plugins**. Local plugin imports must be allowed by your Cursor/team settings.

## Configuration contract

The plugin uses Bento's hosted Streamable HTTP endpoint:

```text
https://mcp.bentonow.com/mcp
```

The remote Worker stores no Bento customer credentials. It reads the three headers for each request and discards them after the request.

## License

MIT
