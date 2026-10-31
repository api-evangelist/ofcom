# Ofcom

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

Ofcom is the Office of Communications, the United Kingdom's independent regulator and competition authority for telecommunications, spectrum, broadcasting, post, and online safety. It licenses UK spectrum, administers the national numbering plan, publishes the Connected Nations reports on fixed and mobile coverage, and supervises the operators (EE, VMO2, Vodafone, Three) rather than selling connectivity itself. Its position in the telecom value chain is therefore upstream of the market it measures — it is a data producer and rule-setter, not a network or a CPaaS aggregator. Its API posture is unusually good for a regulator and unusually narrow in scope. Ofcom runs a real, Ofcom-branded Azure API Management developer portal at api.ofcom.org.uk with open sign-up, an interactive console, published rate-limit tiers, and anonymously downloadable OpenAPI 3.0.1 documents for two APIs — the Connected Nations Broadband API and the Connected Nations Mobile API — both served from the live gateway at api-proxy.ofcom.org.uk and authenticated with an Azure APIM subscription key. Everything else Ofcom publishes (spectrum licence registers, numbering data, market research) is documents and datasets, not APIs, and the community has repeatedly built third-party APIs on top of those files. Ofcom appears once in the CAMARA project participant register but exposes no CAMARA network APIs and is not a GSMA Open Gateway participant — Open Gateway is an operator commitment programme and Ofcom is the regulator, not an operator.

**Areas:** Telecommunications · United Kingdom · Regulator · Broadband · Mobile Network Coverage · Spectrum · Open Data · Connected Nations

## Ofcom on APIs.io

Everything profiled for Ofcom is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/ofcom/](https://apis.io/providers/ofcom/)** — or go straight to one of the APIs or properties below.

### APIs (1)

- [Ofcom Coverage API](https://apis.io/apis/ofcom/ofcom-coverage-api/) — The Coverage API from Ofcom — 1 operation(s) for coverage.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### Arazzo workflows (1)

Multi-step workflows that chain operations into a business task.

- [Ofcom postcode connectivity profile](https://apis.io/arazzos/ofcom/ofcom-postcode-connectivity-profile/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [ofcom](https://apis.io/servers/ofcom/ofcom/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Ofcom Agentic Access](https://apis.io/agentic-access/ofcom/ofcom-agentic-access/)

#### Collections (2)

Postman and Open Collection request collections.

- [Ofcom Connected Nations Broadband API](https://apis.io/collections/ofcom/open-ofcom-connected-nations-broadband-api/)
- [Ofcom Connected Nations Mobile API](https://apis.io/collections/ofcom/open-ofcom-connected-nations-mobile-api/)

#### Overlays (2)

OpenAPI overlays, including conversational phrasing for each operation.

- [Ofcom Connected Nations Broadband Api Overlay](https://apis.io/overlays/ofcom/ofcom-connected-nations-broadband-api-overlay/)
- [Ofcom Connected Nations Mobile Api Overlay](https://apis.io/overlays/ofcom/ofcom-connected-nations-mobile-api-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Ofcom Authentication](https://apis.io/security/ofcom/ofcom-authentication/)
- [Ofcom Domain Security](https://apis.io/security/ofcom/ofcom-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Ofcom Plans](https://apis.io/plans/ofcom/ofcom-plans/)

#### Rate limits (1)

Published request limits.

- [Ofcom Rate Limits](https://apis.io/rate-limits/ofcom/ofcom-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.ofcom.org.uk/)
- [Documentation](https://api.ofcom.org.uk/apis)
- [API reference](https://api.ofcom.org.uk/api-details)
- [Sign up](https://api.ofcom.org.uk/signup)
- [Terms of service](https://www.ofcom.org.uk/siteassets/ofcom/phones-telecoms-and-internet/advice-for-consumers-/broadband-and-mobile-coverage-checker/ofcom-api-terms-of-use-2025.pdf?v=399736)

## API Evangelist rating

**Kin Score 45.1** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 66.1 |
| Contract quality | 48.4 |
| Contract governance | 4.5 |
| Operational transparency | 31.6 |
| Developer ergonomics | 51.8 |
| Access clarity | 55.3 |

**Agent readiness 30.6** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | na |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | na |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | na |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | na |

**Regulatory alignment 22.5** — Telecommunications

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/ofcom/](https://apis.io/providers/ofcom/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Ofcom: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/ofcom/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
