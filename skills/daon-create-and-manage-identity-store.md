---
name: daon-create-and-manage-identity-store
description: Create a new identity store and manage its lifecycle through updates, statistics retrieval, and deletion.
api: openapi/daon-trustx-openapi.yml
operations:
- addStore
- updateStore
- getStoreStats
- deleteStore
generated: '2026-10-18'
method: generated
generator: extract-docs-artifacts.py skills (deepseek)
source: openapi/daon-trustx-openapi.yml ; every operationId checked against the contract
---

# daon-create-and-manage-identity-store

Create a new identity store and manage its lifecycle through updates, statistics retrieval, and deletion.

## Steps

1. 1. Create a new identity store using `addStore` with the required store configuration fields in the request body
2. 2. Update the store's configuration using `updateStore` with the storeName path parameter and updated fields in the request body
3. 3. Retrieve store statistics using `getStoreStats` with the storeName path parameter
4. 4. Delete the store when no longer needed using `deleteStore` with the storeName path parameter

## Rules

- Authentication required using either ApiKeyAuth (X-Api-Key header) or BearerAuth (Authorization header)
- All operations except listStores require the storeName path parameter to identify the specific store
- The deleteStore operation is not idempotent - repeated calls may result in errors if the store no longer exists
