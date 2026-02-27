# Delete Message

Deletes a message from the signed-in user's mailbox, moving it to the Deleted Items folder.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: DELETE
- **Path**: `/me/messages/{message-id}`
- **Operation ID**: `deleteMessage`
- **Tag**: Messages
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/{message-id}`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Mail.ReadWrite`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `message-id` | string | Yes | The unique identifier of the message to delete |

## Example Request

```bash
curl -X DELETE "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/AAMkAGI1AAAGB1rUAAA=" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```
HTTP/1.1 204 No Content
```

## Instructions

Use this operation to delete a specific message from the user's mailbox. The message is moved to the Deleted Items folder rather than being permanently deleted. A successful deletion returns a 204 No Content response with no body. You must have the message ID, which can be obtained from the list messages or get message operations. Use this when a user wants to remove unwanted or processed messages from their mailbox.
