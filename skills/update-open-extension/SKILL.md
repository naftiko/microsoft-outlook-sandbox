# Update Open Extension

Update an existing open type extension on a message.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: PATCH
- **Path**: `/me/messages/{message-id}/extensions/{extension-id}`
- **Operation ID**: `updateOpenExtension`
- **Tag**: Extensions
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/{message-id}/extensions/{extension-id}`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Mail.ReadWrite`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| message-id | path | string | Yes | The unique identifier of the message |
| extension-id | path | string | Yes | The unique identifier of the extension |

## Request Body

| Field | Type | Description |
|-------|------|-------------|
| @odata.type | string | Must be "#microsoft.graph.openTypeExtension" |
| extensionName | string | The extension name |
| (custom fields) | any | Custom properties to update |

## Example Request

```bash
curl -X PATCH "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/AAMkAGVmMDEzMTM4/extensions/Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "@odata.type": "#microsoft.graph.openTypeExtension",
    "extensionName": "Com.Contoso.Referral",
    "companyName": "Contoso",
    "dealValue": 75000
  }'
```

## Example Response

```json
{
  "@odata.type": "#microsoft.graph.openTypeExtension",
  "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
  "extensionName": "Com.Contoso.Referral",
  "companyName": "Contoso",
  "dealValue": 75000
}
```

## Instructions

Use this operation to update an existing open type extension on a message. Provide both the message identifier and the extension identifier in the URL path. Include the updated custom properties in the request body. Note that the entire extension is replaced with the provided data, so include all properties you want to retain.
