# Google Ads MCP for Claude: a quick tracking check

Start here if you want to check one Google Ads campaign link before you connect a live account. This example uses a fictional hotel and the public Qonvert MCP tool.

1. In Claude, open **Customize → Connectors**. Add Qonvert as a custom remote connector at `https://mcp.qonvert.ai/mcp` if your workspace permits it. Follow any prompts shown by the client. [Claude’s remote connector guide](https://support.claude.com/en/articles/11175166-get-started-with-custom-connectors-using-remote-mcp)
2. Ask: “Which campaign tag is missing from `https://example.com/rooms?utm_source=google&utm_medium=cpc`?” This prompt also works in another MCP client that can access the public endpoint. [Qonvert MCP in Glama](https://glama.ai/mcp/connectors/ai.qonvert/qonvert)
3. Expected result: the endpoint found `utm_source` and `utm_medium` and flagged missing `utm_campaign`. Add a campaign label, then test a real visit separately to check redirects and conversion recording.

Once you want to use project data, [open the Google Ads workflow in Qonvert](https://qonvert.ai/services/google-ads?utm_source=github&utm_medium=guide&utm_campaign=google_ads_mcp&utm_content=claude_quickstart) and connect the account you intend to review. See [Connect Qonvert](../skills/connect-qonvert/SKILL.md) for consent and project selection. The sample URL result was verified against the public MCP endpoint.

For a repeatable review, use the [Google Ads audit checklist](google-ads-audit-checklist.md).
