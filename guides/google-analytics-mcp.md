# Google Analytics MCP: why did traffic rise while key events fell?

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

**First prompt:** Compare sessions and key events for the last 28 complete days and the preceding 28 days. Use the example below if the property is unavailable.

**Property tool:** `read_ga4_report` uses the GA4 property you explicitly authorize. It reads sessions, key events and tracked purchase revenue for 1–31 complete days and the preceding period when the client and grant support this tool.

Compare two complete periods before deciding what to change. You can use a GA4 export for this exercise. With an authorized Analytics MCP, ask your assistant for the same metrics and period.

## Start with one property and one outcome

1. Choose a Google Analytics 4 property and the last 28 completed days. Use the preceding 28 days for comparison. Record the property and timezone.
2. Read sessions and counts of key events. Choose the event that represents the outcome you care about, such as a submitted booking request. If you only have the aggregate key event count, open GA4 to check the specific event before drawing a conclusion about bookings.
3. If the outcome dropped, break it down by channel or landing page where your report supports the breakdown. Use the same filters and event definition in each period. Check for recent tagging or form changes before attributing the drop to traffic quality.

Key event counts can include repeated events. To measure the share of sessions that produce a key event, use the GA4 session key event rate for that event. [GA4 dimensions and metrics](https://developers.google.com/analytics/devguides/reporting/data/v1/api-schema)

## Worked example

These numbers are synthetic. A hotel marks a booking-request submission as a key event.

| Period | Sessions | Booking-request events |
| --- | ---: | ---: |
| Previous 28 days | 1,000 | 40 |
| Latest 28 days | 1,240 | 31 |

Sessions increased 24% while booking-request events fell 22.5%. A good first check is to submit the booking form on mobile and verify that the event is recorded. If it is, compare booking-request events by channel and landing page, then inspect the largest drop. If you also have Google Ads spend, compare cost per booking request only where the request can be attributed to the matching campaign.

## First question for your assistant

> For this GA4 property, compare the last 28 complete days with the previous 28. Show sessions and the key event for booking requests if it is available. Give me the date ranges and one next check. Mark missing attribution, incomplete data and unavailable breakdowns.

Qonvert Connect uses the remote endpoint `https://mcp.qonvert.ai/mcp`. If your client offers the analytics reporting permission, follow [Connect Qonvert](../skills/connect-qonvert/SKILL.md), select the project and authorize the intended GA4 property. If the client cannot read the property, use a CSV export and the [Audit Campaign Tracking skill](../skills/audit-campaign-tracking/SKILL.md).

To investigate the paid side separately, use the [Google Ads audit checklist](google-ads-audit-checklist.md). To see what searchers did before reaching the site, use the [Search Console audit guide](google-search-console-mcp.md).

[Open Qonvert Connect](https://qonvert.ai/sign-in?utm_source=github&utm_medium=guide&utm_campaign=google_analytics_mcp&utm_content=first_report)
