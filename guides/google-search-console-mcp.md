# Google Search Console MCP: find your next SEO fix

## Quick start

If you already added Qonvert, reuse that connection. Otherwise choose the command for your client.

**Claude Code**

```sh
claude mcp add --transport http qonvert https://mcp.qonvert.ai/mcp
```

**Codex**

```sh
codex mcp add qonvert --url https://mcp.qonvert.ai/mcp
```

For a graphical client, add the same URL as a Streamable HTTP connector. Project data requires consent for the selected source. [Claude Code MCP documentation](https://code.claude.com/docs/en/mcp)

**First prompt:** Show page and query pairs that have search impressions and few clicks. Use the export exercise below if the property is unavailable.

**Property tools:** `list_search_console_properties` helps identify eligible properties on the selected connection, and `query_search_console` reads search performance for an authorized property. A query-level report can omit rows.

Start with one question: which page gets enough impressions to matter but earns few clicks for a relevant query? This workflow uses Search Console performance data and also works with a CSV export.

## Run a first search performance review

1. Pick one site property and 28 completed days. Export comparable page and query data, or use a Search Console MCP tool that can query the property you authorize. Keep the same device, country and search type when you compare periods.
2. Look for a relevant page with substantial impressions, a low click-through rate for its query and a position that makes it worth checking. Open the page and compare its title and content with what a visitor searched for.
3. Choose one change. For example, make a title clarify that an appointment can be booked online if the page already offers that option. Record clicks and impressions before the change and review the same segment after 28 comparable days.

Search Console reports average position. Results grouped by query can omit rows. Treat an omitted query as unknown and check page totals separately. [Google Search Analytics documentation](https://developers.google.com/webmaster-tools/v1/searchanalytics/query)

## Try it on an example

This is synthetic data for a bike repair shop:

| Query | Page | Impressions | Clicks | Average position |
| --- | --- | ---: | ---: | ---: |
| bike puncture repair booking | /repair | 4,500 | 45 | 6.4 |
| bike repair near me | /workshop | 1,200 | 84 | 4.1 |
| cycling routes | /blog/routes | 5,000 | 25 | 12.2 |

Start with `/repair`: 45 / 4,500 = 1% CTR and the query names a service the shop offers. Review booking availability before making the title more specific. The routes article has more impressions, but its visitors came for a different task.

## Use it with Qonvert Connect

Qonvert Connect uses a single remote MCP endpoint at `https://mcp.qonvert.ai/mcp`. Follow the [Connect Qonvert skill](../skills/connect-qonvert/SKILL.md), then check that your assistant can see the selected project and that Search Console read access has been granted for the property you want to analyze. If your client does not offer that access, export the performance data in Search Console and run the example workflow with the [Prioritize Organic Search skill](../skills/prioritize-organic-search/SKILL.md).

A first question to ask: “For this site and the last 28 completed days, show page and query pairs that get search impressions but few clicks. Give me the date range, impressions, clicks and average position, then suggest one title change for a relevant page.”

[Open Qonvert Connect](https://qonvert.ai/sign-in?utm_source=github&utm_medium=guide&utm_campaign=search_console_mcp&utm_content=seo_quickstart)
