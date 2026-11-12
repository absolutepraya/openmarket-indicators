# Chart MCP notes

Source: https://mcp.openmarket.xyz/llms.txt

Startup sequence after connecting: `chart_workspace_select` (if a chart id was given) -> `chart_status {}` -> `chart_refresh {}` -> report symbol, timeframe, indicators.

Scopes: `mcp:read`, `mcp:chart` (change charts), `mcp:trade` (orders, needs arming in the tab), `mcp:alerts` (alert_* and watchlist_* tools).

Market data without a tab: `metric_get`, `points`, `markets`, `metric_screen`, `market_screen`. Free plan data rate is 10 weight/min.

Add findings below as we learn them (supported indicator formats, quirks, limits).
