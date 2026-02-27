# Delete Focused Inbox Override

Delete a Focused Inbox classification override.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: DELETE
- **Path**: `/me/inferenceClassification/overrides/{override-id}`
- **Operation ID**: `deleteInferenceClassificationOverride`
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
| override-id | path | string | Yes | The unique identifier of the override to delete |

## Example Request

```bash
curl -X DELETE "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/inferenceClassification/overrides/abc123" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
```

## Instructions

Use this operation to permanently delete a Focused Inbox override. Provide the override identifier in the URL path. Returns 204 No Content on successful deletion. After deletion, messages from the sender will be classified automatically by the Focused Inbox algorithm.
