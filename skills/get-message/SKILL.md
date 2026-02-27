# Get Message

Retrieves a specific message from the signed-in user's mailbox by its unique identifier.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/me/messages/{message-id}`
- **Operation ID**: `getMessage`
- **Tag**: Messages
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/{message-id}`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Mail.Read`
- `Mail.ReadWrite`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `message-id` | string | Yes | The unique identifier of the message |

## Query Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `$select` | string | Comma-separated list of properties to include |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/AAMkAGI1AAAGB1rUAAA=?$select=subject,body,from,toRecipients" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "id": "AAMkAGI1AAAGB1rUAAA=",
  "subject": "Quarterly Review Meeting",
  "bodyPreview": "Please join us for the quarterly review...",
  "body": {"contentType": "html", "content": "<html><body>Please join us for the quarterly review...</body></html>"},
  "importance": "normal",
  "isRead": false,
  "isDraft": false,
  "hasAttachments": false,
  "from": {"emailAddress": {"name": "Alex Wilber", "address": "alex@contoso.com"}},
  "toRecipients": [{"emailAddress": {"name": "Megan Bowen", "address": "megan@contoso.com"}}],
  "createdDateTime": "2024-01-15T10:30:00Z",
  "receivedDateTime": "2024-01-15T10:30:00Z",
  "parentFolderId": "AAMkAGI1AAAEJAAA="
}
```

## Instructions

Use this operation to retrieve the full details of a specific message when you have its ID. Use `$select` to limit the properties returned if you only need specific fields, which improves performance. This is commonly used after listing messages to get the full body content of a particular message, or when processing a message ID received from a notification or other operation.
