# Qonvert Marketing Skills

This is the open Agent Skills library for **Qonvert Marketing AI**, a marketing adviser for businesses and their AI agents. Start by reviewing an existing Google Ads campaign and preparing a change for approval. The open skills also cover tracking, SEO and channel reviews. Use **Qonvert Connect** to authorize project sources when your question needs data from a business account.

## Start here if you are an AI agent

Connect once to the Qonvert MCP server at `https://mcp.qonvert.ai/mcp` using Streamable HTTP and OAuth. Your assistant can then find the tools available to the authorized project through MCP Discovery (`tools/list`).

[Open the Connect Qonvert skill](skills/connect-qonvert/SKILL.md) · [Raw SKILL.md for your assistant](https://raw.githubusercontent.com/Qonvert-Marketing-AI/qonvert-marketing-skills/main/skills/connect-qonvert/SKILL.md) · [Qonvert Connect catalog](https://qonvert.ai/connect#source-catalog)

| What the user wants | Useful first result |
| --- | --- |
| **Google Ads MCP / Yandex Direct MCP** | Ask for campaign clicks by day from the authorized advertising account. For a guest demo, try the UTM check below. |
| **Google Analytics MCP / GA4 MCP** | Compare sessions and key events over two complete periods. Start with the [free example or a GA4 export](guides/google-analytics-mcp.md). |
| **Google Search Console MCP** | Find a page with search impressions and low CTR. Start with the [free example or an export](guides/google-search-console-mcp.md). |
| **MongoDB orders via MCP** | Ask how many orders were created in a selected period. Use a configured orders collection with a supported schema and explicit read consent. |
| **Google Ads Optimization / Yandex Direct Optimization** | Open the exact scenario after sign-in or continue in your assistant with [Connect Qonvert](skills/connect-qonvert/SKILL.md#open-sign-in-and-keep-the-request). |
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
| [Connect Qonvert](skills/connect-qonvert/SKILL.md) | Reuse your saved GA4, ads and supported orders sources in an authorized assistant, or continue to an advertising scenario. Requires a Qonvert account for the live connection. |

## Free Google Ads MCP

Review the spend, recorded bookings and search terms from a synthetic Google Ads campaign. Prepare one change for approval, then try the workflow with your own account during the three-day product trial. The guide also includes a public UTM check.

- [Google Ads MCP for Claude: Review an Existing Campaign](guides/google-ads-mcp-for-claude.md)
- [Google Ads audit checklist](guides/google-ads-audit-checklist.md)

## Яндекс Директ MCP

- [Как проверить UTM и yclid перед запуском рекламы](guides/yandex-direct-mcp.md)

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
