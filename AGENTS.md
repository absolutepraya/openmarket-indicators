# OpenMarket workspace

Workspace for building indicators ("plugins") for OpenMarket, driving charts through the OpenMarket chart MCP, and managing the OpenMarket setup overall.

## Chart MCP

- Server: `openmarket`, Streamable HTTP at `https://mcp.openmarket.xyz/`. Full reference: `https://mcp.openmarket.xyz/llms.txt` (re-read it when behavior is unclear, it is the source of truth).
- Connect (user scope, OAuth, no token needed): `claude mcp add --scope user --transport http openmarket https://mcp.openmarket.xyz/`, then `/mcp` > Authenticate. The browser sign-in picks the access level (read only, or read and control charts).
- Never put an agent token in this repo or in chat. If the token fallback is needed, keep it in local client config only.
- When given "chart <id>": call `chart_workspace_select` with that workspaceId first, then `chart_status {}`, then `chart_refresh {}` and report symbol, timeframe and indicators. Without a named chart, call `chart_list` and ask. Never assume the active workspace.
- Prefer `chart_read` over `chart_screenshot` for numbers. Use `symbol_resolve` before `chart_symbol` when unsure of a venue or ticker.
- Offer one small visible change and wait for a yes before changing a chart. Do not place orders unless explicitly asked.

## Layout

- `indicators/` indicator source, grouped by kind: `overlays/`, `oscillators/`, `volume/`, `utilities/`. One indicator per folder: `<name>/<name>.pine` plus a short `README.md` (what it plots, inputs, notes).
- `strategies/` strategy scripts, same one-folder-per-script convention.
- `docs/` notes on the OpenMarket platform, MCP quirks, conventions.
- `scratch/` throwaway experiments, gitignored except `.gitkeep`.

## Conventions

- Indicators are Pine Script v6 unless OpenMarket's chart tooling says otherwise. Use the `pinescript` skill (`.agents/skills/pinescript`) and check the docs for version-specific syntax before writing code.
- kebab-case folder and file names.
- Record anything learned about what OpenMarket's chart actually supports (indicator formats, limits) in `docs/`.
