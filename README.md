# Ofcom (ofcom)

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
