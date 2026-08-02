---
name: Classify a web page with GumGum Contextual
description: >-
  Get IAB category, keyword, brand-safety and sentiment analysis for a web page URL from the
  GumGum Contextual API, handling the cached-vs-initiated response correctly.
api: openapi/gumgum-contextual-api-openapi.yml
operations:
  - classifyPage
generated: '2026-08-01'
method: generated
source: >-
  Grounded in openapi/gumgum-contextual-api-openapi.yml and the GumGum Contextual Get Started -
  Page API page (https://gumgum.jira.com/wiki/spaces/VDC/pages/1712095256).
---

# Classify a web page with GumGum Contextual

Use this when you need to know what a web page is *about* and whether it is brand-safe, before
placing an ad against it or ingesting it.

## Before you start

- **Base URL:** `https://verity-api.gumgum.com`
- **Auth:** every request carries the header `X-api-key: <YOUR_API_KEY>`. Keys are issued by GumGum
  during partner onboarding — there is no self-serve signup, no OAuth, and no scopes.
- **There is no sandbox.** Any call you make is against production and against your contracted
  volume.

## Steps

1. **Call `classifyPage`** — `GET /page/classify?pageUrl=<url-encoded page URL>`.
   URL-encode `pageUrl`. Optionally add:
   - `callBackUrl=<https endpoint>` to have the finished analysis POSTed to you instead of polling.
   - `ignoreCache=true` to force reprocessing instead of returning the stored result.

2. **Read the body, not just the HTTP status.** A `200` does **not** mean the analysis is done.
   Check two fields:
   - `status` — `INITIATED` means analysis is still running; `PROCESSED` means it is complete.
   - `dataAvailable` — `true` when `verityData` is populated.
   Keep the returned `uuid`; it identifies this classification.

3. **If `status` is `INITIATED`, poll.** Re-issue the same `classifyPage` request (without
   `ignoreCache`) on a backoff until `status` is `PROCESSED`. Do not spin: GumGum documents no
   rate-limit headers, so an aggressive poll loop is your problem to bound, not theirs. If you
   supplied `callBackUrl`, skip this step and wait for the webhook.

4. **Consume `verityData`:**
   - `iab.v1` / `iab.v2` / `iab.v3` — IAB Content Taxonomy categories with scores. Pick the
     taxonomy version your demand side actually speaks; they are not interchangeable.
   - `keywords` — keywords extracted from the page.
   - `ner` — named entities.
   - `safe` — the brand-safety boolean.
   - `threats` — detected brand-safety threats with confidence levels.
   - `sentiments` — emotional tone.
   Also read `languageCode` (detected), `processedAt` and `expiresAt` — results expire.

## Error and retry rules

- `403 {"message":"Forbidden"}` — your `X-api-key` header is missing or invalid.
- `403 {"message":"Missing Authentication Token"}` — the **path or method did not match a route**.
  Despite the wording this is a routing error, not an auth error. Re-check the path.
- `500` — retry with backoff; if it persists, check <https://status.contextual.gumgum.com> before
  escalating to `support@gumgum.com`.
- **There is no idempotency key.** Re-submitting is safe only because GumGum returns the cached
  result for an already-analyzed URL — which is exactly what `ignoreCache=true` defeats. Never set
  `ignoreCache` inside a retry loop.
