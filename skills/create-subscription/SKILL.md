# Create Subscription

Subscribe to change notifications for mail resources via webhooks.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: POST
- **Path**: `/subscriptions`
- **Operation ID**: `createSubscription`
- **Tag**: Subscriptions
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/subscriptions`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Mail.Read`

## Request Body

| Field | Type | Description |
|-------|------|-------------|
| changeType | string | The type of changes to subscribe to (e.g., created, updated, deleted) |
| notificationUrl | string | The URL to receive webhook notifications |
| resource | string | The resource to monitor (e.g., me/mailFolders('Inbox')/messages) |
| expirationDateTime | string | The expiration date and time of the subscription (ISO 8601) |
| clientState | string | A secret value for validating notification authenticity |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/subscriptions" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "changeType": "created",
    "notificationUrl": "https://webhook.contoso.com/api/notifications",
    "resource": "me/mailFolders('\''Inbox'\'')/messages",
    "expirationDateTime": "2024-02-15T11:00:00Z",
    "clientState": "secretClientValue"
  }'
```

## Example Response

```json
{
  "id": "7f105c7d-2dc5-4530-97cd-4e7ae6534c07",
  "resource": "me/mailFolders('Inbox')/messages",
  "changeType": "created",
  "notificationUrl": "https://webhook.contoso.com/api/notifications",
  "expirationDateTime": "2024-02-15T11:00:00Z",
  "clientState": "secretClientValue"
}
```

## Instructions

Use this operation to create a new webhook subscription for mail change notifications. Specify the resource to monitor, the types of changes to track, and the URL to receive notifications. The notificationUrl must be a publicly accessible HTTPS endpoint. Returns 201 on success. Subscriptions expire and must be renewed before the expirationDateTime.
