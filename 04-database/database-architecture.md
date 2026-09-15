# Database Architecture

PostgreSQL + TypeORM is mandatory.

## Entity inventory
1. User
2. Admin
3. Role
4. Permission
5. RefreshToken
6. OTP
7. Category
8. Organizer
9. Location
10. EventRequest
11. Event
12. EventImage
13. TicketType
14. TicketReservation
15. Order
16. OrderItem
17. Payment
18. Ticket
19. TicketCheckIn
20. Favorite
21. Review
22. Notification
23. AuditLog

## Global rules
- UUID primary keys where appropriate.
- UTC timestamps.
- Foreign keys for referential integrity.
- Explicit indexes for common filters and joins.
- Composite unique constraints for invariants.
- JSONB only for genuinely variable metadata.
- Soft-delete only where business recovery/history requires it.
- Financial records should generally be retained rather than physically deleted.

## Critical constraints
`Favorite`: `UNIQUE(user_id, event_id)`.

Ticket inventory: mutations must occur under a transaction with appropriate locking/atomic conditions.

OTP: enforce one-time verification at application and data-state level.

Payment: provider transaction identifiers should have appropriate uniqueness/idempotency protection.

## Event lifecycle
EventRequest:
`PENDING → APPROVED | REJECTED | CANCELLED`

Event:
`DRAFT → SCHEDULED → ONGOING → COMPLETED`
or `→ CANCELLED`.

Publication is separate from lifecycle status.

Upcoming/ongoing/previous are derived:
- Upcoming: `startDate > now`
- Ongoing: `startDate <= now <= endDate`
- Previous: `endDate < now`
