# Delete Mail Search Folder

Delete a specific mail search folder permanently.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: DELETE
- **Path**: `/me/mailFolders/{mailFolder-id}/childFolders/{childFolder-id}`
- **Operation ID**: `deleteMailSearchFolder`
- **Tag**: MailSearchFolders
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/{mailFolder-id}/childFolders/{childFolder-id}`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Mail.ReadWrite`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `mailFolder-id` | string | Yes | The unique identifier of the parent mail folder |
| `childFolder-id` | string | Yes | The unique identifier of the search folder to delete |

## Example Request

```bash
curl -X DELETE "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/AAMkAGI1AAAEJAAA=/childFolders/AAMkAGI1SEARCH01=" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
204 No Content
```

## Instructions

Use this operation to permanently delete a mail search folder. Since search folders are virtual and do not physically contain messages, deleting a search folder only removes the saved search definition and does not affect the actual messages. A successful deletion returns a 204 No Content response with no body. Provide both the parent folder ID and the search folder ID in the path.
