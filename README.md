# GumGum

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
