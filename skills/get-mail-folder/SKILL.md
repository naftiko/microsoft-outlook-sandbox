# Get Mail Folder

Retrieve the properties and relationships of a specific mail folder by its ID.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/me/mailFolders/{mailFolder-id}`
- **Operation ID**: `getMailFolder`
- **Tag**: MailFolders
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/{mailFolder-id}`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Mail.Read`
- `Mail.ReadWrite`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `mailFolder-id` | string | Yes | The unique identifier of the mail folder |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/AAMkAGI1AAAEJAAA=" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "id": "AAMkAGI1AAAEJAAA=",
  "displayName": "Inbox",
  "parentFolderId": "AAMkAGI1AAAAAA=",
  "childFolderCount": 2,
  "totalItemCount": 147,
  "unreadItemCount": 12,
  "isHidden": false
}
```

## Instructions

Use this operation to retrieve details about a specific mail folder when you have its ID. This returns properties such as the display name, parent folder, child folder count, and item counts. You can also use well-known folder names like "inbox", "drafts", "sentitems", or "deleteditems" in place of the folder ID.
