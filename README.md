# Aescape

Aescape is a New York City lifestyle-robotics company, founded in 2017 by Eric Litman, that builds a fully automated AI-powered robotic massage platform. Its table uses sensors and computer vision to map over one million 3D data points of a person's body, then drives heated robotic arms through massage techniques at a user-selected pressure, duration and focus area. Sessions run 15 to 60 minutes and are booked through a mobile and web app. Tables are deployed in Equinox clubs, Four Seasons, Marriott and Ritz-Carlton properties, spas and corporate wellness sites across North America, alongside an Aescape One home product.

- https://www.aescape.com/

## API posture

Aescape publishes **no public developer API**. Contract discovery was run against every host on 2026-07-31 and found no OpenAPI, AsyncAPI, GraphQL, MCP server or A2A agent card.

| Host | What it is | Public contract |
|---|---|---|
| `api.aescape.com` | AWS API Gateway serving the consumer app | none — every path returns 404 `{"message":"Not Found"}` |
| `developer.aescape.com` | Developer documentation site | none — 401 on every path, `WWW-Authenticate: Basic realm="Developer Docs"` |
| `app.aescape.com` | Flutter web SPA (booking) | none — 200 HTML catch-all on every path, including `/.well-known/*` |
| `aescape-8ocoec.zitadel.cloud` | Aescape production identity tenant | **OpenID Connect discovery document (200)** |

The one anonymously reachable machine-readable contract in the estate is the OIDC discovery document for Aescape's Zitadel identity tenant. It is saved verbatim and profiled into `authentication/` and `scopes/`.

## Artifacts

- `well-known/` — every `/.well-known/` path probed with status, plus the OIDC discovery document verbatim
- `authentication/` — identity profile (OIDC, PKCE S256, five grant types)
- `scopes/` — the six advertised OIDC scopes; no Aescape-specific application scopes are published
- `conformance/` — standards conformance plus the full contract-discovery record
- `security/` — TLS, HSTS, DNSSEC, CAA, SPF and DMARC posture
- `llms/` — generated llms.txt (Aescape serves none)

No `a2a/`, `mcp/`, `openapi/`, `asyncapi/`, `packages/` or `skills/` directory exists because no such artifact was found. Nothing was authored on Aescape's behalf.
