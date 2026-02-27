# Microsoft Outlook Sandbox
This is sandbox for the Microsoft Outlook Sandbox API, using an OpenAPI specification with examples, Microcks and Bruno as the sandbox interface, and this GitHub repository as the vehicle for delivering as a localized sandbox, or also enabling the working directly with production APIs.

## APIs.json Index
There is an APIs.yml file in the root of this repository, providing an index of all the artifacts used as part of this capability, providing a machine-readable way to read, manage, and execute the resources available here.

## OpenAPI
This capability uses OpenAPI as the definition, providing a complete definition of all available paths for the Microsoft Outlook Sandbox. The OpenAPI for this capability uses examples and Microcks extensions to mock the requests and responses for each API operation, something we will iterate and expand upon with richer examples as the capability evolves.

## Microcks
This capability uses Microcks to deliver the mock API. [You just install Microcks, with the Docker extension being the easiest](https://microcks.io/documentation/guides/installation/docker-desktop-extension/), [import the OpenAPI as a service](openapi/notion-openapi.yml), and you have a mocked API for all APIs, available via REST and MCP APIs--providing a multi-protocol sandbox.

## Bruno
This capability [uses Bruno as the client](https://www.usebruno.com/), leveraging Bruno Collections pre-generated from the OpenAPI and Bruno environments that uses the localhost and port of Microcks to work with the mocked API. You just have to install Microcks, then open the collection provided in this repository, select the available environments, and begin calling the Microsoft Outlook Sandbox via the sandbox or production.


## OpenAPIs
These are the OpenAPIs available for the Microsoft Outlook Sandbox, which are made available via this sandbox API, which can be imported into Microcks and deployed as a sandbox using their mock feature.

  - [Microsoft Outlook Mail Api.yaml](openapi/microsoft-outlook-mail-api.yaml)
  - [Microsoft Outlook Mail Api.yaml](openapi/microsoft-outlook-mail-api.yaml)

## Agent Skills
These are the agent skills available for the Microsoft Outlook Sandbox, providing a discrete list of capabilities that AI agents can use when working with Microsoft Outlook mail and calendar via the Microsoft Graph API. Each skill maps directly to an OpenAPI operation, making it easy for agents to discover and invoke the right capability for a given task.

### Calendar API

#### Calendars
  - [List User Calendars](skills/list-user-calendars/SKILL.md) (`listUserCalendars`) — Get all calendars for the signed-in user with optional filtering and pagination.
  - [Create User Calendar](skills/create-user-calendar/SKILL.md) (`createUserCalendar`) — Create a new calendar in the default or specified calendar group.
  - [Get User Calendar](skills/get-user-calendar/SKILL.md) (`getUserCalendar`) — Get properties and relationships of a single calendar by its ID.
  - [Update User Calendar](skills/patch-user-calendar/SKILL.md) (`patchUserCalendar`) — Update calendar properties such as name and color.
  - [Delete User Calendar](skills/delete-user-calendar/SKILL.md) (`deleteUserCalendar`) — Delete a calendar, moving it to deleted items.
  - [Permanently Delete Calendar](skills/permanent-delete-user-calendar/SKILL.md) (`permanentDeleteUserCalendar`) — Permanently delete a calendar folder from the mailbox with no recovery option.

#### Calendar Groups
  - [List Calendar Group Calendars](skills/list-calendar-group-calendars/SKILL.md) (`listCalendarGroupCalendars`) — Get calendars in a specific calendar group.
  - [Create Calendar in Group](skills/create-calendar-group-calendar/SKILL.md) (`createCalendarGroupCalendar`) — Create a new calendar in a specified calendar group.

#### Group Calendars
  - [Get Group Calendar](skills/get-group-calendar/SKILL.md) (`getGroupCalendar`) — Get the default calendar of a Microsoft 365 group.
  - [Update Group Calendar](skills/patch-group-calendar/SKILL.md) (`patchGroupCalendar`) — Update properties of a Microsoft 365 group calendar.

#### Calendar Views
  - [List Primary Calendar View](skills/list-primary-calendar-view/SKILL.md) (`listPrimaryCalendarView`) — Get events in the primary calendar for a specified time range.
  - [List Calendar View by Calendar](skills/list-calendar-view-by-calendar/SKILL.md) (`listCalendarViewByCalendar`) — Get events in a specific calendar for a specified time range.

#### Events
  - [List Calendar Events](skills/list-calendar-events/SKILL.md) (`listCalendarEvents`) — Get all events in a specified calendar.
  - [Create Calendar Event](skills/create-calendar-event/SKILL.md) (`createCalendarEvent`) — Create a new event in a specified calendar.
  - [Create Default Calendar Event](skills/create-default-calendar-event/SKILL.md) (`createDefaultCalendarEvent`) — Create a new event in the user's default calendar.

#### Schedules
  - [Get Free/Busy Schedule](skills/get-free-busy-schedule/SKILL.md) (`getFreeBusySchedule`) — Get free/busy availability information for users and groups over a time range.
  - [Find Meeting Time Suggestions](skills/find-meeting-time-suggestions/SKILL.md) (`findMeetingTimeSuggestions`) — Suggest meeting times based on participants' availability and constraints.

#### Calendar Extended Properties
  - [Create Single-Value Property](skills/create-calendar-single-value-property/SKILL.md) (`createCalendarSingleValueProperty`) — Create a single-value extended MAPI property on a calendar.
  - [Create Multi-Value Property](skills/create-calendar-multi-value-property/SKILL.md) (`createCalendarMultiValueProperty`) — Create a multi-value extended MAPI property on a calendar.

### Mail API

#### Messages
  - [List Messages](skills/list-messages/SKILL.md) (`listMessages`) — Get messages in the signed-in user's mailbox with filtering, search, and pagination.
  - [Create Draft Message](skills/create-message/SKILL.md) (`createMessage`) — Create a draft message with support for delegation via from/sender properties.
  - [Get Message](skills/get-message/SKILL.md) (`getMessage`) — Get the properties and relationships of a message by its ID.
  - [Update Message](skills/update-message/SKILL.md) (`updateMessage`) — Update properties of a message such as subject, body, or read status.
  - [Delete Message](skills/delete-message/SKILL.md) (`deleteMessage`) — Delete a message from the user's mailbox.
  - [Reply to Message](skills/reply-to-message/SKILL.md) (`replyToMessage`) — Reply to the sender of a message with an optional comment.
  - [Reply All to Message](skills/reply-all-to-message/SKILL.md) (`replyAllToMessage`) — Reply to all recipients of a message with an optional comment.
  - [Forward Message](skills/forward-message/SKILL.md) (`forwardMessage`) — Forward a message to one or more recipients with an optional comment.
  - [Send Mail](skills/send-mail/SKILL.md) (`sendMail`) — Send a new message in JSON or MIME format with optional save to sent items.
  - [Send Draft Message](skills/send-draft-message/SKILL.md) (`sendDraftMessage`) — Send an existing draft message from the user's mailbox.

#### MIME Content
  - [Get Message MIME Content](skills/get-message-mime-content/SKILL.md) (`getMessageMimeContent`) — Get the MIME representation of a message including any attachments.
  - [Get Attachment Content](skills/get-attachment-content/SKILL.md) (`getAttachmentContent`) — Get the raw binary content of a message attachment.

#### Attachments
  - [List Attachments](skills/list-attachments/SKILL.md) (`listAttachments`) — Get all attachments on a message.
  - [Add Attachment](skills/create-attachment/SKILL.md) (`createAttachment`) — Add a file, item, or reference attachment to a message.
  - [Get Attachment](skills/get-attachment/SKILL.md) (`getAttachment`) — Get a single attachment by its ID.
  - [Delete Attachment](skills/delete-attachment/SKILL.md) (`deleteAttachment`) — Delete an attachment from a message.

#### Mail Folders
  - [List Mail Folders](skills/list-mail-folders/SKILL.md) (`listMailFolders`) — Get all mail folders in the user's mailbox.
  - [Create Mail Folder](skills/create-mail-folder/SKILL.md) (`createMailFolder`) — Create a new mail folder in the mailbox root.
  - [Get Mail Folder](skills/get-mail-folder/SKILL.md) (`getMailFolder`) — Get a mail folder by its ID.
  - [Update Mail Folder](skills/update-mail-folder/SKILL.md) (`updateMailFolder`) — Update mail folder properties such as display name.
  - [Delete Mail Folder](skills/delete-mail-folder/SKILL.md) (`deleteMailFolder`) — Delete a mail folder and its contents.
  - [List Folder Messages](skills/list-mail-folder-messages/SKILL.md) (`listMailFolderMessages`) — Get messages in a specific mail folder.
  - [List Child Folders](skills/list-child-folders/SKILL.md) (`listChildFolders`) — Get child folders under a specified mail folder.
  - [Create Child Folder](skills/create-child-folder/SKILL.md) (`createChildFolder`) — Create a child folder under a specified parent folder.
  - [Copy Mail Folder](skills/copy-mail-folder/SKILL.md) (`copyMailFolder`) — Copy a mail folder and its contents to a destination folder.
  - [Move Mail Folder](skills/move-mail-folder/SKILL.md) (`moveMailFolder`) — Move a mail folder to a different destination folder.

#### Mail Search Folders
  - [Create Search Folder](skills/create-mail-search-folder/SKILL.md) (`createMailSearchFolder`) — Create a search folder to dynamically query messages with a filter.
  - [Get Search Folder](skills/get-mail-search-folder/SKILL.md) (`getMailSearchFolder`) — Get a mail search folder by its ID.
  - [Update Search Folder](skills/update-mail-search-folder/SKILL.md) (`updateMailSearchFolder`) — Update a search folder's filter query or source folders.
  - [Delete Search Folder](skills/delete-mail-search-folder/SKILL.md) (`deleteMailSearchFolder`) — Delete a mail search folder.

#### Categories
  - [List Categories](skills/list-categories/SKILL.md) (`listCategories`) — Get all Outlook color categories defined for the user.
  - [Create Category](skills/create-category/SKILL.md) (`createCategory`) — Create a new Outlook color category.
  - [Get Category](skills/get-category/SKILL.md) (`getCategory`) — Get an Outlook category by its ID.
  - [Update Category](skills/update-category/SKILL.md) (`updateCategory`) — Update an Outlook category's name or color.
  - [Delete Category](skills/delete-category/SKILL.md) (`deleteCategory`) — Delete an Outlook category.

#### Inbox Rules
  - [List Inbox Rules](skills/list-message-rules/SKILL.md) (`listMessageRules`) — Get all message rules defined for the user's inbox.
  - [Create Inbox Rule](skills/create-message-rule/SKILL.md) (`createMessageRule`) — Create a rule to automate actions such as forwarding specific messages.
  - [Get Inbox Rule](skills/get-message-rule/SKILL.md) (`getMessageRule`) — Get an inbox message rule by its ID.
  - [Update Inbox Rule](skills/update-message-rule/SKILL.md) (`updateMessageRule`) — Update an inbox message rule's conditions or actions.
  - [Delete Inbox Rule](skills/delete-message-rule/SKILL.md) (`deleteMessageRule`) — Delete an inbox message rule.

#### Focused Inbox
  - [List Focused Inbox Overrides](skills/list-inference-classification-overrides/SKILL.md) (`listInferenceClassificationOverrides`) — Get overrides for classifying messages from specific senders as focused or other.
  - [Create Focused Inbox Override](skills/create-inference-classification-override/SKILL.md) (`createInferenceClassificationOverride`) — Create an override to always classify messages from a sender as focused or other.
  - [Get Focused Inbox Override](skills/get-inference-classification-override/SKILL.md) (`getInferenceClassificationOverride`) — Get a Focused Inbox classification override by its ID.
  - [Update Focused Inbox Override](skills/update-inference-classification-override/SKILL.md) (`updateInferenceClassificationOverride`) — Update a Focused Inbox classification override.
  - [Delete Focused Inbox Override](skills/delete-inference-classification-override/SKILL.md) (`deleteInferenceClassificationOverride`) — Delete a Focused Inbox classification override.

#### Mailbox Settings
  - [Get Mailbox Settings](skills/get-mailbox-settings/SKILL.md) (`getMailboxSettings`) — Get the user's mailbox settings including automatic replies, locale, time zone, and working hours.
  - [Update Mailbox Settings](skills/update-mailbox-settings/SKILL.md) (`updateMailboxSettings`) — Update one or more mailbox settings such as automatic replies or time zone.

#### Locale and Time Zone
  - [List Supported Languages](skills/list-supported-languages/SKILL.md) (`listSupportedLanguages`) — Get the list of locales and languages supported for the user.
  - [List Supported Time Zones](skills/list-supported-time-zones/SKILL.md) (`listSupportedTimeZones`) — Get the list of time zones supported for the user in Windows or IANA format.

#### Mail Tips
  - [Get Mail Tips](skills/get-mail-tips/SKILL.md) (`getMailTips`) — Get MailTips for recipients including out-of-office status and delivery restrictions.

#### Subscriptions
  - [List Subscriptions](skills/list-subscriptions/SKILL.md) (`listSubscriptions`) — Get all webhook subscriptions for change notifications.
  - [Create Subscription](skills/create-subscription/SKILL.md) (`createSubscription`) — Subscribe to change notifications for messages in a folder.
  - [Get Subscription](skills/get-subscription/SKILL.md) (`getSubscription`) — Get a webhook subscription by its ID.
  - [Renew Subscription](skills/renew-subscription/SKILL.md) (`renewSubscription`) — Renew a webhook subscription's expiration date.
  - [Delete Subscription](skills/delete-subscription/SKILL.md) (`deleteSubscription`) — Delete a webhook subscription.

#### Synchronization
  - [Get Mail Folder Delta](skills/get-mail-folder-delta/SKILL.md) (`getMailFolderDelta`) — Get incremental changes to mail folders using delta queries.
  - [Get Message Delta](skills/get-message-delta/SKILL.md) (`getMessageDelta`) — Get incremental changes to messages in a folder using delta queries.

#### Message Trace
  - [Get Message Trace](skills/get-message-trace/SKILL.md) (`getMessageTrace`) — Trace a message through the Exchange Online organization to see routing and delivery events.

#### Extensions
  - [List Extensions](skills/list-extensions/SKILL.md) (`listExtensions`) — Get open type extensions on a message for custom app data.
  - [Create Open Extension](skills/create-open-extension/SKILL.md) (`createOpenExtension`) — Create an open type extension to store custom app data on a message.
  - [Get Extension](skills/get-extension/SKILL.md) (`getExtension`) — Get an open type extension on a message by its ID.
  - [Update Open Extension](skills/update-open-extension/SKILL.md) (`updateOpenExtension`) — Update an open type extension on a message.
  - [Delete Extension](skills/delete-extension/SKILL.md) (`deleteExtension`) — Delete an open type extension from a message.

#### Extended Properties
  - [List Single-Value Properties](skills/list-single-value-extended-properties/SKILL.md) (`listSingleValueExtendedProperties`) — Get single-value extended MAPI properties on a message.
  - [Create Single-Value Property](skills/create-single-value-extended-property/SKILL.md) (`createSingleValueExtendedProperty`) — Create a single-value extended MAPI property on a message.
  - [List Multi-Value Properties](skills/list-multi-value-extended-properties/SKILL.md) (`listMultiValueExtendedProperties`) — Get multi-value extended MAPI properties on a message.
  - [Create Multi-Value Property](skills/create-multi-value-extended-property/SKILL.md) (`createMultiValueExtendedProperty`) — Create a multi-value extended MAPI property on a message.

## Support
Please provide any questions or feedback via GitHub issues, or just email kinlane@naftiko.io with feedback. The goal is to keep iterating upon this sandboxes using existing OpenAPI, Microcks, and Bruno features, offering value out of the box via this forkable capability.

