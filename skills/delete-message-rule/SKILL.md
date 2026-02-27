# Delete Inbox Rule

Delete an inbox message rule from the user's mailbox.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: DELETE
- **Path**: `/me/mailFolders/inbox/messageRules/{messageRule-id}`
- **Operation ID**: `deleteMessageRule`
- **Tag**: InboxRules
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/inbox/messageRules/{messageRule-id}`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `MailboxSettings.ReadWrite`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| messageRule-id | path | string | Yes | The unique identifier of the message rule to delete |

## Example Request

```bash
curl -X DELETE "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/inbox/messageRules/AQAAAJ5dZqA=" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
```

## Instructions

Use this operation to permanently delete an inbox rule from the user's mailbox. Provide the rule identifier in the URL path. Returns 204 No Content on successful deletion. This action cannot be undone.
