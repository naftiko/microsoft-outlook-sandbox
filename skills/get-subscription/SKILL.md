# Get Subscription

Retrieve a specific webhook subscription by its identifier.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/subscriptions/{subscription-id}`
- **Operation ID**: `getSubscription`
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
| subscription-id | path | string | Yes | The unique identifier of the subscription |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/subscriptions/7f105c7d-2dc5-4530-97cd-4e7ae6534c07" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "id": "7f105c7d-2dc5-4530-97cd-4e7ae6534c07",
  "resource": "me/mailFolders('Inbox')/messages",
  "changeType": "created,updated",
  "notificationUrl": "https://webhook.contoso.com/api/notifications",
  "expirationDateTime": "2024-02-15T11:00:00Z"
}
```

## Instructions

Use this operation to retrieve the details of a specific webhook subscription by providing its unique identifier in the URL path. The response includes the subscription's resource, change types, notification URL, and expiration date. This is useful for checking subscription status and expiration.
