# List Focused Inbox Overrides

List all Focused Inbox classification overrides for the user.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/me/inferenceClassification/overrides`
- **Operation ID**: `listInferenceClassificationOverrides`
- **Tag**: FocusedInbox
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/inferenceClassification/overrides`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Mail.ReadWrite`

## Parameters

No required parameters.

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/inferenceClassification/overrides" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "value": [
    {
      "id": "abc123",
      "classifyAs": "focused",
      "senderEmailAddress": {
        "name": "Important Sender",
        "address": "important@contoso.com"
      }
    }
  ]
}
```

## Instructions

Use this operation to retrieve all Focused Inbox overrides configured by the user. Overrides allow users to always classify messages from specific senders as either "focused" or "other", overriding the automatic classification. The response includes each override's identifier, classification, and sender email address.
