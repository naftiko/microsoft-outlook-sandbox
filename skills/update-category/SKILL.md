# Update Category

Update the properties of an existing Outlook category.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: PATCH
- **Path**: `/me/outlook/masterCategories/{category-id}`
- **Operation ID**: `updateCategory`
- **Tag**: Categories
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/outlook/masterCategories/{category-id}`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `MailboxSettings.ReadWrite`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| category-id | path | string | Yes | The unique identifier of the category |

## Request Body

| Field | Type | Description |
|-------|------|-------------|
| displayName | string | The updated display name of the category |
| color | string | The updated color preset for the category |

## Example Request

```bash
curl -X PATCH "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/outlook/masterCategories/afc97c36-af15-4e96-bf52-e228c84d4567" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "displayName": "Project Beta",
    "color": "preset12"
  }'
```

## Example Response

```json
{
  "id": "afc97c36-af15-4e96-bf52-e228c84d4567",
  "displayName": "Project Beta",
  "color": "preset12"
}
```

## Instructions

Use this operation to update the display name or color of an existing category. Provide the category identifier in the URL path and include the properties to update in the request body. Only the provided fields will be updated.
