---
name: daon-archive-and-audit-search
description: 'Run the asynchronous TrustX searches over process archives and audit messages: start a query, poll its status, then fetch the results.'
api: daon:trustx-api
spec: ../openapi/daon-trustx-openapi.yml
operations:
- issueTenantJwt
- startQuery
- getQueryStatus
- getQueryResults
- getArchiveFile
- startAuditQuery
- getAuditQueryStatus
- getAuditQueryResults
generated: '2026-10-18'
method: generated
source: openapi/daon-trustx-openapi.yml
---

# daon-archive-and-audit-search

Run the asynchronous TrustX searches over process archives and audit messages: start a query, poll its status, then fetch the results.

## Steps

1. `issueTenantJwt`: get a bearer JWT.
2. `startQuery`: returns an executionId. Poll `getQueryStatus` until it completes, then call `getQueryResults`.
3. `getArchiveFile`: download an archive by fileKey.
4. For audits, follow the same start, poll and result pattern with `startAuditQuery`, `getAuditQueryStatus` and `getAuditQueryResults`.

## Rules

- Every call except `issueTenantJwt` needs `Authorization: Bearer <JWT>`. Get the JWT from `issueTenantJwt` (POST /api/arthr/apiKeys/issue) with your tenant `X-Api-Key`. The host is per tenant and per region: `https://{tenantId}.{fir|gum|oak}.trustx.com`.
- Errors come back as numeric TrustX REST error codes (https://docs.trustx.com/trust/rest-error-codes-full.md). The spec declares no idempotency keys, so check state with a GET before you retry a POST.
