
## Plants

### Creation and Updating

- **URL**: 
  - [POST] `https://plants.cubit.no/api/import/{environment}/plant`
- **URL Parameters**:
  - `environment`: Has two possible values. 'test' if the instance being synchronized with is a test instance, and 'prod' if it is a production instance. This is to make it more difficult to mistakenly alter production data when intending to change test data.
- **URL Headers**:
  - `api-key`: Required for all requests. Without it, a 401 - Unauthorized response will be received. If the API key is included but does not match the environment specified in the URL, a 400 - Bad Request response will be received.
- **Body**:
  - The body should be in JSON format. Here is an example of a valid body with sample values. Also included in the same request are the hierarchy of the plants, i.e., the connection point, transformer, and power station. Fields needing more information are described after the example.

```json
{
  "ownerId": "1234567",
  "customerChangeFrom": "2020-01-01",
  ...
  "netStation": {
    "name": "Gamlevn.79",
    "address": {
      "addressText": "Gamlevn.79",
      "postalCode": "2040"
    }
  }
}
```

- **auditSpecificInfo**: Optional. If omitted, values for plant type, inspection area, risk category group, and inspection rate will be derived from consumptionCode and industrialClassification.
- **builtByElCompanyId**: Should be specified as the electrical company ID from the electrical company register, not the organization number or other identifier.
- **customerChangeFrom**: Used in connection with a customer change at a plant where the change does not apply from today's date. This field should then contain the date from which this change applies.

### Deletion

- **URL**: 
  - [DELETE] `https://plants.cubit.no/api/import/{environment}/plant/{meteringPointId}`
- **URL Parameters**:
  - `environment`: Has two possible values. 'test' for a test instance, and 'prod' for a production instance.
  - `meteringPointId`: The metering point ID of the metering point to be deleted.
- **URL Headers**:
  - `api-key`: Required for all requests. Without it, a 401 - Unauthorized response will be received.

### Retrieval

- **URL**: 
  - [GET] `https://plants.cubit.no/api/plant/{meteringPointId}`
- **URL Parameters**:
  - `meteringPointId`: The metering point ID of the metering point to be retrieved.
- **URL Headers**:
  - `api-key`: Required for all requests. Without it, a 401 - Unauthorized response will be received.
