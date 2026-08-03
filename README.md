# Aescape

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
