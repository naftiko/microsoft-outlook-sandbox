# Create Default Calendar Event

Creates a new event in the user's default calendar. Use this operation when you need to schedule a meeting or event without specifying a particular calendar.

## API Details

- **API**: Microsoft Outlook Calendar API
- **Method**: POST
- **Path**: `/me/events`
- **Operation ID**: `createDefaultCalendarEvent`
- **Tag**: Events
- **OpenAPI**: [microsoft-outlook-calendar-api.yaml](../../openapi/microsoft-outlook-calendar-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/events`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Calendars.ReadWrite`

## Request Body

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `subject` | string | Yes | The subject/title of the event |
| `start` | object | Yes | Start date/time with `dateTime` and `timeZone` properties |
| `end` | object | Yes | End date/time with `dateTime` and `timeZone` properties |
| `attendees` | array | No | List of attendees with `emailAddress` and `type` |
| `location` | object | No | Location with `displayName` property |
| `body` | object | No | Event body with `contentType` and `content` |
| `isAllDay` | boolean | No | Whether the event lasts all day |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/events" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "subject": "Project Review",
    "start": {
      "dateTime": "2025-06-20T14:00:00",
      "timeZone": "Pacific Standard Time"
    },
    "end": {
      "dateTime": "2025-06-20T15:00:00",
      "timeZone": "Pacific Standard Time"
    },
    "attendees": [
      {
        "emailAddress": {
          "name": "John Doe",
          "address": "john@contoso.com"
        },
        "type": "required"
      }
    ],
    "location": {
      "displayName": "Conference Room B"
    }
  }'
```

## Example Response

```json
{
  "id": "AAMkAGI1NEW=",
  "subject": "Project Review",
  "start": {
    "dateTime": "2025-06-20T14:00:00",
    "timeZone": "Pacific Standard Time"
  },
  "end": {
    "dateTime": "2025-06-20T15:00:00",
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
        "response": "none",
        "time": "0001-01-01T00:00:00Z"
      }
    }
  ],
  "location": {
    "displayName": "Conference Room B"
  }
}
```

## Instructions

Use this operation when you need to create a new event in the user's default calendar. This is the simplest way to create an event when you do not need to target a specific calendar. You must provide the subject, start time, and end time at minimum. The response returns a 201 status code with the created event object. Meeting invitations are automatically sent to attendees.
