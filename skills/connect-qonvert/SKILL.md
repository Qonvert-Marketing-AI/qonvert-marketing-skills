---
name: connect-qonvert
description: Connect or reconnect Qonvert via MCP to reuse saved sources in your assistant. Use for questions about GA4 sessions, ad clicks, or aggregate MongoDB orders, and for Google Ads or Yandex Direct campaign setup and optimization.
license: MIT
---

# Connect Qonvert

Use the official Streamable HTTP MCP endpoint `https://mcp.qonvert.ai/mcp` with OAuth. This is the shared connection for all [Qonvert Connect integrations and scenarios](https://qonvert.ai/connect#source-catalog).

## Discover the right tool

After OAuth, use the client's tool discovery (`tools/list`). Match the requested integration or scenario to the tool's title and call the identifier in `name` with arguments from its `inputSchema`. For example, look for **Google Ads MCP**, **Yandex Direct MCP**, **Google Search Console MCP**, **Google Ads Optimization** or **Yandex Direct Optimization**. These entry tools check the target project's readiness and point to the next operation. Continue with the tool or action returned by Qonvert.

When a named entry is missing, call `qonvert_connect` with the intended `source` or use `get_setup_requirements` for the requested optimization scenario. Refresh discovery after consent changes. Use the MCP client's authorization flow for any additional permission it supports. If the client cannot grant it, give the project-specific Qonvert link or continue in a compatible client. Never infer access from a tool's title.

## Choose sources for the project's market

After OAuth, call `qonvert_connect` without a source to read `source_market`, `recommended_stack`, and the next setup step. For a Russian project, recommend Yandex Direct, Yandex Metrica and Yandex Webmaster. For other markets, recommend Google Ads, GA4 and Google Search Console. Offer the appropriate missing source from that stack. Honor a provider explicitly requested by the user and use relevant sources already connected. The language of the chat does not change the project market.

Before authorization, use the target market the user states. A Russian domain is a useful signal. Ask one short question if the market is unclear and choosing it is necessary for the next step. Once the website is confirmed in Qonvert, use its domain for Analytics, Metrica, Search Console and Webmaster setup. Open the project-specific link and let the owner confirm the matching property, counter or host.

## Open sign-in and keep the request

1. Keep the requested provider and action (create or optimize), project, and any landing page the user supplied. Ask one short question only when the request leaves a choice that affects what you open.
2. When Qonvert tools are present, call `get_project` to check access. If the host already shows Qonvert as signed out and exposes the guest `adsy_campaign_request` for a Google Ads creation request, call that tool first with only a fresh `request_id`. This can request campaign preparation access at the first sign-in. Keep that ID for continuation. When either call requests authorization, open or present the host's **Connect** or **Reconnect** action immediately.
3. If the connector is absent, use the host's custom MCP setup with the endpoint above. Use the host's registered OAuth client or its client metadata when supported. The user signs in and approves the requested access in the browser. Keep credentials, one-time codes and tokens out of the conversation. Use the host-generated OAuth prompt, which includes the callback and PKCE parameters. [ChatGPT setup](https://developers.openai.com/api/docs/guides/custom-mcp-server) · [Claude setup](https://support.claude.com/en/articles/11176164-use-connectors-to-extend-claude-s-capabilities)
4. If the host cannot start MCP authorization, open the matching Qonvert link as soon as the provider and action are known. Offer it as a clickable link when you cannot open a browser. The link opens the scenario after Qonvert sign-in. For work back in the assistant, continue MCP authorization through the host when available.

| Requested work | Sign in and open the scenario |
| --- | --- |
| Create Google Ads | [Open Google Ads creation](https://qonvert.ai/sign-in?redirect=%2Fdashboard%2Fscenarios%3Fscenario%3Dgoogle_ads_creation) |
| Optimize Google Ads | [Open Google Ads optimization](https://qonvert.ai/sign-in?redirect=%2Fdashboard%2Fscenarios%3Fscenario%3Dgoogle_ads_optimization) |
| Create Yandex Direct ads | [Open Yandex Direct creation](https://qonvert.ai/sign-in?redirect=%2Fdashboard%2Fscenarios%3Fscenario%3Dyandex_ads_creation) |
| Optimize Yandex Direct | [Open Yandex Direct optimization](https://qonvert.ai/sign-in?redirect=%2Fdashboard%2Fscenarios%3Fscenario%3Dyandex_ads_optimization) |

## Continue in the authorized project

Call `get_project` after consent and check that it matches the user's request. If it differs, ask the user to reconnect to the intended project before reading data or preparing work. For the correct project, use `qonvert_connect` when available, or `list_connections` and `list_scenarios`, to find the intended source and its status. Ask the user to choose an account only when several are plausible. For a missing connection, open the requested scenario's setup and let the owner authorize the advertising provider. Prefer the project-specific link returned by Qonvert. If the tool only returns the generic scenarios link, call `open_in_qonvert` with `destination: scenarios` and add the selected `scenario` query parameter, preserving its project and workspace parameters.

## Ask about connected data

Qonvert Connect is a set of MCP tools for analytics, ads and orders, available at one endpoint. Save a provider connection once in Qonvert, then issue separate project and source permissions to a compatible assistant. The assistant can answer from supported reports in the chat you already use. You can authorize a new assistant or revoke an old one while keeping the source connected.

| Example question | What to call |
| --- | --- |
| How many sessions did we get in the last seven complete days? Compare with the previous week. | `read_ga4_report` on the authorized Google Analytics 4 property. |
| How many Google Ads clicks did we get in the last seven complete days? Break them down by day. | `read_ads_daily` on the authorized Google Ads account. |
| How many orders were created in the last seven complete days? | `read_orders_aggregate` on the authorized MongoDB orders collection with a supported schema. |

Call `get_qonvert_connect_guide` when available for examples, documentation and setup links without signing in. After OAuth, check the selected source and its permission in `qonvert_connect` or `list_connections` before using a report tool. If the source is saved but the grant lacks read access, request the tool's specific scope through the MCP client's consent flow. If there is no source, use the project setup link from Qonvert. Ask for a date range only when needed, follow the tool's date conventions, and name the source and period in the answer. Treat missing permissions, an incomplete report, and a measured zero as different outcomes. The orders tool returns aggregates, with no arbitrary database queries or individual customer records.

## Continue advertising work

Once the project and source are clear, read the permitted data and continue preparing the requested work in the same session. Share the result or the action Qonvert needs from the user. Existing Qonvert scenarios can deliver notifications through the user's connected channel.

- **Optimize Google Ads or Yandex Direct.** Use `get_setup_requirements` with `google_ads_optimization` or `yandex_ads_optimization`. If optimization is active for the intended source, open the project's tasks with `open_in_qonvert` and continue reviewing the available recommendations. Otherwise, with a confirmed source, call `prepare_scenario_activation` if preparation is available or its reason is `missing_delegated_scope`. Pass the scenario, selected `source_id` and a stable UUID `request_id`. If the host asks for `qonvert.prepare`, open that consent and resume with the same request ID after checking the project. Open the returned `approval_url` and check progress with `get_prepared_scenario`. If Qonvert reports another blocker, open the scenario in the authorized project so the user can complete the indicated step.
- **Create Google Ads.** Use `adsy_campaign_request` if available. Pass the exact HTTPS landing page supplied by the user, or omit it to use the saved project site. Reuse the same `request_id` throughout and supply only confirmed brief details. Follow the tool's returned link and next step.
- **Create Yandex Direct ads.** Call `get_campaign_requirements` for `yandex_direct`. If there is no active creation instance for the intended account, open its `scenario_url` to finish setup. When the required facts, budget and intended instance are confirmed, call `prepare_campaign_brief` for `yandex_direct`. Follow the live tool schema. For Google Ads hosts without `adsy_campaign_request`, use these same two tools with `google_ads` and its own brief schema.
- **Review the result.** Open the returned review link in Qonvert. Poll `get_campaign_brief_status` with the returned `brief_id` when the user asks for progress and open the task link when it is ready. Confirmations for enabling a scenario, applying a recommendation, creating a paused campaign and launching ads happen in Qonvert. Launching and spending require separate user approval.
