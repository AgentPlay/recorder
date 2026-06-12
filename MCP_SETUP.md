# Robinhood Agentic Trading — MCP Connection

This repo contains an MCP client config (`.mcp.json`) that points an MCP-capable
agent at Robinhood's official Agentic Trading server.

## What this config does
- Registers the remote MCP server `robinhood-trading` at
  `https://agent.robinhood.com/mcp/trading`.
- It does **not** place trades by itself and stores no credentials.

## Chosen setup: capped balance + fully autonomous
The control approach here is **fully autonomous (no manual approvals)**, with risk
bounded by **only funding the dedicated account with a small, loss-tolerable
amount**. The capped balance is the safety mechanism, so the agent can run
hands-off.

## Steps you must complete (only the account holder can do these)
1. In the Robinhood app, enable **Agentic Trading** and open the dedicated
   agentic trading account.
2. Fund that dedicated account with only a small amount you're comfortable
   losing. This cap is your risk limit. Your main portfolio stays separate.
3. In setup, choose **fully autonomous (no approvals)** as the control mode.
4. Connect your agent — on first connection the client completes Robinhood's
   OAuth authorization. Approve it in-app.
5. Run the agent on a persistent host (not an ephemeral session) so it can
   trade continuously.

## Keep on, even in autonomous mode (no cost to automation)
- **Push notifications** — leave enabled so you see each trade as it happens.
- **One-tap disconnect** — your kill switch in the Robinhood app if anything
  looks off.

## Safety notes
- You receive a push notification on every trade and a real-time activity feed.
- You can disconnect the agent at any time from the Robinhood app.
- Beta scope is currently US equities only.
- Top up the dedicated account deliberately; never raise the cap beyond what you
  can afford to lose.

## Verify before trusting
Confirm the endpoint URL against Robinhood's official documentation at
robinhood.com before authenticating. Do not authorize a third-party "trading
agent" endpoint.
