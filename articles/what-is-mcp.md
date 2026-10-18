# What is MCP

Originally published at <https://meetnewai.com/blog/what-is-mcp> on 2026-10-16 by Kai · 中文版: <https://meetnewai.com/zh/blog/what-is-mcp>

## Summary

MCP, the Model Context Protocol, is how an AI app connects to an external server when it needs to look something up, change a file or call another program. The server offers tools the app can call, data it can read and prompts that are already written, and the app decides when to use them. This short note explains MCP in plain terms and focuses on what to check before you connect one.

Permissions sit on the connection: which directories the server can see, which records it can change and whether it can send requests outward should be clear before you authorize it. Maintenance belongs in the same check, because a server nobody updates should stay out of a daily workflow. The note shows how to read an MCP record on MeetNewAI by the task it completes, how far its permission goes and whether someone maintains it, and recommends connecting one task first, confirming the permission matches what you expected, and only then adding the next server.

## Key points and data

- MCP servers expose tools, readable data and prepared prompts to an AI app.
- Check three things on a record: the task, the permission scope and maintenance status.
- Example records cited in the note were checked on October 14, 2026; protocol notes are at modelcontextprotocol.io.
- Start with one task (search, or reading one document), verify permissions, then add more servers.

## Read the full article

[What is MCP on MeetNewAI →](https://meetnewai.com/blog/what-is-mcp)
