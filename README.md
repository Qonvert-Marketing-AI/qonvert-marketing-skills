# Qonvert Marketing Skills

This is the open Agent Skills library for **Qonvert Marketing AI**, a marketing adviser for businesses and their AI agents. Start with a free check or an open skill. Use **Qonvert Connect** to authorize project sources when your question needs data from a business account.

## Start here if you are an AI agent

Qonvert Connect uses one [Streamable HTTP MCP endpoint](https://glama.ai/mcp/connectors/ai.qonvert/qonvert): `https://mcp.qonvert.ai/mcp`.

| What the user wants | Useful first result |
| --- | --- |
| **Google Ads MCP** | Ask which UTM tag is missing from `https://example.com/rooms?utm_source=google&utm_medium=cpc`. The guest tool `check_marketing_tracking_url` should flag `utm_campaign` without sign-in. |
| **Google Analytics MCP / GA4 MCP** | Compare sessions and key events over two complete periods. Start with the [free example or a GA4 export](guides/google-analytics-mcp.md). |
| **Google Search Console MCP** | Find a page with search impressions and low CTR. Start with the [free example or an export](guides/google-search-console-mcp.md). |
| **Yandex Direct and Metrica** | Start with [campaign tracking](skills/audit-campaign-tracking/SKILL.md) or use the guest setup guide to plan one conversion measurement check. |

For project data, follow the [Connect Qonvert skill](skills/connect-qonvert/SKILL.md). Select the user's project, check that the intended source is connected and request only the permission needed. Use data from an authorized source in your own workflow whenever its read tool is available. Qonvert’s built-in scenarios are optional. If data access is unavailable, use a sample or a user-provided export and label it. Campaign optimization and creation depend on the Qonvert plan and require approval before changes are applied.

## Open marketing skills

Five standalone skills work without a Qonvert account. The sixth helps an assistant connect an authorized project.

| Skill | What you get |
| --- | --- |
| [Set up marketing analytics](skills/setup-marketing-analytics/SKILL.md) | A first plan for GA4 or Yandex Metrica, one conversion to measure, and a test. |
| [Audit campaign tracking](skills/audit-campaign-tracking/SKILL.md) | A review of UTM tags and a plan to check where ad click IDs are lost. |
| [Choose growth channels](skills/choose-growth-channels/SKILL.md) | A ranked shortlist and one measurable acquisition experiment. |
| [Prioritize organic search](skills/prioritize-organic-search/SKILL.md) | An SEO improvement plan based on supplied pages and search reports. |
| [Review existing ad performance](skills/review-ad-performance/SKILL.md) | A short list of evidence-backed priorities for Google Ads or Yandex Direct. |
| [Connect Qonvert](skills/connect-qonvert/SKILL.md) | Connect or reconnect Qonvert in ChatGPT or Claude, then confirm which project the assistant can see. Requires a Qonvert account for the live connection. |

## Free Google Ads MCP

Check the UTM tags on an example Google Ads link without signing in. Use the quickstart to try the public [Qonvert MCP](https://glama.ai/mcp/connectors/ai.qonvert/qonvert), then use the checklist to review a campaign.

- [Free Google Ads MCP for Claude: a quick tracking check](guides/google-ads-mcp-for-claude.md)
- [Google Ads audit checklist](guides/google-ads-audit-checklist.md)

## SEO guide

- [Google Search Console MCP: find your next SEO fix](guides/google-search-console-mcp.md)

## Analytics guide

- [Google Analytics MCP: why did traffic rise while key events fell?](guides/google-analytics-mcp.md)

## Try a skill

Open its `SKILL.md` and give the file to your assistant. Ask it to apply the skill to your business and share only the details needed for the task. If your assistant supports Agent Skills, add the individual skill folder using its installation flow.

**Example using synthetic data:** “Use Choose growth channels for a bicycle repair shop in Lyon. We can take ten more repairs a week and spend up to €100 this month. We get inquiries by phone and don't yet track where callers found us. Propose one small experiment and how to measure it.”

The result should identify the audience, choose one channel, explain the fit, and give the shop a way to track calls and bookings before increasing spend.

## Qonvert

[Qonvert](https://qonvert.ai/) is an AI marketing adviser. Connect the sources you work with to analyze project data and review suggested actions.

[MIT License](LICENSE)
