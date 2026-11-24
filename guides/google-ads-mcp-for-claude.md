# Free Google Ads MCP for Claude: a quick tracking check

Use Qonvert’s public Google Ads MCP to check the UTM tags on a campaign link for free, without creating a Qonvert account. The example below uses a fictional hotel.

1. In Claude, open **Customize → Connectors**. Add Qonvert as a custom remote connector at `https://mcp.qonvert.ai/mcp` if your workspace permits it. Follow any prompts shown by the client. [Claude’s remote connector guide](https://support.claude.com/en/articles/11175166-get-started-with-custom-connectors-using-remote-mcp)
2. Ask: “Which campaign tag is missing from `https://example.com/rooms?utm_source=google&utm_medium=cpc`?” This prompt also works in another MCP client that can access the public endpoint. [Qonvert MCP in Glama](https://glama.ai/mcp/connectors/ai.qonvert/qonvert)
3. Expected result: the endpoint found `utm_source` and `utm_medium` and flagged missing `utm_campaign`. Add a campaign label, then test a real visit separately to check redirects and conversion recording.

Once you want to use project data, [open the Google Ads workflow in Qonvert](https://qonvert.ai/services/google-ads?utm_source=github&utm_medium=guide&utm_campaign=google_ads_mcp&utm_content=claude_quickstart) and connect the account you intend to review. See [Connect Qonvert](../skills/connect-qonvert/SKILL.md) for consent and project selection. The sample URL result was verified against the public MCP endpoint.

**Pricing.** The public URL check is free. Qonvert offers a standard three-day product trial without a card. Campaign creation requires an eligible paid plan. See [Qonvert pricing](https://qonvert.ai/pricing?utm_source=github&utm_medium=guide&utm_campaign=google_ads_mcp&utm_content=claude_pricing) for current trial and plan details.

For a repeatable review, use the [Google Ads audit checklist](google-ads-audit-checklist.md).
