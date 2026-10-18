---
name: daon-process-token-onboarding
description: Issue a TrustX process token so an applicant can run a hosted identity-verification (ID&V) process, then follow the resulting process instance through to its fraud state and user data.
api: daon:trustx-api
spec: ../openapi/daon-trustx-openapi.yml
operations:
- issueTenantJwt
- listProcessDefinitions
- addProcessToken
- getProcessToken
- getProcessInstance
- getProcessInstanceFraudState
- getProcessInstanceUserData
- invalidateProcessToken
generated: '2026-10-18'
method: generated
source: openapi/daon-trustx-openapi.yml
---

# daon-process-token-onboarding

Issue a TrustX process token so an applicant can run a hosted identity-verification (ID&V) process, then follow the resulting process instance through to its fraud state and user data.

## Steps

1. `issueTenantJwt`: exchange the X-Api-Key for a bearer JWT.
2. `listProcessDefinitions`: pick the process definition to run.
3. `addProcessToken`: create an ACTIVE process token. Put applicant attributes (firstName, lastName, email, phoneNumber) and an optional `_redirectUrl` in `parameters` (see https://docs.trustx.com/trust/api-process-token-guide.md).
4. Send the applicant the hosted URL for the token. Use `getProcessToken` to check its status.
5. `getProcessInstance`: poll the instance the token started.
6. `getProcessInstanceFraudState` and `getProcessInstanceUserData`: read the outcome.
7. `invalidateProcessToken`: revoke a token you no longer need.

## Rules

- Every call except `issueTenantJwt` needs `Authorization: Bearer <JWT>`. Get the JWT from `issueTenantJwt` (POST /api/arthr/apiKeys/issue) with your tenant `X-Api-Key`. The host is per tenant and per region: `https://{tenantId}.{fir|gum|oak}.trustx.com`.
- Errors come back as numeric TrustX REST error codes (https://docs.trustx.com/trust/rest-error-codes-full.md). The spec declares no idempotency keys, so check state with a GET before you retry a POST.
