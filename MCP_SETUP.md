# Robinhood Agentic Trading — MCP Connection

This repo contains an MCP client config (`.mcp.json`) that points an MCP-capable
agent at Robinhood's official Agentic Trading server.

## What this config does
- Registers the remote MCP server `robinhood-trading` at
  `https://agent.robinhood.com/mcp/trading`.
- It does **not** place trades by itself and stores no credentials.

## Steps you must complete (only the account holder can do these)
1. In the Robinhood app, enable **Agentic Trading** and open the dedicated
   agentic trading account.
2. Fund that dedicated account with only the amount you're willing to put under
   agent control. Your main portfolio stays separate.
3. Choose your control mode: **require manual approval** for each trade, or
   **fully autonomous** (no approvals).
4. Connect your agent — on first connection the client completes Robinhood's
   OAuth authorization. Approve it in-app.
5. Run the agent on a persistent host (not an ephemeral session) if you want it
   to trade continuously.

## Safety notes
- You receive a push notification on every trade and a real-time activity feed.
- You can disconnect the agent at any time from the Robinhood app.
- Beta scope is currently US equities only.

## Verify before trusting
Confirm the endpoint URL against Robinhood's official documentation at
robinhood.com before authenticating. Do not authorize a third-party "trading
agent" endpoint.
