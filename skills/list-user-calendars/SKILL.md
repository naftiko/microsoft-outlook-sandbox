# List User Calendars

Retrieves all calendars belonging to the authenticated user. Use this operation to enumerate a user's calendars, optionally filtering or selecting specific properties.

## API Details

- **API**: Microsoft Outlook Calendar API
- **Method**: GET
- **Path**: `/me/calendars`
- **Operation ID**: `listUserCalendars`
- **Tag**: Calendars
- **OpenAPI**: [microsoft-outlook-calendar-api.yaml](../../openapi/microsoft-outlook-calendar-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendars`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Calendars.Read`
- `Calendars.ReadWrite`
- `Calendars.Read.Shared`
- `Calendars.ReadWrite.Shared`

## Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `$top` | integer | No | Maximum number of results to return |
| `$skip` | integer | No | Number of results to skip |
| `$filter` | string | No | OData filter expression |
| `$select` | string | No | Comma-separated list of properties to include |
| `$orderby` | string | No | OData orderby expression |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendars?$top=10" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "value": [
    {
      "id": "AAMkAGI1AAA=",
      "name": "Calendar",
      "color": "auto",
      "isDefaultCalendar": true,
      "canEdit": true,
      "canShare": true,
      "canViewPrivateItems": true,
      "owner": {
        "name": "Jane Smith",
        "address": "jane@contoso.com"
      }
    }
  ]
}
```

## Instructions

Use this operation when you need to retrieve a list of all calendars for the authenticated user. This is useful for discovering available calendars before performing operations on specific ones, such as listing events or creating new events in a particular calendar.
