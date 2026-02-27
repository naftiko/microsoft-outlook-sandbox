# Update Focused Inbox Override

Update an existing Focused Inbox classification override.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: PATCH
- **Path**: `/me/inferenceClassification/overrides/{override-id}`
- **Operation ID**: `updateInferenceClassificationOverride`
- **Tag**: FocusedInbox
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/inferenceClassification/overrides/{override-id}`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Mail.ReadWrite`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| override-id | path | string | Yes | The unique identifier of the override |

## Request Body

| Field | Type | Description |
|-------|------|-------------|
| classifyAs | string | The updated classification: "focused" or "other" |
| senderEmailAddress | object | The updated sender email address |

## Example Request

```bash
curl -X PATCH "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/inferenceClassification/overrides/abc123" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "classifyAs": "other"
  }'
```

## Example Response

```json
{
  "id": "abc123",
  "classifyAs": "other",
  "senderEmailAddress": {
    "name": "Important Sender",
    "address": "important@contoso.com"
  }
}
```

## Instructions

Use this operation to update an existing Focused Inbox override. Provide the override identifier in the URL path and include the properties to update in the request body. You can change the classification from "focused" to "other" or vice versa.
