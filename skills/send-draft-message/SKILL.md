# Send Draft Message

Sends an existing draft message that was previously created in the user's mailbox.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: POST
- **Path**: `/me/messages/{message-id}/send`
- **Operation ID**: `sendDraftMessage`
- **Tag**: Messages
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/{message-id}/send`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Mail.Send`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `message-id` | string | Yes | The unique identifier of the draft message to send |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/AAMkAGI1AAAGB1rUAAA=/send" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```
HTTP/1.1 202 Accepted
```

## Instructions

Use this operation to send a draft message that was previously created using the create message operation. The draft must have at least one recipient in the `toRecipients`, `ccRecipients`, or `bccRecipients` fields. A successful send returns a 202 Accepted response with no body, and the draft is moved from the Drafts folder to the Sent Items folder. This is the final step in the draft workflow: create a draft, optionally add attachments and update properties, then send it.
