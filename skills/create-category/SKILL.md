# Create Category

Create a new Outlook category in the user's master list of categories.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: POST
- **Path**: `/me/outlook/masterCategories`
- **Operation ID**: `createCategory`
- **Tag**: Categories
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/outlook/masterCategories`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `MailboxSettings.ReadWrite`

## Request Body

| Field | Type | Description |
|-------|------|-------------|
| displayName | string | The display name of the category |
| color | string | The color preset for the category (e.g., preset0 through preset24) |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/outlook/masterCategories" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "displayName": "Project Alpha",
    "color": "preset9"
  }'
```

## Example Response

```json
{
  "id": "afc97c36-af15-4e96-bf52-e228c84d4567",
  "displayName": "Project Alpha",
  "color": "preset9"
}
```

## Instructions

Use this operation to create a new category in the user's mailbox. Provide a unique display name and a color preset. The response returns the newly created category with its assigned identifier. Returns 201 on success.
