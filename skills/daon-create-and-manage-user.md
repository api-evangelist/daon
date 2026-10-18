---
name: daon-create-and-manage-user
description: Create a new user in an identity store and perform common management operations.
api: openapi/daon-trustx-openapi.yml
operations:
- createUser
- getUser
- updateUser
- deleteUser
generated: '2026-10-18'
method: generated
generator: extract-docs-artifacts.py skills (deepseek)
source: openapi/daon-trustx-openapi.yml ; every operationId checked against the contract
---

# daon-create-and-manage-user

Create a new user in an identity store and perform common management operations.

## Steps

1. 1. Create a new user using `createUser` with the required fields in the request body
2. 2. Get the created user details using `getUser` with the `storeName` path parameter and `userId` path parameter
3. 3. Update the user using `updateUser` with the `storeName` and `userId` path parameters and fields to update in the request body
4. 4. Delete the user using `deleteUser` with the `storeName` and `userId` path parameters

## Rules

- Authentication requires either ApiKeyAuth with X-Api-Key header or BearerAuth
- The `updateUser` operation only requires fields to be updated in the request body
- User operations require the `storeName` path parameter to identify the identity store
- User identification uses either internal `userId` or external `extId` path parameters
