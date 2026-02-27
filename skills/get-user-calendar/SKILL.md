# Get User Calendar

Retrieves the properties and relationships of a single calendar by its ID. Use this operation to get detailed information about a specific calendar.

## API Details

- **API**: Microsoft Outlook Calendar API
- **Method**: GET
- **Path**: `/me/calendars/{calendarId}`
- **Operation ID**: `getUserCalendar`
- **Tag**: Calendars
- **OpenAPI**: [microsoft-outlook-calendar-api.yaml](../../openapi/microsoft-outlook-calendar-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendars/{calendarId}`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Calendars.Read`
- `Calendars.ReadWrite`
- `Calendars.Read.Shared`
- `Calendars.ReadWrite.Shared`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `calendarId` | string | Yes | The unique identifier of the calendar |

## Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `$select` | string | No | Comma-separated list of properties to include |
| `$expand` | string | No | Related entities to expand inline |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendars/AAMkAGI1AAA=" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
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
```

## Instructions

Use this operation when you need to retrieve details about a specific calendar by its ID. This is helpful for checking calendar properties such as permissions, ownership, and color settings before performing further operations on it.
