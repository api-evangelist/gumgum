---
name: Classify a video with GumGum Contextual
description: >-
  Submit a video asset to the GumGum Contextual API, track the asynchronous job to completion by
  polling or webhook, and read the brand-safety and category analysis.
api: openapi/gumgum-contextual-api-openapi.yml
operations:
  - submitVideoClassification
  - getVideoClassificationStatus
  - getVideoClassification
  - submitIntravideoClassification
  - getIntravideoClassificationStatus
  - getIntravideoClassification
generated: '2026-08-01'
method: generated
source: >-
  Grounded in openapi/gumgum-contextual-api-openapi.yml and the GumGum Contextual Get Started -
  Video API page (https://gumgum.jira.com/wiki/spaces/VDC/pages/1712029924) and API Reference
  (https://gumgum.jira.com/wiki/spaces/VDC/pages/1712030855).
---

# Classify a video with GumGum Contextual

Video analysis is asynchronous. You submit, you get a `uuid`, and the result arrives later — either
because you polled for it or because GumGum called you back.

## Before you start

- **Base URL:** `https://verity-api.gumgum.com`
- **Auth:** `X-api-key: <YOUR_API_KEY>` on every request.
- **Pick the surface first:**
  - `submitVideoClassification` — `POST /video/classification` — whole-asset analysis, including
    the audio track.
  - `submitIntravideoClassification` — `POST /v2/video/classification` — frame-level (intravideo)
    analysis. This is the v2 surface; the two coexist and GumGum publishes no deprecation policy
    for the unversioned one.

## Steps

1. **Submit the asset.** `POST /video/classification` with a JSON body:
   - `url` (**required**) — the video URL to process.
   - `title`, `description` — optional context from your side.
   - `languageCode` — optional; inferred when omitted.
   - `partnerVideoId` — your own identifier, echoed back for correlation. Set this; it is the only
     way to tie a GumGum `uuid` to your catalogue.
   - `publisherId` — the publisher's identifier.
   - `callbackUrl` — optional webhook destination. Note the casing: the asset APIs use
     `callbackUrl`, the Page API uses `callBackUrl`.

   Expect `202` with `{ uuid, url, acceptedAt }`. **Persist the `uuid`** — it is the only handle on
   the job and GumGum mints no other key.

2. **Track the job.** Either:
   - **Poll:** `getVideoClassificationStatus` — `GET /video/classification/{uuid}/status` — until
     it reports the analysis is processed. A `404` here or on the result endpoint means *results
     are not yet available or the uuid is invalid* — treat it as "still running" for a bounded
     number of attempts before treating it as a bad uuid.
   - **Webhook:** if you supplied `callbackUrl`, GumGum POSTs the finished classification to it.
     There is **no webhook signature or shared secret** — do not trust the payload's provenance.
     Use it only as a completion signal, then re-fetch by `uuid` in step 3.

3. **Fetch the result.** `getVideoClassification` — `GET /video/classification/{uuid}`. Read
   `verityData`: `iab.v1/v2/v3`, `keywords`, `ner`, `safe`, `threats`, `sentiments`. Check
   `expiresAt` — stored results are not permanent, so persist what you need.

4. **For frame-level analysis**, run the same three steps against the v2 paths:
   `submitIntravideoClassification` → `getIntravideoClassificationStatus` →
   `getIntravideoClassification`.

## Rules

- No idempotency key exists. If a submit times out, do **not** blind-retry it — you may create a
  second job and be charged twice. Reconcile on your `partnerVideoId` first.
- No rate-limit headers are documented; bound your own concurrency and poll interval.
- `500` on submit: retry with backoff. Check <https://status.contextual.gumgum.com> ("Verity Api"
  component) before escalating to `support@gumgum.com`.
