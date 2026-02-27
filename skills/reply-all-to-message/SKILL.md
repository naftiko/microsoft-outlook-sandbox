# Reply All to Message

Replies to all recipients of a message by adding a comment and sending the reply to the sender and all other recipients.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: POST
- **Path**: `/me/messages/{message-id}/replyAll`
- **Operation ID**: `replyAllToMessage`
- **Tag**: Messages
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/{message-id}/replyAll`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Mail.Send`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `message-id` | string | Yes | The unique identifier of the message to reply to |

## Request Body

| Property | Type | Description |
|----------|------|-------------|
| `comment` | string | The reply comment to include in the response |
| `message` | object | Optional message properties to override in the reply |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/AAMkAGI1AAAGB1rUAAA=/replyAll" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "comment": "Thanks, I'\''ll review.",
    "message": {}
  }'
```

## Example Response

```
HTTP/1.1 202 Accepted
```

## Instructions

Use this operation to send a reply to all recipients of a specific message, including the sender, all To recipients, and all CC recipients. The `comment` field contains the reply text that will be prepended to the original message body. The optional `message` object allows you to override properties such as adding or removing recipients. A successful reply returns a 202 Accepted response with no body. Use the single reply operation instead if you only need to respond to the sender.
