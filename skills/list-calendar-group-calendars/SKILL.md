# List Calendar Group Calendars

Retrieves the calendars belonging to a specific calendar group. Use this operation to get all calendars within a particular calendar group for the authenticated user.

## API Details

- **API**: Microsoft Outlook Calendar API
- **Method**: GET
- **Path**: `/me/calendarGroups/{calendarGroupId}/calendars`
- **Operation ID**: `listCalendarGroupCalendars`
- **Tag**: CalendarGroups
- **OpenAPI**: [microsoft-outlook-calendar-api.yaml](../../openapi/microsoft-outlook-calendar-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendarGroups/{calendarGroupId}/calendars`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Calendars.Read`
- `Calendars.ReadWrite`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `calendarGroupId` | string | Yes | The unique identifier of the calendar group |

## Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `$top` | integer | No | Maximum number of results to return |
| `$skip` | integer | No | Number of results to skip |
| `$select` | string | No | Comma-separated list of properties to include |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendarGroups/AAMkAGI1GRP=/calendars?$top=10" \
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

Use this operation when you need to list all calendars within a specific calendar group. Calendar groups allow users to organize their calendars into logical collections. You must provide the calendar group ID, which can be obtained from the calendar groups listing endpoint.
