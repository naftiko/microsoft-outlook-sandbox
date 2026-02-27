# Get Mail Search Folder

Retrieve the properties and relationships of a specific mail search folder by its ID.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/me/mailFolders/{mailFolder-id}/childFolders/{childFolder-id}`
- **Operation ID**: `getMailSearchFolder`
- **Tag**: MailSearchFolders
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/{mailFolder-id}/childFolders/{childFolder-id}`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Mail.Read`
- `Mail.ReadWrite`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `mailFolder-id` | string | Yes | The unique identifier of the parent mail folder |
| `childFolder-id` | string | Yes | The unique identifier of the search folder |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/AAMkAGI1AAAEJAAA=/childFolders/AAMkAGI1SEARCH01=" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "id": "AAMkAGI1SEARCH01=",
  "displayName": "Unread Priority Mail",
  "parentFolderId": "AAMkAGI1AAAAAA=",
  "childFolderCount": 2,
  "totalItemCount": 147,
  "unreadItemCount": 12,
  "isHidden": false,
  "@odata.type": "#microsoft.graph.mailSearchFolder",
  "filterQuery": "isRead eq false and importance eq 'high'",
  "sourceFolderIds": ["AAMkAGI1AAAEJAAA="],
  "includeNestedFolders": true,
  "isSupported": true
}
```

## Instructions

Use this operation to retrieve the details of a specific mail search folder, including its filter query, source folder IDs, and whether nested folders are included. Provide both the parent folder ID and the search folder ID in the path. The response includes search-folder-specific properties like filterQuery, sourceFolderIds, includeNestedFolders, and isSupported.
