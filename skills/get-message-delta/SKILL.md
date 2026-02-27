# Get Message Delta

Get incremental changes to messages in a mail folder using delta synchronization.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/me/mailFolders/{mailFolder-id}/messages/delta`
- **Operation ID**: `getMessageDelta`
- **Tag**: Synchronization
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/{mailFolder-id}/messages/delta`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Mail.Read`
- `Mail.ReadWrite`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| mailFolder-id | path | string | Yes | The unique identifier of the mail folder |
| $deltatoken | query | string | No | Token from a previous delta response to get changes since that point |
| $skiptoken | query | string | No | Token for pagination to get the next page of results |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/inbox/messages/delta" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "value": [
    {
      "id": "AAMkAGVmMDEzMTM4LTZmYWUtNDdkNC1hMDZiLTU1OGY5OTZhYmY4OABGAAAAAAAiQ8W967B7TKBjgx9rVEURAQAiIsqMbYjsT5e-T7KzowPTAAAAAAEMAAAiIsqMbYjsT5e-T7KzowPTAAFzGhcnAAA=",
      "subject": "Quarterly Review",
      "from": {
        "emailAddress": {
          "name": "Alex Wilber",
          "address": "alex@contoso.com"
        }
      },
      "isRead": false,
      "receivedDateTime": "2024-01-15T10:30:00Z"
    }
  ],
  "@odata.deltaLink": "https://graph.microsoft.com/v1.0/me/mailFolders/inbox/messages/delta?$deltatoken=xyz789"
}
```

## Instructions

Use this operation to perform incremental synchronization of messages within a specific mail folder. On the first call, omit the $deltatoken to get the full set of messages. The response includes an @odata.deltaLink with a delta token. On subsequent calls, use the $deltatoken from the previous response to get only the messages that have changed since the last sync. Use $skiptoken for pagination when the result set spans multiple pages.
