# List Child Folders

List the child folders of a specific mail folder, returning the immediate subfolders within it.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/me/mailFolders/{mailFolder-id}/childFolders`
- **Operation ID**: `listChildFolders`
- **Tag**: MailFolders
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/{mailFolder-id}/childFolders`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Mail.Read`
- `Mail.ReadWrite`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `mailFolder-id` | string | Yes | The unique identifier of the parent mail folder |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/AAMkAGI1AAAEJAAA=/childFolders" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "value": [
    {
      "id": "AAMkAGI1AAAEJAAA=",
      "displayName": "Inbox",
      "parentFolderId": "AAMkAGI1AAAAAA=",
      "childFolderCount": 2,
      "totalItemCount": 147,
      "unreadItemCount": 12,
      "isHidden": false
    }
  ]
}
```

## Instructions

Use this operation to retrieve the immediate child folders within a specific mail folder. This is useful for navigating the folder hierarchy and discovering subfolders. The response returns a collection of folder objects representing the direct children of the specified parent folder.
