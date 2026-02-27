# List Messages in Mailbox

Retrieves a collection of messages from the signed-in user's mailbox, supporting filtering, searching, sorting, and pagination through OData query parameters.

## API Details

- **API**: Microsoft Outlook Mail API
- **Method**: GET
- **Path**: `/me/messages`
- **Operation ID**: `listMessages`
- **Tag**: Messages
- **OpenAPI**: [microsoft-outlook-mail-api.yaml](../../openapi/microsoft-outlook-mail-api.yaml)

## Sandbox

Mock server URL: `http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages`

## Required Headers

- `Authorization: Bearer {access-token}`

## OAuth Scopes

- `Mail.Read`
- `Mail.ReadWrite`

## Query Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `$top` | integer | Number of results to return |
| `$skip` | integer | Number of results to skip |
| `$select` | string | Comma-separated list of properties to include |
| `$filter` | string | OData filter expression |
| `$search` | string | Search expression to match messages |
| `$orderby` | string | Property and direction to sort by |
| `$count` | boolean | Include total count of matching results |

## Example Request

```bash
curl -X GET "http://localhost:8080/rest/microsoft-outlook-mail-api/1.0.0/me/messages?$top=10&$select=subject,from,receivedDateTime&$orderby=receivedDateTime desc" \
  -H "Authorization: Bearer {access-token}"
```

## Example Response

```json
{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#me/messages",
  "value": [
    {
      "id": "AAMkAGI1AAAGB1rUAAA=",
      "subject": "Quarterly Review Meeting",
      "bodyPreview": "Please join us for the quarterly review...",
      "body": {"contentType": "html", "content": "<html><body>Please join us for the quarterly review...</body></html>"},
      "importance": "normal",
      "isRead": false,
      "isDraft": false,
      "hasAttachments": false,
      "from": {"emailAddress": {"name": "Alex Wilber", "address": "alex@contoso.com"}},
      "toRecipients": [{"emailAddress": {"name": "Megan Bowen", "address": "megan@contoso.com"}}],
      "createdDateTime": "2024-01-15T10:30:00Z",
      "receivedDateTime": "2024-01-15T10:30:00Z",
      "parentFolderId": "AAMkAGI1AAAEJAAA="
    }
  ]
}
```

## Instructions

Use this operation to retrieve messages from a user's mailbox. Apply `$filter` to narrow results by criteria such as `isRead eq false` or `from/emailAddress/address eq 'alex@contoso.com'`. Use `$search` for keyword-based searches across message content. Combine `$top` and `$skip` for pagination, and use `$select` to limit the properties returned for better performance. Results are returned in descending order by `receivedDateTime` by default.
