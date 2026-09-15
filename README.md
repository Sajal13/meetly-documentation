# Meetly Engineering Documentation

Production-oriented engineering blueprint for **Meetly**, an event discovery, event management, ticketing, payment, and administration platform.

## Source of truth
This documentation was generated from the supplied Meetly SRS. Requirements explicitly stated in the SRS are treated as requirements. Additional production-grade decisions are marked **Recommendation**.

## Applications
- `apps/web` — Next.js public/user web
- `apps/mobile` — React Native user mobile
- `apps/admin` — Next.js administration
- `apps/api` — NestJS central API

## Core architecture
Turborepo + pnpm + NestJS + PostgreSQL + TypeORM + Next.js + React Native.

Supporting infrastructure: Redis, BullMQ, Docker, object storage, CDN, payment providers, email/SMS/push providers.

> **Hard constraint:** PostgreSQL + TypeORM. Prisma is not used.

## Documentation map
1. [Product Requirements](01-product/product-requirements.md)
2. [Personas & User Stories](01-product/personas-user-stories.md)
3. [User Flows](02-flows/user-flows.md)
4. [System Architecture](03-architecture/system-architecture.md)
5. [Monorepo Architecture](03-architecture/monorepo.md)
6. [Backend Architecture](03-architecture/backend.md)
7. [Database Architecture](04-database/database-architecture.md)
8. [ERD](04-database/erd.md)
9. [Domain Models](04-database/domain-models.md)
10. [API Standards](05-api/api-standards.md)
11. [API Catalog](05-api/api-catalog.md)
12. [Security](06-security/security.md)
13. [Ticketing & Inventory](07-domains/ticketing.md)
14. [Payments](07-domains/payments.md)
15. [Notifications & Jobs](07-domains/notifications-jobs.md)
16. [Search, Time & SEO](08-platform/search-time-seo.md)
17. [Testing](09-quality/testing.md)
18. [DevOps & Deployment](10-devops/deployment.md)
19. [Analytics & Audit](08-platform/analytics-audit.md)
20. [Roadmap](11-delivery/roadmap.md)
21. [Task Backlog](11-delivery/task-backlog.md)
22. [ADRs](12-governance/adrs.md)
23. [Risks](12-governance/risk-register.md)
24. [Definition of Done](12-governance/definition-of-done.md)
25. [Implementation Blueprint](11-delivery/implementation-blueprint.md)

## Architecture principles
- Backend owns pricing, inventory, authorization, and payment truth.
- Payment webhooks are authoritative.
- Inventory-sensitive and financial operations are transactional.
- Ticket reservations expire and release inventory.
- Event requests and events remain separate entities.
- Admin auth is separate from user auth.
- Use permission-based RBAC.
- Store timestamps in UTC and retain event timezone.
- Start search with PostgreSQL.
- Store media in object storage, not PostgreSQL.
- Use background jobs for asynchronous work.
- Use database constraints as a second line of defense after application validation.
