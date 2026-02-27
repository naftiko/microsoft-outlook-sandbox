# List Inbox Rules

List all message rules defined for the user's inbox.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/me/mailFolders/inbox/messageRules`
- **Operation ID**: `listMessageRules`
- **Tag**: InboxRules
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/inbox/messageRules`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `MailboxSettings.ReadWrite`

## Parameters

No required parameters.

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/inbox/messageRules" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "value": [
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
  ]
}
```

## Instructions

Use this operation to retrieve all message rules configured for the user's inbox. Rules automatically process incoming messages based on conditions and actions, such as forwarding, moving, or categorizing messages. Each rule includes its display name, sequence order, enabled status, conditions, and actions.
