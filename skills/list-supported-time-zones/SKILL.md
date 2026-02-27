# List Supported Time Zones

List all supported time zones for the user's mailbox.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/me/outlook/supportedTimeZones`
- **Operation ID**: `listSupportedTimeZones`
- **Tag**: LocaleAndTimeZone
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/outlook/supportedTimeZones`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `MailboxSettings.Read`

## Parameters

| Parameter | In | Type | Required | Description |
|-----------|-----|------|----------|-------------|
| TimeZoneStandard | query | string | No | The time zone standard to use: "windows" or "iana" |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/outlook/supportedTimeZones?TimeZoneStandard=windows" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "value": [
    {
      "alias": "Pacific Standard Time",
      "displayName": "(UTC-08:00) Pacific Time (US & Canada)"
    }
  ]
}
```

## Instructions

Use this operation to retrieve the list of time zones supported for the user's mailbox configuration. Optionally specify the TimeZoneStandard query parameter to get time zones in either "windows" or "iana" format. This is useful when setting the user's time zone preference in mailbox settings.
