---
name: Check UK fixed broadband coverage for a postcode
description: Look up Ofcom's predicted fixed broadband availability for a UK postcode — per-premises maximum predicted download and upload speeds by Basic, Superfast and Ultrafast band — using the Ofcom Connected Nations Broadband API.
api: openapi/ofcom-connected-nations-broadband-api-openapi.yml
operations:
  - CoverageByPostCodeGet
generated: '2026-07-25'
method: generated
source: openapi/ofcom-connected-nations-broadband-api-openapi.yml, conventions/ofcom-conventions.yml, errors/ofcom-problem-types.yml
---

# Check UK fixed broadband coverage for a postcode

Ofcom's Connected Nations Broadband API returns **predicted** fixed broadband
availability for every premises in a UK postcode. It is a regulator's published
dataset, not a live line test.

## Before you start

- Get a subscription key for the **Broadband Coverage** product at
  <https://api.ofcom.org.uk/signup>. Sign-up is self-serve, but every product is
  approval-gated — an Ofcom person approves the subscription before a key is issued.
- The Mobile API needs a **separate** key. One key does not cover both products.
- Base URL: `https://api-proxy.ofcom.org.uk/broadband`

## Authentication

Send the key on every request as the `Ocp-Apim-Subscription-Key` header:

```
Ocp-Apim-Subscription-Key: <your broadband subscription key>
```

A `subscription-key` query parameter is also accepted, but prefer the header — a
query parameter leaks the key into logs and referrers.

Calling without a key returns HTTP `401` with the body
`Access denied due to missing subscription key.`

## Steps

1. **Normalise the postcode.** Uppercase it and strip whitespace (`SW1A 1AA` →
   `SW1A1AA`) before putting it in the path.
2. **Call `CoverageByPostCodeGet`** — `GET /coverage/{PostCode}`. `PostCode` is the
   only parameter, it is a required path parameter of type string, and there is no
   request body, no pagination and no filtering.
3. **Read the envelope.** A `200` returns a single `FixedAvailability` object:
   `PostCode` plus an `Availability` array of `BroadbandProvision` records, one per
   premises, keyed on `UPRN`.
4. **Interpret the speed fields.** `MaxBbPredictedDown`/`Up` (Basic),
   `MaxSfbbPredictedDown`/`Up` (Superfast), `MaxUfbbPredictedDown`/`Up` (Ultrafast)
   and `MaxPredictedDown`/`Up` (overall maximum).
5. **Filter the sentinel.** Every speed field has a minimum of `-1`, which means
   *no prediction available* — not a negative speed. Drop `-1` values before
   averaging, summing or charting, or your aggregate will be wrong.
6. **Aggregate to the postcode** if you need a single answer: count premises above a
   speed threshold rather than reporting one premises' figure as the postcode's.

## Errors

- `401` — missing or invalid subscription key (gateway level, not in the spec).
- `404` — `FixedAvailabilityNotFound`, body `{PostCode, ErrorMessage}`. The postcode
  is not in the dataset; check the normalisation before assuming it does not exist.
- `500` — `GeneralError`, body `{ErrorMessage}`. Retry with backoff.

There are no machine-readable error codes — only free-text `ErrorMessage`. Key your
handling on the HTTP status.

## Rules

- **Respect the published limits.** Basic: 100 calls/minute, 50,000 requests/month.
  Premium: 500 calls/minute, 150,000 requests/month. Ofcom documents no rate-limit
  response headers, so throttle client-side rather than reacting to a header that
  is not there.
- **Cache aggressively.** The dataset is a periodically refreshed Ofcom publication,
  not live data. Re-requesting the same postcode inside a reporting cycle burns
  quota for an identical answer.
- **No writes exist.** The whole surface is read-only, so retries are inherently
  safe and no idempotency key is needed.
- **Say "predicted".** Present results as Ofcom's predicted availability, never as a
  measured or guaranteed speed.
- Terms of use: <https://www.ofcom.org.uk/siteassets/ofcom/phones-telecoms-and-internet/advice-for-consumers-/broadband-and-mobile-coverage-checker/ofcom-api-terms-of-use-2025.pdf?v=399736>
- Support: cnapisupport@ofcom.org.uk
