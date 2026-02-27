# Update Inbox Rule

Update the properties of an existing inbox message rule.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: PATCH
- **Path**: `/me/mailFolders/inbox/messageRules/{messageRule-id}`
- **Operation ID**: `updateMessageRule`
- **Tag**: InboxRules
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/inbox/messageRules/{messageRule-id}`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `MailboxSettings.ReadWrite`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| messageRule-id | path | string | Yes | The unique identifier of the message rule |

## Request Body

| Field | Type | Description |
|-------|------|-------------|
| displayName | string | The updated display name of the rule |
| sequence | integer | The updated execution order |
| isEnabled | boolean | Whether the rule is enabled |
| conditions | object | Updated conditions that trigger the rule |
| actions | object | Updated actions to perform |

## Example Request

```bash
curl -X PATCH "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailFolders/inbox/messageRules/AQAAAJ5dZqA=" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "displayName": "Forward from manager (updated)",
    "isEnabled": false
  }'
```

## Example Response

```json
{
  "id": "AQAAAJ5dZqA=",
  "displayName": "Forward from manager (updated)",
  "sequence": 1,
  "isEnabled": false,
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

Use this operation to update an existing inbox rule. Provide the rule identifier in the URL path and include only the properties to update in the request body. You can modify the rule's display name, sequence, enabled status, conditions, or actions.
