---
name: setup-marketing-analytics
description: Plan the first analytics and search setup for a business website. Use when a user needs to choose GA4 or Yandex Metrica, define a conversion, or verify that their first event is recorded.
---

# Set up marketing analytics

Turn the business goal into a checklist the site owner can test today. Establish the target market, website or checkout flow, and the single most important outcome: an accepted lead, a completed signup, or a confirmed order. Ask only for facts that change the next step.

1. Inventory existing tags, properties and access from the facts the user supplies. With Qonvert connected, use the project's `recommended_stack` from `qonvert_connect`. Recommend Yandex Metrica and Yandex Webmaster for Russia, or GA4 and Google Search Console for other markets. Suggest one default stack. Honor a provider the user explicitly requests and use relevant access already in place. Match the proposed property, counter or host to the confirmed website.
2. Define one primary event in terms of the exact success condition. Record the event name, page or trigger, and how to avoid duplicate events on reload or checkout retry. When a purchase event includes value, specify the amount definition and currency. Keep identifiers and personal details out of analytics parameters.
3. Describe one end-to-end test. Give the user a test action, the provider's verification view and the observation that counts as success. For GA4, use DebugView. For Metrica, use the tag and goal checkers. Label setup as verified only when there is an observed event.
4. Suggest the next search setup step, such as property ownership, sitemap submission or inspecting a key URL. End with a list of three priorities, any material unknowns, and an owner for the first action.

Use current official setup instructions when giving platform-specific steps. See [GA4 DebugView](https://support.google.com/analytics/answer/7201382), [Metrica tag checks](https://yandex.com/support/metrica/en/general/check-counter), and [Metrica goal checks](https://www.yandex.com/support/metrica/en/general/check-goal). Obtain approval before making changes to a live site or account.
