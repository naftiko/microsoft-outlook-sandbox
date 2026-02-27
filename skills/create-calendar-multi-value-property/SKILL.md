# Create Calendar Multi-Value Extended Property

Creates a multi-value extended MAPI property on a calendar. Use this operation to store custom metadata as an array of values on a calendar using extended MAPI properties.

## API Details

- **API**: Microsoft Outlook Calendar API
- **Method**: POST
- **Path**: `/me/calendars/{calendarId}/multiValueExtendedProperties`
- **Operation ID**: `createCalendarMultiValueProperty`
- **Tag**: ExtendedProperties
- **OpenAPI**: [microsoft-outlook-calendar-api.yaml](../../openapi/microsoft-outlook-calendar-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendars/{calendarId}/multiValueExtendedProperties`

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
| `value` | array | Yes | An array of string values for the property |

## Example Request

```bash
curl -X POST "http://localhost:8080/rest/microsoft-outlook-calendar-api/1.0.0/me/calendars/AAMkAGI1AAA=/multiValueExtendedProperties" \
  -H "Authorization: Bearer {access-token}" \
  -H "Content-Type: application/json" \
  -d '{
    "id": "StringArray {66f5a359-4659-4830-9070-00047ec6ac6e} Name Tags",
    "value": ["work", "important"]
  }'
```

## Example Response

```json
{
  "id": "StringArray {66f5a359-4659-4830-9070-00047ec6ac6e} Name Tags",
  "value": [
    "work",
    "important"
  ]
}
```

## Instructions

Use this operation when you need to store custom multi-value metadata on a calendar using extended MAPI properties. The property ID follows the MAPI naming convention with a format like "StringArray {GUID} Name PropertyName". This is useful for storing arrays of application-specific data, such as tags or categories, that are not covered by standard calendar properties.
