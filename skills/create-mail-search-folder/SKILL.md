# Create Mail Search Folder

Create a new mail search folder that dynamically displays messages matching a specified filter query.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: POST
- **Path**: `/me/mailFolders/{mailFolder-id}/childFolders/mailSearchFolder`
- **Operation ID**: `createMailSearchFolder`
- **Tag**: MailSearchFolders
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/{mailFolder-id}/childFolders/mailSearchFolder`

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
| `@odata.type` | string | Yes | Must be `#microsoft.graph.mailSearchFolder` |
| `displayName` | string | Yes | The display name of the search folder |
| `filterQuery` | string | Yes | OData filter query to match messages |
| `sourceFolderIds` | array | Yes | Array of folder IDs to search within |
| `includeNestedFolders` | boolean | No | Whether to include nested folders in the search |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/AAMkAGI1AAAEJAAA=/childFolders/mailSearchFolder" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "@odata.type": "#microsoft.graph.mailSearchFolder",
    "displayName": "Unread Priority Mail",
    "filterQuery": "isRead eq false and importance eq '\''high'\''",
    "sourceFolderIds": ["AAMkAGI1AAAEJAAA="],
    "includeNestedFolders": true
  }'
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

Use this operation to create a virtual search folder that dynamically aggregates messages matching a filter query from one or more source folders. The search folder does not physically contain messages but provides a dynamic view. Specify the OData filter query to define matching criteria, the source folder IDs to search within, and whether to include nested subfolders. The response returns the newly created search folder with a 201 status code.
