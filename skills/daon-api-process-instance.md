---
name: daon-api-process-instance
description: 'Run a TrustX process instance entirely through the API: create it, start it, continue it at a topic, then read the result.'
api: daon:trustx-api
spec: ../openapi/daon-trustx-openapi.yml
operations:
- issueTenantJwt
- createProcessInstance
- startProcessByInstanceId
- continueProcess
- getProcessInstanceWithParameters
- searchProcessInstancesBetweenDates
- updateProcessInstanceFraudState
generated: '2026-10-18'
method: generated
source: openapi/daon-trustx-openapi.yml
---

# daon-api-process-instance

Run a TrustX process instance entirely through the API: create it, start it, continue it at a topic, then read the result.

## Steps

1. `issueTenantJwt`: get a bearer JWT.
2. `createProcessInstance`: create an instance of a process definition.
3. `startProcessByInstanceId`: start it.
4. `continueProcess`: move it forward at a named topic for a business key.
5. `getProcessInstanceWithParameters`: read its state and the extra parameters.
6. `searchProcessInstancesBetweenDates`: find instances in a date window.
7. `updateProcessInstanceFraudState`: record a reviewer's fraud decision.

## Rules

- Every call except `issueTenantJwt` needs `Authorization: Bearer <JWT>`. Get the JWT from `issueTenantJwt` (POST /api/arthr/apiKeys/issue) with your tenant `X-Api-Key`. The host is per tenant and per region: `https://{tenantId}.{fir|gum|oak}.trustx.com`.
- Errors come back as numeric TrustX REST error codes (https://docs.trustx.com/trust/rest-error-codes-full.md). The spec declares no idempotency keys, so check state with a GET before you retry a POST.
