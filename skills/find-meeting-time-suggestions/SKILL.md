# Find Meeting Time Suggestions

Suggests meeting times based on the availability of attendees, organizer, and time constraints. Use this operation to automatically find optimal meeting slots for a group of participants.

## API Details

- **API**: Microsoft Outlook Calendar API
- **Method**: POST
- **Path**: `/me/findMeetingTimes`
- **Operation ID**: `findMeetingTimeSuggestions`
- **Tag**: Schedules
- **OpenAPI**: [microsoft-outlook-calendar-api.yaml](../../openapi/microsoft-outlook-calendar-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/findMeetingTimes`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Calendars.Read`
- `Calendars.ReadWrite`

## Request Body

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `attendees` | array | Yes | List of attendees with `emailAddress` and `type` (required/optional) |
| `timeConstraint` | object | No | Time constraints with `activityDomain` and `timeSlots` array |
| `meetingDuration` | string | No | Duration in ISO 8601 format (e.g., "PT1H" for 1 hour) |
| `maxCandidates` | integer | No | Maximum number of suggestions to return |
| `minimumAttendeePercentage` | number | No | Minimum percentage of attendees that must be available |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/findMeetingTimes" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "attendees": [
      {
        "emailAddress": {
          "name": "John Doe",
          "address": "john@contoso.com"
        },
        "type": "required"
      }
    ],
    "timeConstraint": {
      "activityDomain": "work",
      "timeSlots": [
        {
          "start": {
            "dateTime": "2025-06-16T09:00:00",
            "timeZone": "Pacific Standard Time"
          },
          "end": {
            "dateTime": "2025-06-16T18:00:00",
            "timeZone": "Pacific Standard Time"
          }
        }
      ]
    },
    "meetingDuration": "PT1H"
  }'
```

## Example Response

```json
{
  "meetingTimeSuggestions": [
    {
      "confidence": 100,
      "organizerAvailability": "free",
      "meetingTimeSlot": {
        "start": {
          "dateTime": "2025-06-16T14:00:00",
          "timeZone": "Pacific Standard Time"
        },
        "end": {
          "dateTime": "2025-06-16T15:00:00",
          "timeZone": "Pacific Standard Time"
        }
      },
      "attendeeAvailability": [
        {
          "attendee": {
            "emailAddress": {
              "name": "John Doe",
              "address": "john@contoso.com"
            },
            "type": "required"
          },
          "availability": "free"
        }
      ]
    }
  ]
}
```

## Instructions

Use this operation when you need to find optimal meeting times for a group of attendees. Provide the list of attendees and optionally constrain the search to specific time windows and meeting duration. The response includes suggested time slots ranked by confidence score (0-100), where higher values indicate better availability across all participants. The activityDomain can be "work", "personal", or "unrestricted" to control which hours are considered.
