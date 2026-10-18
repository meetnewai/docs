# MCP servers and agent skills on MeetNewAI

- MCP servers: <https://meetnewai.com/mcp> · 中文 <https://meetnewai.com/zh/mcp>
- Agent skills: <https://meetnewai.com/skills>
- Background: [What is MCP](../articles/what-is-mcp.md)

Each MCP record says what task the server completes, how far its permissions go and whether it is maintained, and gives install snippets taken from the server's official README or docs (with the check date).

## Install patterns used on MCP pages

A **hosted** server is added by URL:

```bash
claude mcp add --transport http vaneform https://vaneform.com/mcp
```

```json
{
  "mcpServers": {
    "vaneform": { "url": "https://vaneform.com/mcp" }
  }
}
```

A **local** server runs a command:

```bash
claude mcp add playwright -- npx @playwright/mcp@latest
```

```json
{
  "mcpServers": {
    "playwright": { "command": "npx", "args": ["@playwright/mcp@latest"] }
  }
}
```

Servers that need a credential take it as an environment variable or header placeholder (for example `-e NOTION_TOKEN='<NOTION_TOKEN>'`). Never paste a real token into a shared config.

These two examples match the [Vaneform MCP](https://meetnewai.com/mcp/vaneform-mcp) and [Playwright MCP](https://meetnewai.com/mcp/playwright-mcp) records as checked on 2026-10-18. Always read the current record and the official README before installing.

## Before you connect a server

1. Does it complete the task you need?
2. Which files, records or network calls can it reach?
3. Is it still maintained?

Connect one server for one task first, confirm the permissions match what you expected, then add the next.

## Finding servers and skills programmatically

```bash
curl -sS https://meetnewai.com/api/tools.json \
  | jq -r '.items[] | select(.kind=="mcp" or .kind=="skill") | "\(.kind)\t\(.name)\t\(.listingUrl)"'
```
