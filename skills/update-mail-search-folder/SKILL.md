# Update Mail Search Folder

Update the properties of a specific mail search folder, such as its filter query or source folders.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: PATCH
- **Path**: `/me/mailFolders/{mailFolder-id}/childFolders/{childFolder-id}`
- **Operation ID**: `updateMailSearchFolder`
- **Tag**: MailSearchFolders
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/{mailFolder-id}/childFolders/{childFolder-id}`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Mail.ReadWrite`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `mailFolder-id` | string | Yes | The unique identifier of the parent mail folder |
| `childFolder-id` | string | Yes | The unique identifier of the search folder to update |

## Request Body

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `@odata.type` | string | Yes | Must be `#microsoft.graph.mailSearchFolder` |
| `displayName` | string | No | The updated display name of the search folder |
| `filterQuery` | string | No | The updated OData filter query |
| `sourceFolderIds` | array | No | Updated array of folder IDs to search within |
| `includeNestedFolders` | boolean | No | Whether to include nested folders in the search |

## Example Request

```bash
curl -X PATCH "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/AAMkAGI1AAAEJAAA=/childFolders/AAMkAGI1SEARCH01=" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "@odata.type": "#microsoft.graph.mailSearchFolder",
    "filterQuery": "isRead eq false and importance eq '\''normal'\''",
    "includeNestedFolders": false
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
  "filterQuery": "isRead eq false and importance eq 'normal'",
  "sourceFolderIds": ["AAMkAGI1AAAEJAAA="],
  "includeNestedFolders": false,
  "isSupported": true
}
```

## Instructions

Use this operation to modify the properties of an existing mail search folder. You can update the filter query to change which messages are matched, modify the source folder IDs to change the search scope, update the display name, or toggle nested folder inclusion. The @odata.type property must be included in the request body. The response returns the updated search folder object.
