# Delete Attachment

Deletes a specific attachment from a message in the signed-in user's mailbox.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: DELETE
- **Path**: `/me/messages/{message-id}/attachments/{attachment-id}`
- **Operation ID**: `deleteAttachment`
- **Tag**: Attachments
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/{message-id}/attachments/{attachment-id}`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Mail.ReadWrite`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `message-id` | string | Yes | The unique identifier of the message |
| `attachment-id` | string | Yes | The unique identifier of the attachment to delete |

## Example Request

```bash
curl -X DELETE "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/AAMkAGI1AAAGB1rUAAA=/attachments/AAMkAGI1AAABEgAQAA==" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```
HTTP/1.1 204 No Content
```

## Instructions

Use this operation to remove a specific attachment from a message. This is typically used on draft messages when you need to remove an attachment before sending. A successful deletion returns a 204 No Content response with no body. You need both the message ID and the attachment ID, which can be obtained from the list attachments operation. This operation permanently removes the attachment from the message.
