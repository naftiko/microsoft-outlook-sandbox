# Create Calendar Single-Value Extended Property

Creates a single-value extended MAPI property on a calendar. Use this operation to store custom metadata as a single string value on a calendar using extended MAPI properties.

## API Details

- **API**: Microsoft Outlook Calendar API
- **Method**: POST
- **Path**: `/me/calendars/{calendarId}/singleValueExtendedProperties`
- **Operation ID**: `createCalendarSingleValueProperty`
- **Tag**: ExtendedProperties
- **OpenAPI**: [microsoft-outlook-calendar-api.yaml](../../openapi/microsoft-outlook-calendar-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendars/{calendarId}/singleValueExtendedProperties`

## Required Headers

- `Authorization: Bearer {access-token}`
- `Content-Type: application/json`

## OAuth Scopes

- `Calendars.ReadWrite`

## Path Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `calendarId` | string | Yes | The unique identifier of the calendar |

## Request Body

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `id` | string | Yes | The property identifier in MAPI format |
| `value` | string | Yes | The single string value for the property |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendars/AAMkAGI1AAA=/singleValueExtendedProperties" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "id": "String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color",
    "value": "Green"
  }'
```

## Example Response

```json
{
  "id": "String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color",
  "value": "Green"
}
```

## Instructions

Use this operation when you need to store custom single-value metadata on a calendar using extended MAPI properties. The property ID follows the MAPI naming convention with a format like "String {GUID} Name PropertyName". This is useful for storing application-specific data that is not covered by standard calendar properties.
