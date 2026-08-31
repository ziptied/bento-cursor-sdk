# Bento MCP for Cursor

Connect Cursor to Bento's hosted MCP server for subscriber management, tags, fields, events, broadcasts, automations, email templates, analytics, delivery troubleshooting, and Bento Chat workflows.

## Requirements

- Cursor with plugin support
- A Bento account with an API publishable key, secret key, and site UUID
- Network access to `https://mcp.bentonow.com/mcp`

## Install

After the plugin is approved and listed, install **Bento MCP** from the Cursor Marketplace.

Open **Customize → Plugins → Bento MCP → Configure**, enter the three Bento values, and enable the `bento-mcp` server under **Customize → MCPs**. Start a new Agent conversation after configuration.

## Configuration

The plugin declares these required variables:

```text
BENTO_PUBLISHABLE_KEY
BENTO_SECRET_KEY
BENTO_SITE_UUID
```

Cursor substitutes the values into the request headers at runtime. Credentials are sent as request headers and are never committed to this repository. Do not paste credentials into chat, documentation, or issue reports.

The MCP endpoint is:

```text
https://mcp.bentonow.com/mcp
```

## Grok Bot

This package is a Cursor plugin. A public GitHub repository does not install or activate it in Grok Bot.

To use Bento directly in Grok Bot, add the hosted endpoint as a custom MCP connector and complete its required authentication. For team or enterprise accounts, an administrator may also need to provision the connector or plugin and allowlist `https://mcp.bentonow.com/mcp`.

The Cursor variable schema does not guarantee that Grok Bot will display a three-field authentication card; that depends on Grok Bot's connector flow. Never send Bento credentials in ordinary Bot chat.

## Local testing

Cursor discovers local plugins from `~/.cursor/plugins/local`. Copy this repository into that directory, then run **Developer: Reload Window**:

```bash
mkdir -p ~/.cursor/plugins/local
cp -R /absolute/path/to/bento-cursor-sdk ~/.cursor/plugins/local/bento-mcp
```

Configure the local plugin from **Customize → Plugins**. Use a copied directory rather than a symlink so the committed logo and other relative assets resolve consistently.

## License

MIT
