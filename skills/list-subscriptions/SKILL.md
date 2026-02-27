# List Subscriptions

List all active webhook subscriptions for the user.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/subscriptions`
- **Operation ID**: `listSubscriptions`
- **Tag**: Subscriptions
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/subscriptions`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Mail.Read`

## Parameters

No required parameters.

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/subscriptions" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "value": [
    {
      "id": "7f105c7d-2dc5-4530-97cd-4e7ae6534c07",
      "resource": "me/mailFolders('Inbox')/messages",
      "changeType": "created,updated",
      "notificationUrl": "https://webhook.contoso.com/api/notifications",
      "expirationDateTime": "2024-02-15T11:00:00Z"
    }
  ]
}
```

## Instructions

Use this operation to retrieve all active webhook subscriptions. Subscriptions allow your application to receive notifications when changes occur in the user's mailbox, such as new messages or updates. The response includes each subscription's identifier, resource, change types, notification URL, and expiration date.
