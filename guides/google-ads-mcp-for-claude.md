# Google Ads MCP for Claude: Review an Existing Campaign

Use **Qonvert Marketing AI** to review one Google Ads campaign you already run. Compare spend, recorded conversions, and actual search terms. Start with one proposed change you can explain and approve.

[Start your 3-day free trial without a card](https://qonvert.ai/services/google-ads?utm_source=github&utm_medium=guide&utm_campaign=google_ads_mcp&utm_content=claude_quickstart)

## Try the review with a sample report

The table is synthetic. It represents 30 complete reporting days for a fictional hotel, after its booking action had time to report.

| Campaign | Ad group | Search term | Clicks | Spend | Recorded bookings |
| --- | --- | --- | ---: | ---: | ---: |
| Direct Bookings | City Rooms | hotel front desk jobs | 28 | $84 | 0 |

Give Claude the table or a sanitized export and ask:

> Review these Google Ads search terms using recorded bookings as the outcome. Show one proposed change with the exact campaign, ad group, search term, and evidence. Tell me what to verify before I approve it.

A candidate is to add the exact-match negative keyword `[hotel front desk jobs]` to **Direct Bookings → City Rooms**. The query suggests job-seeking intent and accounts for $84 in spend with zero recorded bookings in the sample. Check existing exclusions, conversion lag, and related booking terms before approving. The [open ad review skill](../skills/review-ad-performance/SKILL.md) describes how to handle missing evidence.

If you approve a supported change in Qonvert, confirm it in the intended ad group after application. Compare job-seeker spend and recorded bookings across comparable reporting periods with the same conversion definition. [Google Ads search terms](https://support.google.com/google-ads/answer/2472708?hl=en) · [Conversion lag](https://support.google.com/google-ads/answer/9347065?hl=en) · [Negative keywords](https://support.google.com/google-ads/answer/2453972?hl=en)

## Connect your own account

Qonvert Connect uses one Streamable HTTP MCP endpoint, `https://mcp.qonvert.ai/mcp`. In Claude, use **Customize → Connectors → Add custom connector** if your plan and workspace allow it. For Claude Code, run the command below. Reuse an existing Qonvert connection when available. [Claude connectors](https://support.claude.com/en/articles/11175166-get-started-with-custom-connectors-using-remote-mcp) · [Claude Code MCP](https://code.claude.com/docs/en/mcp)

```sh
claude mcp add --transport http qonvert https://mcp.qonvert.ai/mcp
```

For Codex, use the same endpoint.

```sh
codex mcp add qonvert --url https://mcp.qonvert.ai/mcp
```

1. Follow the client's OAuth prompt, choose the intended Qonvert project, and connect or select your Google Ads account. Grant access only to that source.
2. Check the project with `get_project` and discover tools available in your client. Use the Google Ads Optimization entry to check readiness. Report and preparation access depends on your client, project permissions, plan, and the account connection.
3. When the workflow is available, ask for the same campaign review using your account. Open a returned recommendation or setup link in Qonvert and review the evidence before approving any change.

[Google Ads Optimization setup](https://qonvert.ai/connect/google-ads-optimization) · [Google Ads MCP tools and permissions](https://qonvert.ai/connect/google-ads?utm_source=github&utm_medium=guide&utm_campaign=google_ads_mcp&utm_content=claude_source_docs) · [Connect Qonvert skill](../skills/connect-qonvert/SKILL.md)

## Check tracking on a campaign link

As a separate free check, ask which core UTM tag is missing from `https://example.com/rooms?utm_source=google&utm_medium=cpc`. The public `check_marketing_tracking_url` tool identifies `utm_campaign` from the supplied URL without an account. Test an approved visit separately to check redirects and event recording. [Google Ads audit checklist](google-ads-audit-checklist.md) · [Qonvert MCP in Glama](https://glama.ai/mcp/connectors/ai.qonvert/qonvert)
