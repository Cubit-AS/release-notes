
## Built by and Upgrades of Electrical Plant
This is used to indicate who built a facility or to register an expansion of an electrical plant.

- **URL**: 
  - `https://plants.cubit.no/api/import/{environment}/plant/builtby`
- **URL Parameters**:
  - `environment`: Has two possible values. 'test' if the instance being synchronized with is a test instance, and 'prod' if it is a production instance. This is to make it more difficult to mistakenly alter production data when intending to change test data.
- **URL Headers**:
  - `api-key`: Required for all requests. Without it, a 401 - Unauthorized response will be received. If the API key is included but does not match the environment specified in the URL, a 400 - Bad Request response will be received.
- **Body**:
  - The body should be in JSON format. Here is an example of a valid body with sample values for registering a new electrical plant:

```json
{
  "meteringPointId": "707057500026392734",
  "builtByElCompanyId": 12345
}
```

- And here is an example of a body for indicating an extension, and not who built the entire plant:

```json
{
  "meteringPointId": "707057500026392734",
  "builtByElCompanyId": 12345,
  "extensionName": "Kjøkken",
  "extensionYearBuilt": 2019
}
```
