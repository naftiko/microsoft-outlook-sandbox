# Get Attachment

Retrieves a specific attachment from a message by its unique identifier, including metadata and base64-encoded content.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/me/messages/{message-id}/attachments/{attachment-id}`
- **Operation ID**: `getAttachment`
- **Tag**: Attachments
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/{message-id}/attachments/{attachment-id}`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Mail.Read`
- `Mail.ReadWrite`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `message-id` | string | Yes | The unique identifier of the message |
| `attachment-id` | string | Yes | The unique identifier of the attachment |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/AAMkAGI1AAAGB1rUAAA=/attachments/AAMkAGI1AAABEgAQAA==" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
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
```

## Instructions

Use this operation to retrieve the full details of a specific attachment when you have both the message ID and attachment ID. The response includes the attachment metadata and, for file attachments, the base64-encoded content in the `contentBytes` field. The attachment ID can be obtained from the list attachments operation. For downloading just the raw binary content without base64 encoding, use the get attachment content operation instead, which is more efficient for large files.
