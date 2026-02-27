# Get Focused Inbox Override

Retrieve a specific Focused Inbox classification override by its identifier.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/me/inferenceClassification/overrides/{override-id}`
- **Operation ID**: `getInferenceClassificationOverride`
- **Tag**: FocusedInbox
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/inferenceClassification/overrides/{override-id}`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Mail.ReadWrite`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| override-id | path | string | Yes | The unique identifier of the override |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/inferenceClassification/overrides/abc123" \
  -H "Authorization: Bearer {access-token}"
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

Use this operation to retrieve the details of a specific Focused Inbox override by providing its unique identifier in the URL path. The response includes the override's classification setting and the sender email address it applies to.
