# Get Attachment Raw Content

Retrieves the raw binary content of a specific attachment on a message, returned as an application/octet-stream.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/me/messages/{message-id}/attachments/{attachment-id}/$value`
- **Operation ID**: `getAttachmentContent`
- **Tag**: MimeContent
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/{message-id}/attachments/{attachment-id}/$value`

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
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/AAMkAGI1AAAGB1rUAAA=/attachments/AAMkAGI1AAABEgAQAA==/$value" \
  -H "Authorization: Bearer {access-token}" \
  -o report.pdf
```

## Example Response

```
HTTP/1.1 200 OK
Content-Type: application/octet-stream

<raw binary content>
```

## Instructions

Use this operation to download the raw binary content of an attachment directly. Unlike the get attachment operation which returns metadata and base64-encoded content, this returns the raw bytes of the file as an application/octet-stream. This is more efficient for downloading large attachments since it avoids the overhead of base64 encoding. Use the `-o` flag with curl to save the output to a file. You need both the message ID and attachment ID, which can be obtained from the list attachments operation.
