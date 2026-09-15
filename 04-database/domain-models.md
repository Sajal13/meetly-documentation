# Domain Models

## User
Purpose: normal customer identity and account.

Core fields:
`id`, identity/contact fields, profile fields, status, created/updated timestamps.

Relations: orders, tickets, favorites, reviews, notifications, event requests.

## Admin
Purpose: internal administrative identity.

Relations: roles, audit logs.

## Role / Permission
Permission-based RBAC. Roles aggregate permissions.

## RefreshToken
Stores revocable/rotatable refresh-session state. Recommendation: store a hash rather than a reusable raw token.

## OTP
Fields from SRS:
`destination`, `codeHash`, `purpose`, `expiresAt`, `attempts`, `verifiedAt`, `createdAt`.

Purposes: LOGIN, SIGNUP, PHONE_VERIFICATION, EMAIL_VERIFICATION.

## EventRequest
User-submitted proposal. Must remain separate from Event.

## Event
Core published/draft event with organizer, location, category, images, ticket types, dates, timezone, lifecycle status, publication state, and unique SEO slug.

## Location
Fields include:
`name`, `address`, `addressLine1`, `addressLine2`, `city`, `state`, `country`, `postalCode`, `latitude`, `longitude`, `placeId`, `mapProvider`.

## TicketType
`name`, `description`, `price`, `currency`, `quantity`, `soldQuantity`, `maxPerOrder`, `salesStart`, `salesEnd`, `status`.

## TicketReservation
Temporary inventory hold with expiry. Recommendation: track reservation status and release timestamp explicitly.

## Order / OrderItem
Order stores authoritative totals and state. OrderItem snapshots unit price and quantity at purchase time.

## Payment
Provider abstraction fields:
`orderId`, `provider`, `transactionId`, `amount`, `currency`, `status`, `paymentMethod`, `paidAt`, `metadata`.

## Ticket
Issued only after successful payment confirmation. Includes ticket number, ownership, event, ticket type, QR representation, status, and check-in state.

## TicketCheckIn
Immutable/checkable audit record of a check-in operation.

## Favorite
Composite uniqueness on `(userId,eventId)`.

## Review
Should enforce business eligibility: user must have attended/held a valid ticket for the event.

## Notification
`userId`, `type`, `title`, `message`, `data`, `readAt`, `createdAt`.

## AuditLog
`adminId`, `action`, `entityType`, `entityId`, `oldValue`, `newValue`, `ipAddress`, `userAgent`, `createdAt`.
