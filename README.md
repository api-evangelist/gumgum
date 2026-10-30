# GumGum

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

GumGum is a Santa Monica-based advertising technology company, founded in 2008, that sells contextual, CTV/online-video and high-impact display advertising built on its own content intelligence. Its GumGum Contextual platform (formerly Verity) uses in-house computer vision and natural language processing to read the text, images, video and audio of a page or asset before the bid, returning IAB Content Taxonomy classifications (v1, v2 and v3), extracted keywords, named entities, brand-safety and suitability threats, and sentiment. That analysis is exposed to publishers, DSPs, agencies and advertisers as a server-to-server REST API at verity-api.gumgum.com with separate Page, Video, Intravideo, Image and Text surfaces, plus an asynchronous webhook callback for delivering completed classifications. GumGum also ships an open-source Prebid.js bid adapter for header bidding, and holds Media Rating Council accreditation for content-level classification across desktop, mobile web and CTV.

**Areas:** Advertising · AdTech · Contextual Advertising · Brand Safety · content-classification · Computer Vision · Natural Language Processing · Video Analysis · Image Analysis · Connected TV · Header Bidding · Programmatic Advertising

## GumGum on APIs.io

Everything profiled for GumGum is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/gumgum/](https://apis.io/providers/gumgum/)** — or go straight to one of the APIs or properties below.

### APIs (6)

- [GumGum Prebid Header Bidding Endpoint](https://apis.io/apis/gumgum/gumgum-prebid-header-bidding-endpoint/) — GumGum's real-time bidding endpoint for header bidding, integrated through the open-source Prebid.js gumgumBidAdapter (bidder code gumgum, alias gg, IAB GVL…
- [GumGum Image API](https://apis.io/apis/gumgum/gumgum-image-api/) — Contextual classification, keyword and threat analysis of a single image.
- [GumGum Intravideo API](https://apis.io/apis/gumgum/gumgum-intravideo-api/) — Frame-level (intravideo) classification of a video asset. Version 2 of the video classification surface.
- [GumGum Page API](https://apis.io/apis/gumgum/gumgum-page-api/) — Contextual classification and brand-safety analysis of a web page URL.
- [GumGum Text API](https://apis.io/apis/gumgum/gumgum-text-api/) — Contextual classification, keyword and brand-safety analysis of a raw block of text.
- [GumGum Video API](https://apis.io/apis/gumgum/gumgum-video-api/) — Contextual classification and brand-safety analysis of a video asset, including its audio track.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### Arazzo workflows (1)

Multi-step workflows that chain operations into a business task.

- [Classify a video with GumGum Contextual and retrieve the result](https://apis.io/arazzos/gumgum/gumgum-classify-video/)

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Gumgum Contextual Webhooks](https://apis.io/asyncapis/gumgum/gumgum-contextual-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [gumgum-contextual](https://apis.io/servers/gumgum/gumgum-contextual/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Gumgum Agentic Access](https://apis.io/agentic-access/gumgum/gumgum-agentic-access/)

#### Collections (1)

Postman and Open Collection request collections.

- [GumGum Contextual API](https://apis.io/collections/gumgum/open-gumgum-contextual-api/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Gumgum Contextual Api Overlay](https://apis.io/overlays/gumgum/gumgum-contextual-api-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Gumgum Authentication](https://apis.io/security/gumgum/gumgum-authentication/)
- [Gumgum Domain Security](https://apis.io/security/gumgum/gumgum-domain-security/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://gumgum.com/)
- [Documentation](https://gumgum.jira.com/wiki/spaces/VDC)
- [Getting started](https://gumgum.jira.com/wiki/spaces/VDC/pages/1712095256)
- [API reference](https://gumgum.jira.com/wiki/spaces/VDC/pages/1712030855)
- [Support](https://gumgum.jira.com/wiki/spaces/VDC/pages/1728217585)
- [Blog](https://gumgum.com/blog)
- [Compliance](https://gumgum.com/accreditation)
- [Terms of service](https://gumgum.com/terms-and-policies)
- [Privacy policy](https://gumgum.com/privacy-policy)
- [GitHub](https://github.com/gumgum)
- [Status](https://status.contextual.gumgum.com)

## API Evangelist rating

**Kin Score 42.2** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 78.6 |
| Contract quality | 22.6 |
| Contract governance | 18.2 |
| Operational transparency | 42.1 |
| Developer ergonomics | 58.9 |
| Access clarity | 35.5 |

**Agent readiness 29.8** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | — |
| Rate Limit Signal | — |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 27.3** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/gumgum/](https://apis.io/providers/gumgum/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for GumGum: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/gumgum/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
