# Get Extension

Retrieve a specific open type extension on a message.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/me/messages/{message-id}/extensions/{extension-id}`
- **Operation ID**: `getExtension`
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
| extension-id | path | string | Yes | The unique identifier of the extension |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/AAMkAGVmMDEzMTM4/extensions/Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "@odata.type": "#microsoft.graph.openTypeExtension",
  "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
  "extensionName": "Com.Contoso.Referral",
  "companyName": "Contoso",
  "dealValue": 50000
}
```

## Instructions

Use this operation to retrieve a specific open type extension on a message. Provide both the message identifier and the extension identifier in the URL path. The response includes the extension's type, name, and all custom properties stored in the extension.
