# Permanently Delete User Calendar

Permanently deletes a calendar folder from the user's mailbox. Use this operation when you need to irrecoverably remove a calendar without moving it to deleted items.

## API Details

- **API**: Microsoft Outlook Calendar API
- **Method**: POST
- **Path**: `/me/calendars/{calendarId}/permanentDelete`
- **Operation ID**: `permanentDeleteUserCalendar`
- **Tag**: Calendars
- **OpenAPI**: [microsoft-outlook-calendar-api.yaml](../../openapi/microsoft-outlook-calendar-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendars/{calendarId}/permanentDelete`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Calendars.ReadWrite`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `calendarId` | string | Yes | The unique identifier of the calendar to permanently delete |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendars/AAMkAGI1AAA=/permanentDelete" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json"
```

## Example Response

```
204 No Content
```

## Instructions

Use this operation when you need to permanently and irrecoverably delete a calendar from the user's mailbox. Unlike the standard delete operation, this does not move the calendar to deleted items -- it is removed entirely and cannot be recovered. Exercise caution when using this operation.
