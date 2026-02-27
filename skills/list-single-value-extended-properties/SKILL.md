# List Single-Value Extended Properties

List single-value MAPI extended properties on a message.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/me/messages/{message-id}/singleValueExtendedProperties`
- **Operation ID**: `listSingleValueExtendedProperties`
- **Tag**: ExtendedProperties
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/{message-id}/singleValueExtendedProperties`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Mail.ReadWrite`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| message-id | path | string | Yes | The unique identifier of the message |
| $filter | query | string | No | Filter to retrieve specific extended properties |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages/AAMkAGVmMDEzMTM4/singleValueExtendedProperties" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "value": [
    {
      "id": "String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color",
      "value": "Green"
    }
  ]
}
```

## Instructions

Use this operation to retrieve single-value MAPI extended properties on a message. Extended properties provide access to MAPI properties that are not otherwise exposed through the Microsoft Graph API. Provide the message identifier in the URL path. Use the $filter query parameter to retrieve specific properties by their identifier.
