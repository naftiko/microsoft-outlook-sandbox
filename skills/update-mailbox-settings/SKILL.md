# Update Mailbox Settings

Update the user's mailbox settings such as automatic replies, locale, time zone, or working hours.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: PATCH
- **Path**: `/me/mailboxSettings`
- **Operation ID**: `updateMailboxSettings`
- **Tag**: MailboxSettings
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailboxSettings`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `MailboxSettings.ReadWrite`

## Request Body

| Field | Type | Description |
|-------|------|-------------|
| automaticRepliesSetting | object | Automatic reply (out of office) configuration |
| language | object | Language and locale preferences |
| timeZone | string | The user's time zone |
| workingHours | object | Working hours configuration |

## Example Request

```bash
curl -X PATCH "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailboxSettings" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "automaticRepliesSetting": {
      "status": "scheduled",
      "externalAudience": "contactsOnly",
      "internalReplyMessage": "I am out of office until Monday."
    },
    "timeZone": "Eastern Standard Time"
  }'
```

## Example Response

```json
{
  "automaticRepliesSetting": {
    "status": "scheduled",
    "externalAudience": "contactsOnly",
    "internalReplyMessage": "I am out of office until Monday."
  },
  "language": {
    "locale": "en-US",
    "displayName": "English (United States)"
  },
  "timeZone": "Eastern Standard Time",
  "workingHours": {
    "daysOfWeek": [
      "monday",
      "tuesday",
      "wednesday",
      "thursday",
      "friday"
    ],
    "startTime": "08:00:00",
    "endTime": "17:00:00"
  }
}
```

## Instructions

Use this operation to update the user's mailbox settings. You can configure automatic replies (out of office messages), change language and locale preferences, update the time zone, or modify working hours. Only the provided fields will be updated.
