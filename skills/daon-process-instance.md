---
name: daon-process-instance
description: Start a process instance and continue it through a specific topic.
api: openapi/daon-trustx-openapi.yml
operations:
- startProcessByInstanceId
- continueProcess
generated: '2026-10-18'
method: generated
generator: extract-docs-artifacts.py skills (deepseek)
source: openapi/daon-trustx-openapi.yml ; every operationId checked against the contract
---

# daon-process-instance

Start a process instance and continue it through a specific topic.

## Steps

1. 1. Start a process instance using `startProcessByInstanceId` with the required headers and body parameters
2. 2. Continue the process using `continueProcess` with path parameters for processDefinitionName, businessKey, and topicName

## Rules

- Authentication requires either ApiKeyAuth (X-Api-Key header) or BearerAuth
- Process operations require specific path parameters like processDefinitionName, businessKey, and topicName
- Both operations use POST method for process execution
