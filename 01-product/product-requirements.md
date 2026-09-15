# Product Requirements

## Vision
Meetly provides a unified platform for discovering events, managing events, purchasing tickets, managing tickets/orders, and operating the platform through an administration dashboard.

## Product goals
- Make event discovery simple for guests and authenticated users.
- Provide reliable ticket reservation and purchase flows.
- Prevent inventory overselling.
- Provide administrators with controlled event, user, order, ticket, analytics, and audit operations.
- Support web and mobile clients through one user-facing API.
- Provide production-grade security and operational traceability.

## Target users
### Guest
Can browse, search, filter, and view public events without authentication.

### User
Can authenticate with OTP, purchase tickets, manage orders/tickets/profile, favorite events, request events, receive notifications, and review attended events.

### Admin
Operates events, users, ticketing, orders/refunds, categories, organizers, analytics, notifications, and audit logs.

### Super Admin
Has administrator-management and access-management capabilities in addition to Admin capabilities.

## Functional requirements
- Public event discovery.
- Event search/filter/sort/pagination.
- Event details and exact location.
- OTP-based user authentication.
- Admin email/password + MFA authentication.
- Event request submission and review.
- Event lifecycle and publication.
- Ticket types and inventory.
- Temporary reservations.
- Orders and order items.
- Payment provider abstraction and webhooks.
- Ticket generation and QR check-in.
- Favorites and reviews.
- Notifications.
- RBAC and permissions.
- File uploads through object storage.
- Analytics.
- Audit logging.

## Non-functional requirements
- Secure by default.
- Transactional consistency for money and inventory.
- Idempotent payment/webhook handling.
- Scalable asynchronous processing.
- Observable production services.
- API versioning under `/api/v1`.
- Testable domain services.
- UTC timestamps.
- Database constraints for critical invariants.

## Business rules
1. Frontend input is never authoritative for user identity, role, permissions, prices, totals, inventory, or payment success.
2. Backend calculates order prices.
3. Inventory is controlled by the backend.
4. Payment provider webhooks determine payment success.
5. Reservations expire and release inventory.
6. Event request approval is distinct from event publication.
7. Upcoming/ongoing/previous is derived from dates rather than duplicated status fields.
8. Ticket check-in is single-use.
9. Administrative actions with material impact are auditable.

## Assumptions
- PostgreSQL is the primary transactional database.
- Redis is available for queues/caching/rate limiting where appropriate.
- Object storage and CDN are available for media.
- Payment providers expose webhook mechanisms.
- Email/SMS/push providers can be integrated behind provider abstractions.

## Out of scope for the initial architecture
- Elasticsearch/OpenSearch before PostgreSQL search becomes insufficient.
- Unnecessary microservice decomposition.
- Prisma.
