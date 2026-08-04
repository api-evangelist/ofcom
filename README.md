# Ofcom (ofcom)

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

Ofcom is the Office of Communications, the United Kingdom's independent regulator and competition authority for telecommunications, spectrum, broadcasting, post, and online safety. It licenses UK spectrum, administers the national numbering plan, publishes the Connected Nations reports on fixed and mobile coverage, and supervises the operators (EE, VMO2, Vodafone, Three) rather than selling connectivity itself. Its position in the telecom value chain is upstream of the market it measures — a data producer and rule-setter, not a network or a CPaaS aggregator.

Its API posture is unusually good for a regulator and unusually narrow in scope. Ofcom runs a real, Ofcom-branded Azure API Management developer portal at [api.ofcom.org.uk](https://api.ofcom.org.uk/) with open sign-up, an interactive console, published rate-limit tiers, and anonymously downloadable OpenAPI 3.0.1 documents for two APIs — the Connected Nations Broadband API and the Connected Nations Mobile API — both served from the live gateway at `api-proxy.ofcom.org.uk` and authenticated with an Azure APIM subscription key. Everything else Ofcom publishes (spectrum licence registers, numbering data, market research) is documents and datasets rather than APIs, and the community has repeatedly built third-party APIs on top of those files.

Ofcom appears once in the CAMARA project participant register but exposes no CAMARA network APIs, and it is not a GSMA Open Gateway participant — Open Gateway is an operator commitment programme and Ofcom is the regulator, not an operator.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/ofcom/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/ofcom/refs/heads/main/apis.yml)

## Tags

- Telecommunications
- United Kingdom
- Regulator
- Broadband
- Mobile Network Coverage
- Spectrum
- Open Data
- Connected Nations

## Timestamps

- **Created:** 2026-07-25
- **Modified:** 2026-07-25

## APIs

### Ofcom Connected Nations Broadband API

Returns predicted fixed broadband availability for a UK postcode from Ofcom's Connected Nations dataset — per-premises maximum predicted download and upload speeds broken out by Basic, Superfast, and Ultrafast bands, plus percentage availability of each speed category. A single GET operation, `GET /coverage/{PostCode}`, authenticated with an Azure API Management subscription key sent as the `Ocp-Apim-Subscription-Key` header or a `subscription-key` query parameter.

- **Human URL:** [https://api.ofcom.org.uk/apis](https://api.ofcom.org.uk/apis)
- **Base URL:** `https://api-proxy.ofcom.org.uk/broadband`

#### Tags

- Broadband
- Coverage
- United Kingdom
- Open Data
- Connected Nations

#### Properties

- [OpenAPI](openapi/ofcom-connected-nations-broadband-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://api.ofcom.org.uk/)
- [API Reference](https://api.ofcom.org.uk/api-details)

### Ofcom Connected Nations Mobile API

Returns predicted mobile coverage for a UK postcode from Ofcom's Connected Nations dataset, scored 0 (none), 3 (limited), or 4 (likely) for each of the four UK mobile network operators — EE, H3 (Three), TF (Virgin Media O2), and VO (Vodafone) — split by voice and data and by indoor and outdoor, with separate no-4G variants. A single GET operation, `GET /coverage/{PostCode}`, authenticated with an Azure API Management subscription key sent as the `Ocp-Apim-Subscription-Key` header or a `subscription-key` query parameter.

- **Human URL:** [https://api.ofcom.org.uk/apis](https://api.ofcom.org.uk/apis)
- **Base URL:** `https://api-proxy.ofcom.org.uk/mobile`

#### Tags

- Mobile Network Coverage
- Coverage
- United Kingdom
- Open Data
- Connected Nations

#### Properties

- [OpenAPI](openapi/ofcom-connected-nations-mobile-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://api.ofcom.org.uk/)
- [API Reference](https://api.ofcom.org.uk/api-details)

## Plans

Rate limits are published in the product descriptions on the portal, which is unusually transparent for a public-sector API. All four products require Ofcom approval before a subscription key is issued.

| Product | Rate limit | Monthly quota |
| --- | --- | --- |
| Broadband Coverage (Basic) | 100 calls/minute | 50,000 requests |
| Broadband Coverage (Premium) | 500 calls/minute | 150,000 requests |
| Mobile Coverage (Basic) | 100 calls/minute | 50,000 requests |
| Mobile Coverage (Premium) | 500 calls/minute | 150,000 requests |

## Links

- [Website](https://www.ofcom.org.uk/)
- [Developer Portal](https://api.ofcom.org.uk/)
- [APIs](https://api.ofcom.org.uk/apis)
- [Products / Plans](https://api.ofcom.org.uk/products)
- [Sign Up](https://api.ofcom.org.uk/signup)
- [Mobile and Broadband Checker](https://checker.ofcom.org.uk/)
