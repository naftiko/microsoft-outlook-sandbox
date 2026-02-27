# List Primary Calendar View

Retrieves events from the user's primary calendar within a specified time range. Use this operation to get a time-windowed view of events, which automatically expands recurring event instances.

## API Details

- **API**: Microsoft Outlook Calendar API
- **Method**: GET
- **Path**: `/me/calendarView`
- **Operation ID**: `listPrimaryCalendarView`
- **Tag**: CalendarViews
- **OpenAPI**: [microsoft-outlook-calendar-api.yaml](../../openapi/microsoft-outlook-calendar-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendarView`

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
| `startDateTime` | string | Yes | Start of the time range (ISO 8601 format) |
| `endDateTime` | string | Yes | End of the time range (ISO 8601 format) |
| `$top` | integer | No | Maximum number of results to return |
| `$skip` | integer | No | Number of results to skip |
| `$select` | string | No | Comma-separated list of properties to include |
| `$filter` | string | No | OData filter expression |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendarView?startDateTime=2025-06-16T00:00:00&endDateTime=2025-06-17T00:00:00&$top=10" \
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

Use this operation when you need to retrieve events from the user's primary calendar for a specific date or time range. The startDateTime and endDateTime parameters are required and define the time window. This endpoint automatically expands recurring events into individual instances, making it ideal for displaying a calendar view. Use $top and $skip for pagination of large result sets.
