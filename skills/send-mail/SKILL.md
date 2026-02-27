# Send Mail

Sends a new email message directly without first creating a draft. Supports both JSON and MIME format message content.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: POST
- **Path**: `/me/sendMail`
- **Operation ID**: `sendMail`
- **Tag**: Messages
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/sendMail`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Mail.Send`

## Request Body

| Property | Type | Description |
|----------|------|-------------|
| `message` | object | The message object containing subject, body, recipients, and other properties |
| `message.subject` | string | The subject of the message |
| `message.body` | object | The body with `contentType` (text/html) and `content` |
| `message.toRecipients` | array | Array of recipient objects with `emailAddress` containing `name` and `address` |
| `message.ccRecipients` | array | Array of CC recipient objects |
| `message.bccRecipients` | array | Array of BCC recipient objects |
| `message.importance` | string | The importance: low, normal, high |
| `saveToSentItems` | boolean | Whether to save the message in Sent Items (default: true) |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/sendMail" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "message": {
      "subject": "Hello",
      "body": {
        "contentType": "text",
        "content": "World"
      },
      "toRecipients": [
        {
          "emailAddress": {
            "address": "megan@contoso.com"
          }
        }
      ]
    },
    "saveToSentItems": true
  }'
```

## Example Response

```
HTTP/1.1 202 Accepted
```

## Instructions

Use this operation to compose and send a message in a single step without creating a draft first. This is the most efficient way to send a simple email. Set `saveToSentItems` to `false` if you do not want to keep a copy in the Sent Items folder. A successful send returns a 202 Accepted response with no body. For messages that require attachments or multiple edits before sending, use the create draft message workflow instead, which allows you to add attachments and make changes before sending.
