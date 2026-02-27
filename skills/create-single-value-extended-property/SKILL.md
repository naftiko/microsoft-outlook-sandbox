# Create Single-Value Extended Property

Create a single-value MAPI extended property on a message.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: POST
- **Path**: `/me/messages/{message-id}/singleValueExtendedProperties`
- **Operation ID**: `createSingleValueExtendedProperty`
- **Tag**: ExtendedProperties
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/{message-id}/singleValueExtendedProperties`

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
| id | string | The property identifier in the format: Type {GUID} Name PropertyName |
| value | string | The property value |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/AAMkAGVmMDEzMTM4/singleValueExtendedProperties" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "id": "String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color",
    "value": "Green"
  }'
```

## Example Response

```json
{
  "id": "String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color",
  "value": "Green"
}
```

## Instructions

Use this operation to create a single-value MAPI extended property on a message. Extended properties allow you to store custom MAPI properties that are not otherwise available through the Microsoft Graph API. The property identifier follows the format "Type {GUID} Name PropertyName". Returns 201 on success.
