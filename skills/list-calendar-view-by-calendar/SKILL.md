# List Calendar View by Calendar

Retrieves events from a specific calendar within a given time range. Use this operation to get a time-windowed view of events for a particular calendar, which automatically expands recurring event instances.

## API Details

- **API**: Microsoft Outlook Calendar API
- **Method**: GET
- **Path**: `/me/calendars/{calendarId}/calendarView`
- **Operation ID**: `listCalendarViewByCalendar`
- **Tag**: CalendarViews
- **OpenAPI**: [microsoft-outlook-calendar-api.yaml](../../openapi/microsoft-outlook-calendar-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendars/{calendarId}/calendarView`

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
| `startDateTime` | string | Yes | Start of the time range (ISO 8601 format) |
| `endDateTime` | string | Yes | End of the time range (ISO 8601 format) |
| `$top` | integer | No | Maximum number of results to return |
| `$skip` | integer | No | Number of results to skip |
| `$select` | string | No | Comma-separated list of properties to include |
| `$filter` | string | No | OData filter expression |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendars/AAMkAGI1AAA=/calendarView?startDateTime=2025-06-16T00:00:00&endDateTime=2025-06-17T00:00:00&$top=10" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "value": [
    {
      "id": "AAMkAGI1EVT=",
      "subject": "Team Standup",
      "start": {
        "dateTime": "2025-06-16T09:00:00",
        "timeZone": "Pacific Standard Time"
      },
      "end": {
        "dateTime": "2025-06-16T09:30:00",
        "timeZone": "Pacific Standard Time"
      },
      "organizer": {
        "emailAddress": {
          "name": "Jane Smith",
          "address": "jane@contoso.com"
        }
      },
      "isAllDay": false,
      "isCancelled": false,
      "type": "singleInstance",
      "attendees": [
        {
          "emailAddress": {
            "name": "John Doe",
            "address": "john@contoso.com"
          },
          "type": "required",
          "status": {
            "response": "accepted",
            "time": "2025-06-14T12:00:00Z"
          }
        }
      ],
      "location": {
        "displayName": "Conference Room A"
      }
    }
  ]
}
```

## Instructions

Use this operation when you need to retrieve events from a specific calendar (not the default primary calendar) for a particular date or time range. Both startDateTime and endDateTime are required. This is useful when the user has multiple calendars and you need events from a non-default one. Recurring events are automatically expanded into individual instances.
