# Create Focused Inbox Override

Create a new Focused Inbox classification override for a specific sender.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: POST
- **Path**: `/me/inferenceClassification/overrides`
- **Operation ID**: `createInferenceClassificationOverride`
- **Tag**: FocusedInbox
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/inferenceClassification/overrides`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Mail.ReadWrite`

## Request Body

| Field | Type | Description |
|-------|------|-------------|
| classifyAs | string | The classification: "focused" or "other" |
| senderEmailAddress | object | The sender email address to override classification for |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/inferenceClassification/overrides" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "classifyAs": "focused",
    "senderEmailAddress": {
      "address": "important@contoso.com"
    }
  }'
```

## Example Response

```json
{
  "id": "abc123",
  "classifyAs": "focused",
  "senderEmailAddress": {
    "name": "Important Sender",
    "address": "important@contoso.com"
  }
}
```

## Instructions

Use this operation to create a new Focused Inbox override that always classifies messages from a specific sender as "focused" or "other". Provide the sender's email address and the desired classification. Returns 201 on success.
