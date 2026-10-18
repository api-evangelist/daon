---
name: daon-passkey-registration
description: Create a user in a TrustX identity store, register a passkey (FIDO/WebAuthn) for that user, then authenticate with it.
api: daon:trustx-api
spec: ../openapi/daon-trustx-openapi.yml
operations:
- issueTenantJwt
- createUser
- getUser
- createPasskeyRegistrationForUser
- completePasskeyRegistrationWithSession
- getUserPasskeyRegistrationRecord
- createPasskeyAuthenticationForUser
- completePasskeyAuthenticationWithSession
generated: '2026-10-18'
method: generated
source: openapi/daon-trustx-openapi.yml
---

# daon-passkey-registration

Create a user in a TrustX identity store, register a passkey (FIDO/WebAuthn) for that user, then authenticate with it.

## Steps

1. `issueTenantJwt`: get a bearer JWT.
2. `createUser`: create the user in a store (`storeName`), or `getUser` to load an existing one.
3. `createPasskeyRegistrationForUser`: get the credential-creation request and pass it to the browser or device WebAuthn API.
4. `completePasskeyRegistrationWithSession`: send back the attestation the authenticator produced.
5. `getUserPasskeyRegistrationRecord`: audit the registration.
6. `createPasskeyAuthenticationForUser` then `completePasskeyAuthenticationWithSession`: run an assertion ceremony.

## Rules

- Every call except `issueTenantJwt` needs `Authorization: Bearer <JWT>`. Get the JWT from `issueTenantJwt` (POST /api/arthr/apiKeys/issue) with your tenant `X-Api-Key`. The host is per tenant and per region: `https://{tenantId}.{fir|gum|oak}.trustx.com`.
- Errors come back as numeric TrustX REST error codes (https://docs.trustx.com/trust/rest-error-codes-full.md). The spec declares no idempotency keys, so check state with a GET before you retry a POST.
