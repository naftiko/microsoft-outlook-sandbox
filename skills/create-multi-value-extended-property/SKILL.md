# Create Multi-Value Extended Property

Create a multi-value MAPI extended property on a message.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: POST
- **Path**: `/me/messages/{message-id}/multiValueExtendedProperties`
- **Operation ID**: `createMultiValueExtendedProperty`
- **Tag**: ExtendedProperties
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/{message-id}/multiValueExtendedProperties`

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
| id | string | The property identifier in the format: TypeArray {GUID} Name PropertyName |
| value | array | An array of property values |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/AAMkAGVmMDEzMTM4/multiValueExtendedProperties" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "id": "StringArray {66f5a359-4659-4830-9070-00047ec6ac6e} Name Tags",
    "value": [
      "work",
      "important"
    ]
  }'
```

## Example Response

```json
{
  "id": "StringArray {66f5a359-4659-4830-9070-00047ec6ac6e} Name Tags",
  "value": [
    "work",
    "important"
  ]
}
```

## Instructions

Use this operation to create a multi-value MAPI extended property on a message. Multi-value extended properties allow you to store arrays of values, such as tags or multiple identifiers. The property identifier follows the format "TypeArray {GUID} Name PropertyName". Returns 201 on success.
