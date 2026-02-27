# Delete Subscription

Delete a webhook subscription to stop receiving change notifications.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: DELETE
- **Path**: `/subscriptions/{subscription-id}`
- **Operation ID**: `deleteSubscription`
- **Tag**: Subscriptions
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/subscriptions/{subscription-id}`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Mail.Read`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| subscription-id | path | string | Yes | The unique identifier of the subscription to delete |

## Example Request

```bash
curl -X DELETE "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/subscriptions/7f105c7d-2dc5-4530-97cd-4e7ae6534c07" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
```

## Instructions

Use this operation to delete a webhook subscription and stop receiving change notifications. Provide the subscription identifier in the URL path. Returns 204 No Content on successful deletion. After deletion, no further notifications will be sent to the notification URL.
