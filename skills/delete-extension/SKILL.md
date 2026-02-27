# Delete Extension

Delete an open type extension from a message.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: DELETE
- **Path**: `/me/messages/{message-id}/extensions/{extension-id}`
- **Operation ID**: `deleteExtension`
- **Tag**: Extensions
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/{message-id}/extensions/{extension-id}`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Mail.ReadWrite`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| message-id | path | string | Yes | The unique identifier of the message |
| extension-id | path | string | Yes | The unique identifier of the extension to delete |

## Example Request

```bash
curl -X DELETE "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/AAMkAGVmMDEzMTM4/extensions/Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
```

## Instructions

Use this operation to permanently delete an open type extension from a message. Provide both the message identifier and the extension identifier in the URL path. Returns 204 No Content on successful deletion. This removes the custom data stored in the extension.
