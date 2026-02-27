# List Mail Folders

List all mail folders in the authenticated user's mailbox, including built-in folders like Inbox, Drafts, and Sent Items, as well as custom folders.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/me/mailFolders`
- **Operation ID**: `listMailFolders`
- **Tag**: MailFolders
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Mail.Read`
- `Mail.ReadWrite`

## Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `$top` | integer | No | Maximum number of folders to return |
| `$skip` | integer | No | Number of folders to skip for pagination |
| `$filter` | string | No | OData filter expression to filter results |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders?$top=10" \
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

Use this operation to retrieve a list of all mail folders in the user's mailbox. This is useful for discovering available folders before performing operations like moving messages or listing folder contents. Use query parameters to paginate through large folder lists or filter for specific folders.
