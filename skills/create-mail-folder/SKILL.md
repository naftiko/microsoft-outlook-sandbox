# Create Mail Folder

Create a new mail folder in the authenticated user's mailbox as a top-level folder.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: POST
- **Path**: `/me/mailFolders`
- **Operation ID**: `createMailFolder`
- **Tag**: MailFolders
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Mail.ReadWrite`

## Request Body

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `displayName` | string | Yes | The display name of the new folder |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "displayName": "Project Alpha"
  }'
```

## Example Response

```json
{
  "id": "AAMkAGI1AAAEJAAA=",
  "displayName": "Project Alpha",
  "parentFolderId": "AAMkAGI1AAAAAA=",
  "childFolderCount": 0,
  "totalItemCount": 0,
  "unreadItemCount": 0,
  "isHidden": false
}
```

## Instructions

Use this operation to create a new top-level mail folder in the user's mailbox. Provide a display name for the folder in the request body. The response returns the newly created folder with a 201 status code. To create a nested folder, use the create child folder operation instead.
