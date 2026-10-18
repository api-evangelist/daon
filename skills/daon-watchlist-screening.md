---
name: daon-watchlist-screening
description: Create a TrustX V2 watchlist, add entries to it and query it. The face watchlist endpoints are marked deprecated, so use the V2 ones.
api: daon:trustx-api
spec: ../openapi/daon-trustx-openapi.yml
operations:
- issueTenantJwt
- createWatchlistV2
- listWatchlistsV2
- createWatchlistEntry
- listWatchlistEntries
- queryWatchlistV2
- getWatchlistUsage
generated: '2026-10-18'
method: generated
source: openapi/daon-trustx-openapi.yml
---

# daon-watchlist-screening

Create a TrustX V2 watchlist, add entries to it and query it. The face watchlist endpoints are marked deprecated, so use the V2 ones.

## Steps

1. `issueTenantJwt`: get a bearer JWT.
2. `createWatchlistV2`, or `listWatchlistsV2` to find an existing watchlist.
3. `createWatchlistEntry`: add an entry. `listWatchlistEntries` reviews them.
4. `queryWatchlistV2`: screen a subject against the list.
5. `getWatchlistUsage`: check its size. Guide: https://docs.trustx.com/trust/managing-watchlists-via-api.md

## Rules

- Every call except `issueTenantJwt` needs `Authorization: Bearer <JWT>`. Get the JWT from `issueTenantJwt` (POST /api/arthr/apiKeys/issue) with your tenant `X-Api-Key`. The host is per tenant and per region: `https://{tenantId}.{fir|gum|oak}.trustx.com`.
- Errors come back as numeric TrustX REST error codes (https://docs.trustx.com/trust/rest-error-codes-full.md). The spec declares no idempotency keys, so check state with a GET before you retry a POST.
