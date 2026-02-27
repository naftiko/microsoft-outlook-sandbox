# Create Inbox Rule

Create a new message rule for the user's inbox to automatically process incoming messages.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: POST
- **Path**: `/me/mailFolders/inbox/messageRules`
- **Operation ID**: `createMessageRule`
- **Tag**: InboxRules
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/inbox/messageRules`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `MailboxSettings.ReadWrite`

## Request Body

| Field | Type | Description |
|-------|------|-------------|
| displayName | string | The display name of the rule |
| sequence | integer | The order in which the rule is executed |
| isEnabled | boolean | Whether the rule is enabled |
| conditions | object | Conditions that trigger the rule |
| actions | object | Actions to perform when conditions are met |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/inbox/messageRules" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
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
  }'
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

Use this operation to create a new inbox rule that automatically processes messages matching specified conditions. Define conditions (such as sender address, subject keywords) and actions (such as forward, move, categorize). Returns 201 on success.
