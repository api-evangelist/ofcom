---
name: Check UK mobile network coverage for a postcode
description: Look up Ofcom's predicted mobile coverage for a UK postcode across all four UK mobile network operators — EE, Three, Virgin Media O2 and Vodafone — split by voice/data and indoor/outdoor, using the Ofcom Connected Nations Mobile API.
api: openapi/ofcom-connected-nations-mobile-api-openapi.yml
operations:
  - CoverageByPostCodeGet
generated: '2026-07-25'
method: generated
source: openapi/ofcom-connected-nations-mobile-api-openapi.yml, conventions/ofcom-conventions.yml, errors/ofcom-problem-types.yml
---

# Check UK mobile network coverage for a postcode

Ofcom's Connected Nations Mobile API returns **predicted** mobile coverage per
premises for all four UK mobile network operators. Ofcom is the regulator that
collects this from the operators — it is one authoritative cross-operator view, not
four vendor checkers.

## Before you start

- Get a subscription key for the **Mobile Coverage** product at
  <https://api.ofcom.org.uk/signup>. Approval-gated, like every Ofcom product.
- The Broadband API needs a **separate** key.
- Base URL: `https://api-proxy.ofcom.org.uk/mobile`

## Authentication

```
Ocp-Apim-Subscription-Key: <your mobile subscription key>
```

The `subscription-key` query parameter also works; prefer the header. No key returns
`401 Access denied due to missing subscription key.`

## Steps

1. **Normalise the postcode** — uppercase, whitespace stripped (`SW1A 1AA` →
   `SW1A1AA`).
2. **Call `CoverageByPostCodeGet`** — `GET /coverage/{PostCode}`. One required path
   parameter, no body, no query filters, no pagination.
3. **Unwrap the array.** This API returns a `MobileAvailabilityArray` — an **array**
   of `MobileAvailability` envelopes — where the Broadband API returns a single
   object. Do not assume the two APIs are symmetric; that is the most common
   integration bug across the pair.
4. **Read the provision records.** Each envelope's `Availability` array holds
   `MobileProvision` records keyed on `UPRN`, with 32 coverage fields following the
   pattern `{EE|H3|TF|VO}{Voice|Data}{Outdoor|Indoor}` plus an optional `No4g`
   suffix.
5. **Map the operator codes** before showing anything to a person:
   `EE` = EE, `H3` = Three UK, `TF` = Virgin Media O2, `VO` = Vodafone UK.
6. **Interpret the values as an enum, not a scale**: `0` = none (do not expect
   coverage), `3` = limited (coverage may be limited), `4` = likely (you are likely
   to have coverage). Ofcom's own spec states that `1` and `2` are no longer used.
   Never average these numbers — a mean of 0 and 4 is not "2".
7. **Choose the right variant.** The `No4g` fields report coverage excluding 4G, for
   devices or use cases that cannot use it. Use the plain fields unless you
   specifically need the no-4G case, and never mix the two in one comparison.
8. **Pick indoor vs outdoor deliberately.** Indoor is the stricter, more realistic
   figure for a home or office question; outdoor flatters every operator.

## Errors

- `401` — missing or invalid subscription key (gateway level, not in the spec).
- `404` — `MobileAvailabilityNotFound`, body `{PostCode, ErrorMessage}`.
- `500` — `GeneralError`, body `{ErrorMessage}`. Retry with backoff.

## Rules

- **Respect the published limits.** Basic: 100 calls/minute, 50,000 requests/month.
  Premium: 500 calls/minute, 150,000 requests/month. No rate-limit headers are
  documented — throttle client-side.
- **Cache.** The dataset changes on Ofcom's reporting cycle, not per request.
- **Read-only surface** — retries are safe, no idempotency key exists or is needed.
- **Say "predicted".** These are Ofcom predictions collected from operators, not
  measurements from the caller's device.
- To compare fixed and mobile for the same premises, call the Broadband API
  separately and join on `UPRN` client-side — Ofcom exposes no combined operation.
- Support: cnapisupport@ofcom.org.uk
