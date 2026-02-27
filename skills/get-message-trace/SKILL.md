# Get Message Trace

Trace a message through Exchange Online to see its delivery events and status.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/me/messages/{message-id}/messageTrace`
- **Operation ID**: `getMessageTrace`
- **Tag**: MessageTrace
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/{message-id}/messageTrace`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Mail.Read`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| message-id | path | string | Yes | The unique identifier of the message to trace |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/AAMkAGVmMDEzMTM4/messageTrace" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "messageId": "<msg001@contoso.com>",
  "receivedDateTime": "2024-01-15T10:30:00Z",
  "senderAddress": "alex@contoso.com",
  "recipientAddress": "megan@contoso.com",
  "subject": "Quarterly Review",
  "status": "Delivered",
  "events": [
    {
      "timestamp": "2024-01-15T10:29:55Z",
      "eventType": "Receive",
      "detail": "Message received by Exchange Online"
    },
    {
      "timestamp": "2024-01-15T10:30:00Z",
      "eventType": "Deliver",
      "detail": "Message delivered to mailbox"
    }
  ]
}
```

## Instructions

Use this operation to trace a message through Exchange Online and view its delivery events. Provide the message identifier in the URL path. The response includes the message's sender, recipient, subject, delivery status, and a chronological list of events showing how the message was processed through Exchange Online. This is useful for diagnosing delivery issues.
