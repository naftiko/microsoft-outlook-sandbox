# Get MailTips

Get MailTips for one or more recipients, such as automatic replies and mailbox full status.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: POST
- **Path**: `/me/getMailTips`
- **Operation ID**: `getMailTips`
- **Tag**: MailTips
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/getMailTips`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Mail.Read`

## Request Body

| Field | Type | Description |
|-------|------|-------------|
| emailAddresses | array | List of recipient email addresses to get MailTips for |
| mailTipsOptions | string | Types of MailTips to retrieve (e.g., automaticReplies, mailboxFullStatus, customMailTip, externalMemberCount, totalMemberCount, maxMessageSize, deliveryRestriction, moderationStatus) |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/getMailTips" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "emailAddresses": [
      "megan@contoso.com"
    ],
    "mailTipsOptions": "automaticReplies"
  }'
```

## Example Response

```json
{
  "value": [
    {
      "emailAddress": {
        "name": "Megan Bowen",
        "address": "megan@contoso.com"
      },
      "automaticReplies": {
        "message": "I am out of office."
      },
      "mailboxFull": false
    }
  ]
}
```

## Instructions

Use this operation to retrieve MailTips for one or more recipients before sending a message. MailTips provide useful information such as whether the recipient has automatic replies enabled, if their mailbox is full, or delivery restrictions. This helps users make informed decisions before sending messages.
