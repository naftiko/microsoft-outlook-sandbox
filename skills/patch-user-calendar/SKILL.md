# Update User Calendar

Updates the properties of an existing calendar, such as its name or color. Use this operation when you need to modify calendar settings for the authenticated user.

## API Details

- **API**: Microsoft Outlook Calendar API
- **Method**: PATCH
- **Path**: `/me/calendars/{calendarId}`
- **Operation ID**: `patchUserCalendar`
- **Tag**: Calendars
- **OpenAPI**: [microsoft-outlook-calendar-api.yaml](../../openapi/microsoft-outlook-calendar-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendars/{calendarId}`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Calendars.ReadWrite`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `calendarId` | string | Yes | The unique identifier of the calendar to update |

## Request Body

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | string | No | The updated name of the calendar |
| `color` | string | No | The color theme (auto, lightBlue, lightGreen, lightOrange, lightGray, lightYellow, lightTeal, lightPink, lightBrown, lightRed, maxColor) |

## Example Request

```bash
curl -X PATCH "http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendars/AAMkAGI1AAA=" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Updated Calendar Name",
    "color": "lightBlue"
  }'
```

## Example Response

```json
{
  "id": "AAMkAGI1AAA=",
  "name": "Updated Calendar Name",
  "color": "lightBlue",
  "isDefaultCalendar": true,
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

Use this operation when you need to update a calendar's properties such as its display name or color. Only include the properties you want to change in the request body. Properties not included in the request will remain unchanged.
