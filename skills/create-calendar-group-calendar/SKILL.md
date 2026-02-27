# Create Calendar in Calendar Group

Creates a new calendar within a specified calendar group. Use this operation when you need to add a calendar to a particular organizational group rather than the default group.

## API Details

- **API**: Microsoft Outlook Calendar API
- **Method**: POST
- **Path**: `/me/calendarGroups/{calendarGroupId}/calendars`
- **Operation ID**: `createCalendarGroupCalendar`
- **Tag**: CalendarGroups
- **OpenAPI**: [microsoft-outlook-calendar-api.yaml](../../openapi/microsoft-outlook-calendar-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendarGroups/{calendarGroupId}/calendars`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Calendars.ReadWrite`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `calendarGroupId` | string | Yes | The unique identifier of the calendar group |

## Request Body

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | string | Yes | The name of the new calendar |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendarGroups/AAMkAGI1GRP=/calendars" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Team Meetings"
  }'
```

## Example Response

```json
{
  "id": "AAMkAGI1CCC=",
  "name": "Team Meetings",
  "color": "auto",
  "isDefaultCalendar": false,
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

Use this operation when you need to create a new calendar inside a specific calendar group. You must provide the calendar group ID and the name for the new calendar. This is useful for organizing calendars into logical groups such as work, personal, or project-specific collections.
