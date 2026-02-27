# Delete Category

Delete an Outlook category from the user's master list of categories.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: DELETE
- **Path**: `/me/outlook/masterCategories/{category-id}`
- **Operation ID**: `deleteCategory`
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
| category-id | path | string | Yes | The unique identifier of the category to delete |

## Example Request

```bash
curl -X DELETE "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/outlook/masterCategories/afc97c36-af15-4e96-bf52-e228c84d4567" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
```

## Instructions

Use this operation to permanently delete a category from the user's mailbox. Provide the category identifier in the URL path. Returns 204 No Content on successful deletion. This action cannot be undone.
