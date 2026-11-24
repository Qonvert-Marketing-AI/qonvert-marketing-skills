---
name: connect-qonvert
description: Connect or reconnect Qonvert via MCP, then continue the user's Google Ads or Yandex Direct campaign creation or optimization request. Use for first sign-in, expired access, wrong projects, and handoff to the exact advertising scenario.
license: MIT
---

# Connect Qonvert

Use the official Streamable HTTP MCP endpoint `https://mcp.qonvert.ai/mcp` with OAuth.

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

Call `get_project` after consent and check that it matches the user's request. If it differs, ask the user to reconnect to the intended project before reading data or preparing work. For the correct project, use `qonvert_connect` when available, or `list_connections` and `list_scenarios`, to find the intended source and its status. Ask the user to choose an account only when several are plausible. For a missing connection, open the requested scenario's setup and let the owner authorize the advertising provider. Prefer the project-specific link returned by Qonvert.

- **Optimize Google Ads or Yandex Direct.** Use `get_setup_requirements` with `google_ads_optimization` or `yandex_ads_optimization`. If optimization is active for the intended source, open the project's tasks with `open_in_qonvert` and continue reviewing the available recommendations. Otherwise, if Qonvert reports preparation is available, call `prepare_scenario_activation` with the scenario, selected `source_id` and a stable UUID `request_id`. Open its `approval_url` for the user. Check progress with `get_prepared_scenario`.
- **Create Google Ads.** Use `adsy_campaign_request` if available. Pass the exact HTTPS landing page supplied by the user, or omit it to use the saved project site. Reuse the same `request_id` throughout and supply only confirmed brief details. Follow the tool's returned link and next step.
- **Create Yandex Direct ads.** Call `get_campaign_requirements` for `yandex_direct`. If there is no active creation instance for the intended account, open its `scenario_url` to finish setup. When the required facts, budget and intended instance are confirmed, call `prepare_campaign_brief` for `yandex_direct`. Follow the live tool schema. For Google Ads hosts without `adsy_campaign_request`, use these same two tools with `google_ads` and its own brief schema.
- **Review the result.** Open the returned review link in Qonvert. Poll `get_campaign_brief_status` with the returned `brief_id` when the user asks for progress and open the task link when it is ready. Confirmations for enabling a scenario, applying a recommendation, creating a paused campaign and launching ads happen in Qonvert. Launching and spending require separate user approval.
