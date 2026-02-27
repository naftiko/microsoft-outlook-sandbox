# List Supported Languages

List all supported languages for the user's mailbox.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/me/outlook/supportedLanguages`
- **Operation ID**: `listSupportedLanguages`
- **Tag**: LocaleAndTimeZone
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/outlook/supportedLanguages`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `MailboxSettings.Read`

## Parameters

No required parameters.

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/outlook/supportedLanguages" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "value": [
    {
      "locale": "en-US",
      "displayName": "English (United States)"
    }
  ]
}
```

## Instructions

Use this operation to retrieve the list of languages supported for the user's mailbox configuration. The response includes locale codes and display names for each supported language. This is useful when setting the user's language preference in mailbox settings.
