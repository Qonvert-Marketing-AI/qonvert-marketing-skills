# Google Ads audit checklist

Run this checklist against one Search campaign. Pick one improvement you can explain and measure.

- [ ] **Outcome.** Write down the business outcome and the exact conversion action that represents it.
- [ ] **Tracking.** Check URL tags and final destination. Verify a real test action in the system that records the outcome. [Google’s UTM guide](https://support.google.com/analytics/answer/10917952?hl=en)
- [ ] **Search terms.** Review actual queries, cost and recorded conversions. Check whether recent conversions have had time to appear. [Google Ads search terms](https://support.google.com/google-ads/answer/2472708?hl=en) · [Conversion lag](https://support.google.com/google-ads/answer/9347065?hl=en)
- [ ] **Spend.** Compare campaign or ad-group spend over the same period and with the same conversion definition.
- [ ] **Landing page.** Open the page on mobile and try the action promised in the ad. Use a measured speed result if performance looks like a problem. [PageSpeed Insights](https://developers.google.com/speed/docs/insights/v5/about)
- [ ] **Delivery.** Check bidding strategy, budget, locations, schedule and recent changes.
- [ ] **Next test.** Record the evidence, the proposed change, what you’ll measure and when you’ll review it.

## Try the tracking check

Add [Qonvert Connect](https://qonvert.ai/connect/google-ads?utm_source=github&utm_medium=guide&utm_campaign=google_ads_mcp&utm_content=audit_checklist_tracking) in your MCP client. Ask it to check the tags on the sample below. An agent can call `check_marketing_tracking_url` with the supplied `url` and `language` set to `en`. This check runs without a Qonvert account.

| Fictional hotel URL | Result from the public check |
| --- | --- |
| `https://example.com/rooms?utm_source=google&utm_medium=cpc` | Reports missing `utm_campaign`. |
| `https://example.com/rooms?utm_source=google&utm_medium=cpc&utm_campaign=hotel_bookings` | All three core UTM fields are present. |

The tool inspects the supplied URL. To verify that tags survive redirects, open an approved test link and inspect the final address. To verify conversion recording, complete the intended test action and find it in the system that records it. The sample has no click ID. Google Ads can add one at click time when auto-tagging is enabled. [Google Ads auto-tagging](https://support.google.com/google-ads/answer/3095550?hl=en)

Start with the [Google Ads MCP quickstart for Claude](google-ads-mcp-for-claude.md) to check one sample link. Use [Qonvert’s Google Ads workflow](https://qonvert.ai/services/google-ads?utm_source=github&utm_medium=guide&utm_campaign=google_ads_mcp&utm_content=audit_checklist) when you’re ready to review a connected campaign.
