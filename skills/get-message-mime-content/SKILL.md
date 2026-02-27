# Get Message MIME Content

Retrieves the MIME representation of a message, which includes all headers, body, and attachments in a single stream.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/me/messages/{message-id}/$value`
- **Operation ID**: `getMessageMimeContent`
- **Tag**: MimeContent
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/{message-id}/$value`

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
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/AAMkAGI1AAAGB1rUAAA=/$value" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```
MIME-Version: 1.0
From: Alex Wilber <alex@contoso.com>
To: Megan Bowen <megan@contoso.com>
Subject: Quarterly Review Meeting
Content-Type: text/html; charset="UTF-8"
Date: Mon, 15 Jan 2024 10:30:00 +0000

<html><body>Please join us for the quarterly review...</body></html>
```

## Instructions

Use this operation to retrieve the full MIME content of a message as a text/plain stream. The MIME format includes all message headers, the body content, and any inline or file attachments encoded in the standard email format. This is useful for archiving messages, forwarding via external systems, or when you need the raw email content with all headers intact. The response is a raw MIME stream, not JSON.
