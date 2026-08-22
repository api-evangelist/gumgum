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

GumGum is a Santa Monica-based advertising technology company, founded in 2008, that sells
contextual, CTV/online-video and high-impact display advertising built on its own content
intelligence. Its GumGum Contextual platform (formerly Verity) uses computer vision and natural
language processing to read the text, images, video and audio of a page or asset before the bid,
returning IAB Content Taxonomy classifications, keywords, named entities, brand-safety threats and
sentiment.

- Website — https://gumgum.com/
- Documentation Center — https://gumgum.jira.com/wiki/spaces/VDC
- API Reference — https://gumgum.jira.com/wiki/spaces/VDC/pages/1712030855
- Status — https://status.contextual.gumgum.com
- GitHub — https://github.com/gumgum

## APIs

| API | Base URL | Notes |
|---|---|---|
| GumGum Contextual API | `https://verity-api.gumgum.com` | Page, Video, Intravideo (v2), Image and Text classification. `X-api-key` header auth. Asynchronous submit → poll or webhook callback. |
| GumGum Prebid Header Bidding Endpoint | `https://g2.gumgum.com` | Real-time bidding via the open-source Prebid.js `gumgumBidAdapter` (bidder code `gumgum`, alias `gg`, IAB GVL ID 61). |

## Artifacts

| Dir | File | Method |
|---|---|---|
| `openapi/` | `gumgum-contextual-api-openapi.yml` | generated — transcribed from the Documentation Center; GumGum publishes no OpenAPI |
| `llms/` | `gumgum-llms.txt` | searched — served verbatim at https://gumgum.com/llms.txt |
| `authentication/` | `gumgum-authentication.yml` | derived |
| `conventions/` | `gumgum-conventions.yml` | searched |
| `errors/` | `gumgum-problem-types.yml` | derived + live probe |
| `lifecycle/` | `gumgum-lifecycle.yml` | searched |
| `changelog/` | `gumgum-changelog.yml` | searched |
| `conformance/` | `gumgum-conformance.yml` | searched |
| `data-model/` | `gumgum-data-model.yml` | derived |
| `asyncapi/` | `gumgum-contextual-webhooks.yml` | searched — webhook catalog; no AsyncAPI published |
| `packages/` | `gumgum-packages.yml` | searched |
| `components/` | `gumgum-components.yml` | searched |
| `well-known/` | `gumgum-well-known.yml` | probed — no first-party `/.well-known/` documents |
| `security/` | `gumgum-domain-security.yml` | probed |
| `overlays/` | `gumgum-contextual-api-overlay.yaml` | generated |
| `agentic-access/` | `gumgum-agentic-access.yml` | generated |
| `skills/` | 3 agent skills + `_index.yml` | generated |
| `arazzo/` | `gumgum-classify-video.yml` | generated |
| `mcp/` | `gumgum-mcp.yml` | derived — **candidate only**, GumGum operates no MCP server |

## Gaps found (2026-08-01)

- No published OpenAPI, AsyncAPI, GraphQL, gRPC, MCP server or A2A agent card.
- No `/.well-known/security.txt`, no vulnerability-disclosure program, no trust center.
- No client SDK in any language for the Contextual API — the docs describe a raw HTTPS integration.
- No idempotency contract, no documented rate limits, no deprecation policy, no public pricing.
- No sandbox or test credentials; every call is production.
