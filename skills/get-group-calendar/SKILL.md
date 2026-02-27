# Get Group Calendar

Retrieves the default calendar of a Microsoft 365 group. Use this operation to access the shared calendar associated with a group for viewing its properties.

## API Details

- **API**: Microsoft Outlook Calendar API
- **Method**: GET
- **Path**: `/groups/{groupId}/calendar`
- **Operation ID**: `getGroupCalendar`
- **Tag**: GroupCalendars
- **OpenAPI**: [microsoft-outlook-calendar-api.yaml](../../openapi/microsoft-outlook-calendar-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/groups/{groupId}/calendar`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Group.Read.All`
- `Group.ReadWrite.All`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `groupId` | string | Yes | The unique identifier of the Microsoft 365 group |

## Query Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `$select` | string | No | Comma-separated list of properties to include |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/groups/02bd9fd6-8f93-4758-87c3-1fb73740a315/calendar" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "id": "AAMkAGI1DDD=",
  "name": "Engineering Team",
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

Use this operation when you need to retrieve the default calendar for a Microsoft 365 group. This gives you access to the shared group calendar's properties, including its name, permissions, and owner information. You need the group ID, which can be obtained from the Microsoft Graph groups API.
