# List Calendar Events

Retrieves all events from a specific calendar. Use this operation to get the complete list of events in a calendar, with optional filtering, sorting, and pagination.

## API Details

- **API**: Microsoft Outlook Calendar API
- **Method**: GET
- **Path**: `/me/calendars/{calendarId}/events`
- **Operation ID**: `listCalendarEvents`
- **Tag**: Events
- **OpenAPI**: [microsoft-outlook-calendar-api.yaml](../../openapi/microsoft-outlook-calendar-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendars/{calendarId}/events`

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
| `$top` | integer | No | Maximum number of results to return |
| `$skip` | integer | No | Number of results to skip |
| `$select` | string | No | Comma-separated list of properties to include |
| `$filter` | string | No | OData filter expression |
| `$orderby` | string | No | OData orderby expression |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendars/AAMkAGI1AAA=/events?$top=10&$orderby=start/dateTime" \
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

Use this operation when you need to retrieve all events from a specific calendar. Unlike calendarView, this endpoint does not expand recurring events into individual instances. Use $filter to narrow results and $orderby to sort them. For time-range queries with recurring event expansion, use the calendarView endpoint instead.
