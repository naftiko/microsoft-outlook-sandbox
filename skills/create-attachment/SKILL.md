# Create Attachment

Adds a new attachment to an existing message, typically a draft message, by providing the file content as a base64-encoded string.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: POST
- **Path**: `/me/messages/{message-id}/attachments`
- **Operation ID**: `createAttachment`
- **Tag**: Attachments
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/{message-id}/attachments`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Mail.ReadWrite`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `message-id` | string | Yes | The unique identifier of the message to attach to |

## Request Body

| Property | Type | Description |
|----------|------|-------------|
| `@odata.type` | string | The attachment type, e.g., `#microsoft.graph.fileAttachment` |
| `name` | string | The display name of the attachment |
| `contentBytes` | string | Base64-encoded content of the file |
| `contentType` | string | The MIME type of the attachment (optional) |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/AAMkAGI1AAAGB1rUAAA=/attachments" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "@odata.type": "#microsoft.graph.fileAttachment",
    "name": "report.pdf",
    "contentBytes": "SGVsbG8gV29ybGQ="
  }'
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

Use this operation to add a file attachment to a message, typically a draft message before sending. The file content must be base64-encoded in the `contentBytes` field. The `@odata.type` must be set to `#microsoft.graph.fileAttachment` for file attachments. A successful creation returns a 201 status code with the attachment object. This is commonly used in the draft workflow: create a draft, add attachments, then send. For attachments larger than 3 MB, use the upload session API instead.
