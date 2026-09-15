# Meetly Implementation Blueprint

## Exact build order

1. Repository setup
2. Turborepo configuration
3. NestJS application
4. PostgreSQL + TypeORM
5. Database configuration
6. Base entities
7. Migrations
8. User authentication
9. Admin authentication
10. RBAC
11. Event domain
12. Ticketing
13. Orders
14. Payments
15. Tickets / QR
16. Notifications
17. Admin
18. Web
19. Mobile
20. Testing hardening
21. CI/CD
22. Production deployment

## Phase execution template

For every phase, create:
- Goal
- Prerequisites
- Deliverables
- Database changes
- API changes
- Frontend changes
- Tests
- Definition of Done
- Operational considerations

## Why this order
The API and database establish authoritative business rules before client implementations. Ticketing and payment depend on correct inventory/order foundations. Web, mobile, and admin should consume stable contracts rather than independently implementing business rules.

## First implementation milestone
A strong first vertical slice is:
`foundation → user auth → event read APIs → event discovery UI`.

Then add:
`ticket inventory → reservation → order → payment webhook → ticket → check-in`.

## Architecture guardrails
Before merging a feature, verify:
- Does it introduce a new source of truth unnecessarily?
- Is money calculated server-side?
- Is inventory protected transactionally?
- Is the operation idempotent where retries are possible?
- Is authorization enforced server-side?
- Is the state transition auditable where required?
- Are UTC timestamps and event timezone handled?
- Are API/database/tests/docs updated together?
