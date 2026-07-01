# GEOly Agent Skills

Agent skills that teach AI agents to use the **[GEOly](https://www.geoly.ai) MCP server**
correctly — picking the right tool, following the org/brand discovery flow, quoting the right
KPI caliber, and avoiding metric-definition pitfalls.

[GEOly](https://www.geoly.ai) is a GEO (Generative Engine Optimization) platform that tracks how
brands are mentioned and cited across AI engines (ChatGPT, Gemini, Perplexity, Grok, Google AI).
Connect your AI agent to GEOly via the MCP server, then add this skill so it queries and reports
your data accurately.

## Install

Using the [skills CLI](https://skills.sh):

```bash
npx skills add geoly-ai/agent-skills
```

This installs the skills below into your project (`.agents/skills/…`) with per-agent links
(Claude Code, Cursor, Windsurf, Codex, Gemini CLI, and more).

You can also just copy a skill's `SKILL.md` into your agent's context, or drop the
`skills/geoly-mcp/` folder into `.claude/skills/`.

## Skills

| Skill | What it does |
|---|---|
| [`geoly-mcp`](skills/geoly-mcp/SKILL.md) | Correct usage of the GEOly MCP server: tool selection across the self/brand and public/industry surfaces, the connection & access model, KPI calibers, recipes, and a full tool catalog. |

## Connecting the GEOly MCP server

Point your MCP client at the hosted URL — **no token to paste**. On first connect the client
runs the OAuth flow in your browser, where you pick the organization and the read/write scope:

```json
{
  "mcpServers": {
    "geoly": {
      "url": "https://app.geoly.ai/api/mcp"
    }
  }
}
```

Config keys vary by client: Cursor and Claude Code use `url`, Windsurf uses `serverUrl`, VS Code
uses `servers` with `"type": "http"`, and Claude Desktop bridges via `npx -y mcp-remote <url>`.
On OpenAI Codex, install the plugin (`codex plugin add geoly-mcp@geoly`) — it authorizes on install.

For headless / CI where no browser is available, a legacy **read-only** static token is still
accepted as `Authorization: Bearer geom_…`.

## Contributing

The canonical source for `geoly-mcp` lives in the GEOly app repo and is mirrored here for
distribution. Tool names, parameters, calibers, limits, and gating are verified against the
codebase. Open an issue if anything is out of date.

## License

© GEOly. Provided for use with the GEOly MCP server.
