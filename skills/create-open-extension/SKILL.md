# Create Open Extension

Create an open type extension on a message to store custom data.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: POST
- **Path**: `/me/messages/{message-id}/extensions`
- **Operation ID**: `createOpenExtension`
- **Tag**: Extensions
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/{message-id}/extensions`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Mail.ReadWrite`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| message-id | path | string | Yes | The unique identifier of the message |

## Request Body

| Field | Type | Description |
|-------|------|-------------|
| @odata.type | string | Must be "#microsoft.graph.openTypeExtension" |
| extensionName | string | A unique identifier for the extension |
| (custom fields) | any | Any custom properties to store |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/AAMkAGVmMDEzMTM4/extensions" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "@odata.type": "#microsoft.graph.openTypeExtension",
    "extensionName": "Com.Contoso.Referral",
    "companyName": "Contoso",
    "dealValue": 50000
  }'
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

Use this operation to create an open type extension on a message to store custom data. Extensions allow you to add custom properties to messages without requiring an external database. Provide a unique extension name and any custom properties in the request body. Returns 201 on success.
