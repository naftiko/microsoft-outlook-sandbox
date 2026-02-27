# Get Mailbox Settings

Get the user's mailbox settings including automatic replies, locale, time zone, and working hours.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/me/mailboxSettings`
- **Operation ID**: `getMailboxSettings`
- **Tag**: MailboxSettings
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailboxSettings`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `MailboxSettings.Read`
- `MailboxSettings.ReadWrite`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| $select | query | string | No | Select specific settings to return (e.g., automaticRepliesSetting, language, timeZone, workingHours) |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/mailboxSettings" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "automaticRepliesSetting": {
    "status": "scheduled",
    "externalAudience": "contactsOnly",
    "internalReplyMessage": "I am out of office."
  },
  "language": {
    "locale": "en-US",
    "displayName": "English (United States)"
  },
  "timeZone": "Pacific Standard Time",
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

Use this operation to retrieve the user's mailbox settings. This includes automatic reply settings (out of office), language and locale preferences, time zone, and working hours configuration. Use the $select query parameter to retrieve only specific settings.
