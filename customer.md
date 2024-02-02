
# API Documentation

## Synchronization of Customers and Facilities

This document covers the APIs used to create, update, delete, or retrieve customers and plants from Cubit Core.

### Endpoints for Creation and Updating:
The endpoints for creating and updating are 'upsert' endpoints. That means there are no separate endpoints for update and insert; the same endpoint is used for both. If an element does not exist, it will be created. If it exists, it will be updated.

## Customers

### Creation and Updating

- **URL**: 
  - [POST] `https://plants.cubit.no/api/import/{environment}/customer`
- **URL Parameters**:
  - `environment`: Can be 'test' for a test instance or 'prod' for a production instance. This distinction is made to prevent accidental changes to production data when intending to modify test data.
- **URL Headers**:
  - `api-key`: Required for all requests. Without it, a 401 - Unauthorized response will be received. If the API key does not match the environment specified in the URL, a 400 - Bad Request response will be received.
- **Body**:
  - The body should be in JSON format. Below is an example with sample values. Details for each field are described below the example.

```json
{
  "Number": "1234567",
  "FirstName": "Ola",
  "LastName": "Normann",
  ...
}
```

- **SocialSecurityNumber and OrganizationNumber**: SocialSecurityNumber is used for private customers, and OrganizationNumber for corporate customers. It's possible to use both, but it doesn't make sense for most customers. SocialSecurityNumbers are transformed as ExternalHashID and not saved as string in customer database.
- **AcceptElectronicCommunication**: Indicates whether the customer has consented to receive electronic communication, like documents via email instead of letters.

### Deletion

- **URL**: 
  - [DELETE] `https://plants.cubit.no/api/import/{environment}/customer/{number}`
- **URL Parameters**:
  - `environment`: Can be 'test' for a test instance or 'prod' for a production instance.
  - `number`: Customer number of the customer to be deleted.
- **URL Headers**:
  - `api-key`: Required for all requests. Without it, a 401 - Unauthorized response will be received.

### Retrieval

- **URL**: 
  - [GET] `https://plants.cubit.no/api/customer/{number}`
- **URL Parameters**:
  - `number`: Customer number of the customer to be retrieved.
- **URL Headers**:
  - `api-key`: Required for all requests. Without it, a 401 - Unauthorized response will be received.
