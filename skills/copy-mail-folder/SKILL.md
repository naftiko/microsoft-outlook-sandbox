# Copy Mail Folder

Copy a mail folder and its contents to a specified destination folder.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: POST
- **Path**: `/me/mailFolders/{mailFolder-id}/copy`
- **Operation ID**: `copyMailFolder`
- **Tag**: MailFolders
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/{mailFolder-id}/copy`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Mail.ReadWrite`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `mailFolder-id` | string | Yes | The unique identifier of the mail folder to copy |

## Request Body

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `destinationId` | string | Yes | The ID of the destination folder to copy into |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/AAMkAGI1AAAEJAAA=/copy" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "destinationId": "AAMkAGI1DEST="
  }'
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

Use this operation to copy a mail folder and its contents to another location in the mailbox. Provide the source folder ID in the path and the destination folder ID in the request body. The response returns the newly created copy of the folder. The original folder remains unchanged.
