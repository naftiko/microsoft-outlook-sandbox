# Get Mail Folder Delta

Get incremental changes to mail folders using delta synchronization.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/me/mailFolders/delta`
- **Operation ID**: `getMailFolderDelta`
- **Tag**: Synchronization
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/delta`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Mail.Read`
- `Mail.ReadWrite`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| $deltatoken | query | string | No | Token from a previous delta response to get changes since that point |
| $skiptoken | query | string | No | Token for pagination to get the next page of results |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/delta" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "value": [
    {
      "id": "AAMkAGVmMDEzMTM4LTZmYWUtNDdkNC1hMDZiLTU1OGY5OTZhYmY4OAAuAAAAAAAiQ8W967B7TKBjgx9rVEURAQAiIsqMbYjsT5e-T7KzowPTAAAAAAEMAAA=",
      "displayName": "Inbox",
      "parentFolderId": "AAMkAGVmMDEzMTM4LTZmYWUtNDdkNC1hMDZiLTU1OGY5OTZhYmY4OAAuAAAAAAAiQ8W967B7TKBjgx9rVEURAQAiIsqMbYjsT5e-T7KzowPTAAAAAAEIAAA=",
      "childFolderCount": 0,
      "unreadItemCount": 5,
      "totalItemCount": 42
    }
  ],
  "@odata.deltaLink": "https://graph.microsoft.com/v1.0/me/mailFolders/delta?$deltatoken=abc123"
}
```

## Instructions

Use this operation to perform incremental synchronization of mail folders. On the first call, omit the $deltatoken to get the full set of folders. The response includes an @odata.deltaLink with a delta token. On subsequent calls, use the $deltatoken from the previous response to get only the folders that have changed since the last sync. Use $skiptoken for pagination when the result set spans multiple pages.
