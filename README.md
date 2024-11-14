
# API Specification: Customers and Installations

# Testing mermaid

```mermaid
sequenceDiagram
  participant A as AuditService.AuditContreller.SetStatus
  A->>+AuditDB: Start transaction
  A->>+AuditDB: 1. Query for authentication is not needed when JWT Tokens are indroduced
  A->>+AuditDB: 2. Sets new Audit Status
  A->>+AuditDB: 3. Updates History
  A->>+AuditDB: 6. MarkAudit to update Last Audit Date (requires rewrite)
  A->>+AuditDB: 7. Save after more logic is performed
  A->>+AuditDB: Save notifications needed for Archive and Lantern 
  AuditDB->>+A: Commit transaction
  A->>+ServiceBus: Send notifications that audit status was updated
  ServiceBus->>+Archive: 4. Save Case (3rd party call)
  ServiceBus->>+LanterService: 5. Send notifications
```


## Overview
This API provides the functionality to create, update, delete, and retrieve customers and plant data from Cubit Core. The API uses "upsert" endpoints for creating and updating, meaning the same endpoint handles both insertions and updates.

## Endpoints
### Customers
- **Create/Update**: `[POST]` Endpoint with details on request parameters, headers, and example JSON body.
- **Delete**: `[DELETE]` Endpoint with required parameters and headers.
- **Retrieve**: `[GET]` Endpoint with required parameters and headers.

### Installations
- **Create/Update**: `[POST]` Endpoint for installations with details on request parameters, headers, and JSON body structure.
- **Delete**: `[DELETE]` Endpoint for installations.
- **Retrieve**: `[GET]` Endpoint for installations.

## Additional Information
- **Environment Parameters**: Details on the 'test' and 'prod' environment parameters.
- **API Key**: Information on the necessity of the API key in headers for authorization.
- **Error Handling**: Description of common error responses like 401 - Unauthorized and 400 - Bad Request.

## Example Requests
- Provide JSON examples for creating or updating customers and installations.
- Describe scenarios where these examples can be applied.

## Contact
For further information or queries, contact Mindaugas Guzas at mindaugas@cubit.no
