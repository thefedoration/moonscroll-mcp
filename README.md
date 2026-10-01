# Moonscroll MCP

**Short Form Video Insights for Instagram, TikTok, Shorts**

This repository packages the **public, remote** Moonscroll Model Context Protocol (MCP) server for easy install in Claude, Cursor, VS Code, and related MCP clients. The backend is **hosted by Moonscroll** — this repo does **not** include or open-source the server implementation.

| | |
|---|---|
| **MCP endpoint** | `https://api.moonscroll.ai/mcp` |
| **Website** | [https://moonscroll.ai/](https://moonscroll.ai/) |
| **API docs** | [https://api.moonscroll.ai/docs/](https://api.moonscroll.ai/docs/) |
| **Privacy** | [https://moonscroll.ai/privacy-policy/](https://moonscroll.ai/privacy-policy/) |
| **Transport** | Streamable HTTP (remote only) |

> **TODO:** Replace every `YOUR_GITHUB_USERNAME` placeholder in this repo (`server.json`, `.cursor-plugin/plugin.json`, `glama.json`, and any README links) with your real GitHub username or org before publishing to the Official MCP Registry, Glama, or GitHub.

## What it does

Moonscroll exposes short-form video insight tools over MCP so agents can research and analyze content on:

- **Instagram** Reels
- **TikTok**
- **YouTube Shorts**

Typical use cases: trend spotting, creator research, competitive briefs, content ideation, and summarizing public short-form performance signals. Exact tools and parameters are defined by the live remote server — see the [API docs](https://api.moonscroll.ai/docs/).

## Remote-only packaging

- There is **no local Node/Python server** to run from this repo.
- There are **no API keys checked in**. If the hosted MCP requires auth (OAuth or a bearer token), configure that in your client — never commit secrets.
- Clients connect directly to `https://api.moonscroll.ai/mcp` over Streamable HTTP.

## Install

### Cursor (recommended: plugin / Marketplace)

This repo is structured as a Cursor plugin (`.cursor-plugin/plugin.json` + root `mcp.json`).

1. Install from the [Cursor Marketplace](https://cursor.com/marketplace) when listed, **or** clone this repo and add it as a local/team plugin.
2. Ensure the Moonscroll MCP server appears under MCP settings and points at `https://api.moonscroll.ai/mcp`.
3. Complete any sign-in / auth flow the client prompts for.

**Manual Cursor config** (`~/.cursor/mcp.json` or project `.cursor/mcp.json`):

```json
{
  "mcpServers": {
    "moonscroll": {
      "url": "https://api.moonscroll.ai/mcp"
    }
  }
}
```

Optional headers (only if Moonscroll documents a static token — do not invent keys):

```json
{
  "mcpServers": {
    "moonscroll": {
      "url": "https://api.moonscroll.ai/mcp",
      "headers": {
        "Authorization": "Bearer ${env:MOONSCROLL_TOKEN}"
      }
    }
  }
}
```

### Claude Code

```bash
claude mcp add --transport http moonscroll https://api.moonscroll.ai/mcp
```

Or project `.mcp.json`:

```json
{
  "mcpServers": {
    "moonscroll": {
      "type": "http",
      "url": "https://api.moonscroll.ai/mcp"
    }
  }
}
```

### Claude Desktop (custom connector)

Add a remote MCP connector with URL `https://api.moonscroll.ai/mcp` in Claude Desktop settings (Custom Connectors / MCP). Prefer OAuth when offered by the host. For header-only auth, follow Anthropic’s current remote MCP guidance.

### VS Code

Create or edit `.vscode/mcp.json`:

```json
{
  "servers": {
    "moonscroll": {
      "type": "http",
      "url": "https://api.moonscroll.ai/mcp"
    }
  }
}
```

## Official MCP Registry (`server.json`)

`server.json` declares this as a **remote** registry entry with Streamable HTTP:

```json
"remotes": [
  {
    "type": "streamable-http",
    "url": "https://api.moonscroll.ai/mcp"
  }
]
```

Namespace placeholder: `io.github.YOUR_GITHUB_USERNAME/moonscroll` — replace `YOUR_GITHUB_USERNAME` before publishing.

## Agent skill

`skills/short-form-video-insights/SKILL.md` is a starter skill for agents using Moonscroll for Instagram / TikTok / Shorts research. Keep tool calls aligned with the live server’s tool list from the MCP session.

## Directory layout

```text
moonscroll-mcp/
├── .cursor-plugin/plugin.json   # Cursor Marketplace manifest
├── assets/logo.svg              # Brand mark (from moonscroll.ai/favicon.svg)
├── skills/short-form-video-insights/SKILL.md
├── glama.json                   # Glama ownership claim (maintainers placeholder)
├── mcp.json                     # Cursor plugin MCP (remote URL)
├── server.json                  # Official MCP Registry remote server
├── smithery.yaml                # Minimal Smithery remote HTTP config
├── LICENSE                      # MIT
├── README.md
└── .gitignore
```

## License

MIT — see [LICENSE](./LICENSE). The hosted Moonscroll API and product remain subject to Moonscroll’s terms and [privacy policy](https://moonscroll.ai/privacy-policy/).

## Links

- Site: [https://moonscroll.ai/](https://moonscroll.ai/)
- MCP: [https://api.moonscroll.ai/mcp](https://api.moonscroll.ai/mcp)
- Docs: [https://api.moonscroll.ai/docs/](https://api.moonscroll.ai/docs/)
- Privacy: [https://moonscroll.ai/privacy-policy/](https://moonscroll.ai/privacy-policy/)
