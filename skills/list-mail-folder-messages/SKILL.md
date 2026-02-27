# List Mail Folder Messages

List all messages contained in a specific mail folder.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/me/mailFolders/{mailFolder-id}/messages`
- **Operation ID**: `listMailFolderMessages`
- **Tag**: MailFolders
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/{mailFolder-id}/messages`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Mail.Read`
- `Mail.ReadWrite`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `mailFolder-id` | string | Yes | The unique identifier of the mail folder |

## Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `$top` | integer | No | Maximum number of messages to return |
| `$skip` | integer | No | Number of messages to skip for pagination |
| `$select` | string | No | Comma-separated list of properties to include |
| `$filter` | string | No | OData filter expression to filter results |
| `$search` | string | No | Search expression to find matching messages |
| `$orderby` | string | No | Property and direction to sort results by |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/AAMkAGI1AAAEJAAA=/messages?$top=10&$select=subject,from,receivedDateTime" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "value": [
    {
      "id": "AAMkAGI1MSG001=",
      "subject": "Project Update",
      "from": {
        "emailAddress": {
          "name": "Jane Doe",
          "address": "jane@example.com"
        }
      },
      "receivedDateTime": "2025-01-15T10:30:00Z",
      "isRead": false
    }
  ]
}
```

## Instructions

Use this operation to retrieve messages from a specific mail folder. This is useful for reading the contents of any folder including Inbox, Sent Items, or custom folders. Use query parameters to paginate, filter, search, sort, and select specific properties to optimize the response payload. Well-known folder names like "inbox" or "drafts" can be used in place of the folder ID.
