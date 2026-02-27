# Update Group Calendar

Updates the properties of a Microsoft 365 group's calendar. Use this operation when you need to modify the shared calendar settings for a group.

## API Details

- **API**: Microsoft Outlook Calendar API
- **Method**: PATCH
- **Path**: `/groups/{groupId}/calendar`
- **Operation ID**: `patchGroupCalendar`
- **Tag**: GroupCalendars
- **OpenAPI**: [microsoft-outlook-calendar-api.yaml](../../openapi/microsoft-outlook-calendar-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/groups/{groupId}/calendar`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Group.ReadWrite.All`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `groupId` | string | Yes | The unique identifier of the Microsoft 365 group |

## Request Body

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `name` | string | No | The updated name of the group calendar |
| `color` | string | No | The color theme for the calendar |

## Example Request

```bash
curl -X PATCH "http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/groups/02bd9fd6-8f93-4758-87c3-1fb73740a315/calendar" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Engineering Team Calendar"
  }'
```

## Example Response

```json
{
  "id": "AAMkAGI1DDD=",
  "name": "Engineering Team Calendar",
  "color": "auto",
  "isDefaultCalendar": true,
  "canEdit": true,
  "canShare": false,
  "canViewPrivateItems": false,
  "owner": {
    "name": "Engineering Team",
    "address": "engineering@contoso.com"
  }
}
```

## Instructions

Use this operation when you need to update a Microsoft 365 group calendar's properties, such as renaming it. Only include the properties you want to change in the request body. You need Group.ReadWrite.All permissions to modify group calendar settings.
