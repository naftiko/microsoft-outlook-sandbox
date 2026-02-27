# Forward Message

Forwards an existing message to one or more recipients with an optional comment.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: POST
- **Path**: `/me/messages/{message-id}/forward`
- **Operation ID**: `forwardMessage`
- **Tag**: Messages
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/{message-id}/forward`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Mail.Send`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `message-id` | string | Yes | The unique identifier of the message to forward |

## Request Body

| Property | Type | Description |
|----------|------|-------------|
| `toRecipients` | array | Array of recipient objects with `emailAddress` containing `name` and `address` |
| `comment` | string | Optional comment to include with the forwarded message |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/AAMkAGI1AAAGB1rUAAA=/forward" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "toRecipients": [
      {
        "emailAddress": {
          "name": "Bob",
          "address": "bob@contoso.com"
        }
      }
    ],
    "comment": "FYI"
  }'
```

## Example Response

```
HTTP/1.1 202 Accepted
```

## Instructions

Use this operation to forward an existing message to one or more new recipients. The `toRecipients` array specifies who will receive the forwarded message, and the optional `comment` field adds text above the forwarded content. A successful forward returns a 202 Accepted response with no body, indicating the message has been queued for delivery. Any attachments on the original message are automatically included in the forwarded message.
