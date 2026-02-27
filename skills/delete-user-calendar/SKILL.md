# Delete User Calendar

Deletes a calendar by moving it to the deleted items folder. Use this operation when you need to remove a calendar that is no longer needed.

## API Details

- **API**: Microsoft Outlook Calendar API
- **Method**: DELETE
- **Path**: `/me/calendars/{calendarId}`
- **Operation ID**: `deleteUserCalendar`
- **Tag**: Calendars
- **OpenAPI**: [microsoft-outlook-calendar-api.yaml](../../openapi/microsoft-outlook-calendar-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendars/{calendarId}`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Calendars.ReadWrite`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `calendarId` | string | Yes | The unique identifier of the calendar to delete |

## Example Request

```bash
curl -X DELETE "http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendars/AAMkAGI1AAA=" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```
204 No Content
```

## Instructions

Use this operation when you need to delete a user's calendar. The calendar is moved to the deleted items folder and may be recoverable. Note that you cannot delete the user's default calendar. For permanent deletion, use the permanentDelete operation instead.
