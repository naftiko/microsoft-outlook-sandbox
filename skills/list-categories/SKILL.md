# List All Categories

List all Outlook categories defined for the user's mailbox.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/me/outlook/masterCategories`
- **Operation ID**: `listCategories`
- **Tag**: Categories
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/outlook/masterCategories`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `MailboxSettings.ReadWrite`

## Parameters

No required parameters.

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/outlook/masterCategories" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "value": [
    {
      "id": "afc97c36-af15-4e96-bf52-e228c84d4567",
      "displayName": "Blue Category",
      "color": "preset7"
    }
  ]
}
```

## Instructions

Use this operation to retrieve all master categories configured in the user's mailbox. Categories can be applied to messages, events, and other Outlook items to help organize them. The response includes each category's display name, color preset, and unique identifier.
