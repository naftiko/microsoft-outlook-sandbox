# Get Inbox Rule

Retrieve a specific inbox message rule by its identifier.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/me/mailFolders/inbox/messageRules/{messageRule-id}`
- **Operation ID**: `getMessageRule`
- **Tag**: InboxRules
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/inbox/messageRules/{messageRule-id}`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `MailboxSettings.ReadWrite`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| messageRule-id | path | string | Yes | The unique identifier of the message rule |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/inbox/messageRules/AQAAAJ5dZqA=" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "id": "AQAAAJ5dZqA=",
  "displayName": "Forward from manager",
  "sequence": 1,
  "isEnabled": true,
  "conditions": {
    "fromAddresses": [
      {
        "emailAddress": {
          "name": "Manager",
          "address": "manager@contoso.com"
        }
      }
    ]
  },
  "actions": {
    "forwardTo": [
      {
        "emailAddress": {
          "name": "Archive",
          "address": "archive@contoso.com"
        }
      }
    ],
    "stopProcessingRules": true
  }
}
```

## Instructions

Use this operation to retrieve the details of a specific inbox rule by providing its unique identifier in the URL path. The response includes the rule's display name, sequence, enabled status, conditions, and actions.
