# Renew Subscription

Renew a webhook subscription by extending its expiration date.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: PATCH
- **Path**: `/subscriptions/{subscription-id}`
- **Operation ID**: `renewSubscription`
- **Tag**: Subscriptions
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/subscriptions/{subscription-id}`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Mail.Read`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| subscription-id | path | string | Yes | The unique identifier of the subscription |

## Request Body

| Field | Type | Description |
|-------|------|-------------|
| expirationDateTime | string | The new expiration date and time (ISO 8601) |

## Example Request

```bash
curl -X PATCH "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/subscriptions/7f105c7d-2dc5-4530-97cd-4e7ae6534c07" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "expirationDateTime": "2024-03-15T11:00:00Z"
  }'
```

## Example Response

```json
{
  "id": "7f105c7d-2dc5-4530-97cd-4e7ae6534c07",
  "resource": "me/mailFolders('Inbox')/messages",
  "changeType": "created,updated",
  "notificationUrl": "https://webhook.contoso.com/api/notifications",
  "expirationDateTime": "2024-03-15T11:00:00Z"
}
```

## Instructions

Use this operation to renew a webhook subscription before it expires. Provide the subscription identifier in the URL path and the new expiration date in the request body. Subscriptions must be renewed periodically to continue receiving notifications.
