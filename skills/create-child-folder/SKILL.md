# Create Child Folder

Create a new child folder under a specific mail folder, enabling nested folder organization.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: POST
- **Path**: `/me/mailFolders/{mailFolder-id}/childFolders`
- **Operation ID**: `createChildFolder`
- **Tag**: MailFolders
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/{mailFolder-id}/childFolders`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Mail.ReadWrite`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `mailFolder-id` | string | Yes | The unique identifier of the parent mail folder |

## Request Body

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `displayName` | string | Yes | The display name of the new child folder |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/AAMkAGI1AAAEJAAA=/childFolders" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "displayName": "Sub-Folder"
  }'
```

## Example Response

```json
{
  "id": "AAMkAGI1AAAEJAAA=",
  "displayName": "Sub-Folder",
  "parentFolderId": "AAMkAGI1AAAAAA=",
  "childFolderCount": 0,
  "totalItemCount": 0,
  "unreadItemCount": 0,
  "isHidden": false
}
```

## Instructions

Use this operation to create a nested folder under an existing mail folder. Provide the parent folder ID in the path and the display name for the new child folder in the request body. The response returns the newly created child folder with a 201 status code. This is useful for building folder hierarchies to organize mail.
