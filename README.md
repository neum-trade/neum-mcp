<p align="center"><img src="assets/neum-icon.png" width="72" alt="NEUM"></p>

# NEUM MCP server

**US stock price levels, level crossings and earnings dates inside your AI assistant.**
NEUM is a remote [Model Context Protocol](https://modelcontextprotocol.io) server for Claude, Claude Code, Cursor, VS Code and other MCP clients.

[![MCP Registry](https://img.shields.io/badge/MCP%20Registry-trade.neum%2Fmcp-1f6feb)](https://registry.modelcontextprotocol.io/v0.1/servers?search=trade.neum/mcp)
[![Guide](https://img.shields.io/badge/guide-neum.trade%2Fmcp-dcb162)](https://neum.trade/mcp)

> Educational data from automated models, not investment advice or a recommendation to buy, sell or hold any security.

## Server

```
https://api.neum.trade/mcp
```

Streamable HTTP · OAuth 2.1 sign-in with dynamic client registration · needs an active [NEUM](https://neum.trade) plan (NEUM is in Beta; [join the waitlist](https://neum.trade/waitlist)).

## Set up

**Claude (web, desktop, mobile):** Customize → Connectors → **+ Add** → **Add custom connector**, name it `NEUM`, paste the address, then sign in to NEUM and select **Allow**. [Step-by-step guide](https://neum.trade/claude)

**Claude Code:**

```bash
claude mcp add --transport http neum https://api.neum.trade/mcp
```

Then run `/mcp` in Claude Code and authenticate.

**Cursor** (`~/.cursor/mcp.json`):

```json
{
  "mcpServers": {
    "neum": { "url": "https://api.neum.trade/mcp" }
  }
}
```

**VS Code / GitHub Copilot** (`.vscode/mcp.json`, or **MCP: Add Server** → HTTP):

```json
{
  "servers": {
    "neum": { "type": "http", "url": "https://api.neum.trade/mcp" }
  }
}
```

**Any other MCP client:** add the address as a remote (HTTP) server and sign in when asked. Full setup notes: **[neum.trade/mcp](https://neum.trade/mcp)**.

## What you can ask

- "What are the price levels for NVDA and AMD right now?"
- "Which tickers on my watchlist had a level crossed this week?"
- "Show me MU's recent level history and how each set ended."
- "Which tickers on my watchlist report earnings in the next two weeks?"
- "Add SBUX to my Tech list." (your AI asks you to confirm first)

## Tools

| Tool | What it does | Access |
|---|---|---|
| `get_price_levels` | Current Long above / Short below levels, reference targets and any active model event (up to 20 tickers) | Read |
| `get_level_history` | Recent level sets for one ticker and how each ended | Read |
| `list_upcoming_events` | Earnings, dividends, splits, AGMs and M&A in a date range | Read |
| `get_track_record` | NEUM's overall published model history | Read |
| `search_tickers` | Find covered US tickers by symbol or company name | Read |
| `list_watchlists` | Your NEUM watchlists and which one is active | Read |
| `add_to_watchlist` | Add a ticker to a watchlist | Write, confirms first |
| `remove_from_watchlist` | Remove a ticker from a watchlist | Write, confirms first |
| `set_active_watchlist` | Switch the watchlist NEUM follows | Write, confirms first |

The server cannot place trades, move money, or read billing details.

## Sign-in and privacy

You sign in and approve access on a NEUM page; the AI app never sees your password. NEUM logs each request the app sends (tool, details, result, timing) for 90 days to run and secure the service, and never receives your conversations. Disconnect any time in NEUM under **Account → Connected apps**. See the [Privacy Policy](https://neum.trade/privacy) and [Terms](https://neum.trade/terms).

## Support

support@rapidaigo.com · NEUM is a product of RapidAIGo Pvt. Ltd.

This repository contains documentation only. The server itself is hosted by NEUM.
