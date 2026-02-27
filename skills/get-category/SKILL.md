# Get Category

Retrieve a specific Outlook category by its identifier.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/me/outlook/masterCategories/{category-id}`
- **Operation ID**: `getCategory`
- **Tag**: Categories
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/outlook/masterCategories/{category-id}`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `MailboxSettings.ReadWrite`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| category-id | path | string | Yes | The unique identifier of the category |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/outlook/masterCategories/afc97c36-af15-4e96-bf52-e228c84d4567" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "id": "afc97c36-af15-4e96-bf52-e228c84d4567",
  "displayName": "Blue Category",
  "color": "preset7"
}
```

## Instructions

Use this operation to retrieve the details of a specific category by providing its unique identifier in the URL path. The response includes the category's display name, color preset, and identifier.
