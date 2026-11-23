---
name: connect-qonvert
description: Connect or reconnect a Qonvert project in ChatGPT or Claude and verify the authorized project with read-only tools. Use when onboarding someone to Qonvert MCP or diagnosing a missing, expired, or wrong-project connection.
license: MIT
---

# Connect Qonvert

This skill is free under MIT. Qonvert account access and host features depend on what the user already has available.

## Connect the intended project

- Ask which host and Qonvert project to connect if either is unclear. If Qonvert tools are already available, call `get_project` first. If it returns the intended project, reuse the connection.
- If the plugin already provides Qonvert, open its connection settings and choose **Connect**. For a manual connection, use the official HTTPS MCP URL `https://mcp.qonvert.ai/mcp` with OAuth.
- **ChatGPT:** Open **Plugins**, select **+ → Add custom MCP server**, enter the URL and select OAuth. If the host offers Client ID Metadata Documents (CIMD), use it. Workspace policy may restrict custom servers. See the [OpenAI setup guide](https://developers.openai.com/api/docs/guides/custom-mcp-server).
- **Claude:** Open **Plugins → Add → Custom → Web** (called **Customize → Connectors** in some versions). Enter the URL, require sign-in, and keep Claude's published OAuth client identity where offered. If the host requires a separately registered client, stop and ask the Qonvert administrator for the supported configuration. See the [Claude setup guide](https://support.claude.com/en/articles/11176164-use-connectors-to-extend-claude-s-capabilities).
- The user signs in through Qonvert's consent page, checks the account, workspace, project and permissions, and confirms. Start with project read access. Keep passwords, one-time codes, tokens, and OAuth secrets out of the chat and package.

## Verify with a safe first request

1. Call `get_project` and report the project name and public website, if present. If it is the wrong project, stop there. Have the user disconnect that authorization and reconnect with the intended Qonvert account and project before calling other tools.
2. For the correct project, call `list_connections` and `list_scenarios` if available. Summarize what is connected and what is ready. Connected sources may need separate consent before the assistant can read provider data.
3. If the tools are missing or authorization fails, report which step failed: host setup, Qonvert sign-in, project selection or permission. Give the next supported step. Leave approval and application of any proposed business action in Qonvert.

First prompt after connecting: “Which Qonvert project am I connected to, and which sources and scenarios can this connection see?”
