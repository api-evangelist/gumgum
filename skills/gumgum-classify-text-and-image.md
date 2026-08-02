---
name: Classify text and images with GumGum Contextual
description: >-
  Submit a raw text block or a single image to the GumGum Contextual API and retrieve brand-safety,
  keyword and category analysis using the shared submit / status / result pattern.
api: openapi/gumgum-contextual-api-openapi.yml
operations:
  - submitTextClassification
  - getTextClassificationStatus
  - getTextClassification
  - submitImageClassification
  - getImageClassificationStatus
  - getImageClassification
generated: '2026-08-01'
method: generated
source: >-
  Grounded in openapi/gumgum-contextual-api-openapi.yml, the GumGum Contextual Image API Reference
  (https://gumgum.jira.com/wiki/spaces/VDC/pages/1780187188) and Text API Reference
  (https://gumgum.jira.com/wiki/spaces/VDC/pages/1780187198).
---

# Classify text and images with GumGum Contextual

The Image and Text surfaces use the same three-call shape as Video, with one important difference:
**neither reference page documents a callback parameter**, so plan on polling.

## Before you start

- **Base URL:** `https://verity-api.gumgum.com`
- **Auth:** `X-api-key: <YOUR_API_KEY>`.
- Image analysis is per-image; text analysis is per-block. Neither endpoint batches.

## Image

1. `submitImageClassification` — `POST /image/classification`. The reference documents that you
   specify the **URL of the image to be analyzed** (`url`). Expect `202` with a `uuid`.
2. `getImageClassificationStatus` — `GET /image/classification/{uuid}/status` — poll until
   processed. `404` means results are not yet available, or the uuid is wrong.
3. `getImageClassification` — `GET /image/classification/{uuid}` — returns brand-safety, keyword
   and threat categorization data in `verityData`.

Check GumGum's supported image formats list on the Image API Reference before submitting; the
reference enumerates supported formats and unsupported ones will fail at analysis, not at submit.

## Text

1. `submitTextClassification` — `POST /text/classification`. **Confirm the exact request field
   names against the live Text API Reference** — GumGum's published page describes the endpoint but
   does not enumerate the body fields, so the captured spec deliberately leaves the body schema
   open rather than guessing. Do not copy the video body shape and assume it applies.
2. `getTextClassificationStatus` — `GET /text/classification/{uuid}/status`.
3. `getTextClassification` — `GET /text/classification/{uuid}` — returns complete brand safety,
   keyword and categorization analysis for the text.

GumGum publishes a Language Support Grid; check it before sending non-English text, and set
`languageCode` where the surface accepts it rather than relying on inference for short blocks.

## Rules

- No idempotency key, no documented rate limits, and no webhook for these two surfaces — poll on a
  bounded backoff and reconcile on your own identifier.
- Errors follow the shared envelope: `403 {"message":"Forbidden"}` for a bad key,
  `403 {"message":"Missing Authentication Token"}` for a path that did not match a route.
- Results carry `expiresAt`; persist anything you need to keep.
