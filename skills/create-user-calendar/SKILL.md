# Create User Calendar

Creates a new calendar for the authenticated user in the default or specified calendar group. Use this operation when a user needs a new calendar to organize events separately.

## API Details

- **API**: Microsoft Outlook Calendar API
- **Method**: POST
- **Path**: `/me/calendars`
- **Operation ID**: `createUserCalendar`
- **Tag**: Calendars
- **OpenAPI**: [microsoft-outlook-calendar-api.yaml](../../openapi/microsoft-outlook-calendar-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendars`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Calendars.ReadWrite`

## Request Body

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | string | Yes | The name of the new calendar |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendars" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Project Deadlines"
  }'
```

## Example Response

```json
{
  "id": "AAMkAGI1BBB=",
  "name": "Project Deadlines",
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

Use this operation when you need to create a new calendar for the user. The only required field is the calendar name. The newly created calendar will appear in the user's default calendar group unless otherwise specified.
