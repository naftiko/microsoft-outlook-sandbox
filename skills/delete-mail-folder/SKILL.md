# Delete Mail Folder

Delete a specific mail folder and all of its contents permanently.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: DELETE
- **Path**: `/me/mailFolders/{mailFolder-id}`
- **Operation ID**: `deleteMailFolder`
- **Tag**: MailFolders
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/{mailFolder-id}`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Mail.ReadWrite`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `mailFolder-id` | string | Yes | The unique identifier of the mail folder to delete |

## Example Request

```bash
curl -X DELETE "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/AAMkAGI1AAAEJAAA=" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
204 No Content
```

## Instructions

Use this operation to permanently delete a mail folder and all of its contents. This action cannot be undone. A successful deletion returns a 204 No Content response with no body. Built-in folders like Inbox, Drafts, and Sent Items cannot be deleted.
