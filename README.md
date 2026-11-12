# openmarket-indicators

Workspace for building indicators for [OpenMarket](https://openmarket.xyz), driving charts through the [OpenMarket chart MCP](https://mcp.openmarket.xyz/llms.txt), and managing the setup overall.

## Connect an agent to the chart MCP

```sh
# Claude Code
claude mcp add --scope user --transport http openmarket https://mcp.openmarket.xyz/

# Codex
codex mcp add openmarket --url https://mcp.openmarket.xyz/
```

Then authenticate in the browser (Claude Code: `/mcp`, Authenticate). Pick "Read only" or "Read and control charts" on the sign-in page.

## Layout

| Path | Purpose |
|---|---|
| `indicators/` | Indicator source (`overlays`, `oscillators`, `volume`, `utilities`) |
| `strategies/` | Strategy scripts |
| `docs/` | Platform and MCP notes |
| `scratch/` | Throwaway experiments (gitignored) |
| `.agents/skills/` | Agent skills (Pine Script) |

See `AGENTS.md` for agent conventions.
