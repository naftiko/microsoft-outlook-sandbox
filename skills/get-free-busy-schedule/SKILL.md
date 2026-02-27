# Get Free/Busy Schedule

Retrieves the free/busy availability information for a collection of users and distribution lists. Use this operation to check people's availability before scheduling a meeting.

## API Details

- **API**: Microsoft Outlook Calendar API
- **Method**: POST
- **Path**: `/me/calendar/getSchedule`
- **Operation ID**: `getFreeBusySchedule`
- **Tag**: Schedules
- **OpenAPI**: [microsoft-outlook-calendar-api.yaml](../../openapi/microsoft-outlook-calendar-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendar/getSchedule`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Calendars.Read`
- `Calendars.ReadWrite`
- `Calendars.Read.Shared`
- `Calendars.ReadWrite.Shared`

## Request Body

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `schedules` | array | Yes | Array of email addresses to check availability for |
| `startTime` | object | Yes | Start of the time range with `dateTime` and `timeZone` properties |
| `endTime` | object | Yes | End of the time range with `dateTime` and `timeZone` properties |
| `availabilityViewInterval` | integer | No | Duration of each time slot in minutes (default: 30) |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendar/getSchedule" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "schedules": ["john@contoso.com", "jane@contoso.com"],
    "startTime": {
      "dateTime": "2025-06-16T09:00:00",
      "timeZone": "Pacific Standard Time"
    },
    "endTime": {
      "dateTime": "2025-06-16T18:00:00",
      "timeZone": "Pacific Standard Time"
    },
    "availabilityViewInterval": 30
  }'
```

## Example Response

```json
{
  "value": [
    {
      "scheduleId": "john@contoso.com",
      "availabilityView": "0020000020000000000000000000000000",
      "scheduleItems": [
        {
          "status": "busy",
          "start": {
            "dateTime": "2025-06-16T10:00:00",
            "timeZone": "Pacific Standard Time"
          },
          "end": {
            "dateTime": "2025-06-16T11:00:00",
            "timeZone": "Pacific Standard Time"
          },
          "subject": "Team Standup"
        }
      ],
      "workingHours": {
        "daysOfWeek": [
          "monday",
          "tuesday",
          "wednesday",
          "thursday",
          "friday"
        ],
        "startTime": "08:00:00",
        "endTime": "17:00:00",
        "timeZone": {
          "name": "Pacific Standard Time"
        }
      }
    }
  ]
}
```

## Instructions

Use this operation when you need to check the availability of one or more users before scheduling a meeting. Provide the email addresses of the people to check, along with the time range. The availabilityView string uses digits to represent availability in each time slot: 0 = free, 1 = tentative, 2 = busy, 3 = out of office, 4 = working elsewhere. The scheduleItems array provides detailed information about each busy period.
