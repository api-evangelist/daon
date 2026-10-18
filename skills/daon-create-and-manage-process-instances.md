---
name: daon-create-and-manage-process-instances
description: Create a process instance and perform common management operations on it.
api: openapi/daon-trustx-openapi.yml
operations:
- createProcessInstance
- getProcessInstance
- updateProcessInstanceFraudState
- searchProcessInstancesBetweenDates
- exportProcessInstancesToCsv
generated: '2026-10-18'
method: generated
generator: extract-docs-artifacts.py skills (deepseek)
source: openapi/daon-trustx-openapi.yml ; every operationId checked against the contract
---

# daon-create-and-manage-process-instances

Create a process instance and perform common management operations on it.

## Steps

1. 1. Create a new process instance using `createProcessInstance` operation with required request body fields
2. 2. Retrieve the created process instance details using `getProcessInstance` operation with the `processInstanceId` path parameter
3. 3. Update the fraud state of the process instance using `updateProcessInstanceFraudState` operation with the `processInstanceId` path parameter and request body
4. 4. Search for process instances using `searchProcessInstancesBetweenDates` operation with query parameters for date ranges
5. 5. Export search results to CSV using `exportProcessInstancesToCsv` operation with request body containing search criteria

## Rules

- Authentication requires either ApiKeyAuth (X-Api-Key header) or BearerAuth (Authorization header with Bearer token)
- Most operations require the processInstanceId path parameter to identify specific instances
- Search operations support date range filtering through query parameters
- Export operations generate CSV files from search results
