# Update Message

Updates the properties of an existing message in the signed-in user's mailbox, such as marking it as read or changing its importance.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: PATCH
- **Path**: `/me/messages/{message-id}`
- **Operation ID**: `updateMessage`
- **Tag**: Messages
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/{message-id}`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Mail.ReadWrite`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `message-id` | string | Yes | The unique identifier of the message |

## Request Body

Provide only the properties you want to update:

| Property | Type | Description |
|----------|------|-------------|
| `subject` | string | The subject of the message |
| `body` | object | The body with `contentType` and `content` |
| `isRead` | boolean | Whether the message has been read |
| `importance` | string | The importance: low, normal, high |
| `categories` | array | Array of category strings |

## Example Request

```bash
curl -X PATCH "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/AAMkAGI1AAAGB1rUAAA=" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "isRead": true,
    "importance": "high"
  }'
```

## Example Response

```json
{
  "id": "AAMkAGI1AAAGB1rUAAA=",
  "subject": "Quarterly Review Meeting",
  "bodyPreview": "Please join us for the quarterly review...",
  "body": {"contentType": "html", "content": "<html><body>Please join us for the quarterly review...</body></html>"},
  "importance": "high",
  "isRead": true,
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

Use this operation to modify properties of an existing message. Common uses include marking a message as read or unread, changing its importance level, updating categories, or modifying the content of a draft message. Only include the properties you want to change in the request body. The response returns the full updated message object. This operation works on both received messages and drafts.
