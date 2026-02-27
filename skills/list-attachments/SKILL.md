# List Attachments

Retrieves a collection of all attachments on a specific message in the signed-in user's mailbox.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/me/messages/{message-id}/attachments`
- **Operation ID**: `listAttachments`
- **Tag**: Attachments
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/{message-id}/attachments`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Mail.Read`
- `Mail.ReadWrite`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `message-id` | string | Yes | The unique identifier of the message |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/AAMkAGI1AAAGB1rUAAA=/attachments" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#me/messages('AAMkAGI1AAAGB1rUAAA=')/attachments",
  "value": [
    {
      "@odata.type": "#microsoft.graph.fileAttachment",
      "id": "AAMkAGI1AAABEgAQAA==",
      "name": "report.pdf",
      "contentType": "application/pdf",
      "size": 35684,
      "isInline": false,
      "lastModifiedDateTime": "2024-01-15T10:30:00Z",
      "contentBytes": "SGVsbG8gV29ybGQ="
    }
  ]
}
```

## Instructions

Use this operation to retrieve all attachments associated with a specific message. The response includes metadata for each attachment such as its name, content type, size, and for file attachments, the base64-encoded content in the `contentBytes` field. Check the `hasAttachments` property on a message before calling this operation to avoid unnecessary requests. The `@odata.type` field indicates the attachment type: `#microsoft.graph.fileAttachment` for file attachments, `#microsoft.graph.itemAttachment` for attached Outlook items, or `#microsoft.graph.referenceAttachment` for cloud file links.
