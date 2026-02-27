# Reply to Message

Replies to the sender of a message by adding a comment and sending the reply. This only replies to the original sender, not to all recipients.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: POST
- **Path**: `/me/messages/{message-id}/reply`
- **Operation ID**: `replyToMessage`
- **Tag**: Messages
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/{message-id}/reply`

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
curl -X POST "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/AAMkAGI1AAAGB1rUAAA=/reply" \
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

Use this operation to send a reply to the sender of a specific message. The `comment` field contains the reply text that will be prepended to the original message body. The optional `message` object allows you to override properties of the reply, such as adding additional recipients. A successful reply returns a 202 Accepted response with no body, indicating the reply has been queued for delivery. Use the reply all operation instead if you need to respond to all recipients.
