# Create Draft Message

Creates a new draft message in the signed-in user's mailbox. The draft can be updated and sent later using the send draft operation.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: POST
- **Path**: `/me/messages`
- **Operation ID**: `createMessage`
- **Tag**: Messages
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Mail.ReadWrite`

## Request Body

| Property | Type | Description |
|----------|------|-------------|
| `subject` | string | The subject of the message |
| `body` | object | The body of the message with `contentType` (text/html) and `content` |
| `toRecipients` | array | Array of recipient objects with `emailAddress` containing `name` and `address` |
| `ccRecipients` | array | Array of CC recipient objects |
| `bccRecipients` | array | Array of BCC recipient objects |
| `importance` | string | The importance of the message: low, normal, high |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "subject": "Quarterly Review Meeting",
    "body": {
      "contentType": "html",
      "content": "<html><body>Please join us for the quarterly review...</body></html>"
    },
    "toRecipients": [
      {
        "emailAddress": {
          "name": "Megan Bowen",
          "address": "megan@contoso.com"
        }
      }
    ],
    "importance": "normal"
  }'
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
  "isDraft": true,
  "hasAttachments": false,
  "from": {"emailAddress": {"name": "Alex Wilber", "address": "alex@contoso.com"}},
  "toRecipients": [{"emailAddress": {"name": "Megan Bowen", "address": "megan@contoso.com"}}],
  "createdDateTime": "2024-01-15T10:30:00Z",
  "receivedDateTime": "2024-01-15T10:30:00Z",
  "parentFolderId": "AAMkAGI1AAAEJAAA="
}
```

## Instructions

Use this operation to create a draft message that can be edited before sending. After creating the draft, you can add attachments using the create attachment operation and then send it using the send draft message operation. The response returns the created message with `isDraft` set to `true` and a status code of 201. This is the preferred workflow when you need to compose a message in multiple steps.
