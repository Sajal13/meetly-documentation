# Architecture Decision Records

## ADR-001 — Turborepo monorepo
**Status:** Accepted

**Context:** Four applications and shared packages need coordinated tooling and types.

**Decision:** Use Turborepo.

**Consequence:** Shared build/lint/typecheck workflows and centralized dependency management.

## ADR-002 — pnpm
**Status:** Accepted

Use pnpm as the monorepo package manager.

## ADR-003 — PostgreSQL
**Status:** Accepted

Use PostgreSQL as the primary relational transactional database.

## ADR-004 — TypeORM
**Status:** Accepted

Use TypeORM. Prisma is explicitly excluded.

## ADR-005 — NestJS
**Status:** Accepted

Use NestJS for the central API with domain-oriented modules.

## ADR-006 — Separate EventRequest and Event
**Status:** Accepted

An event request represents a user proposal; an Event represents the platform-managed event. Keeping them separate avoids conflating approval workflow with publication lifecycle.

## ADR-007 — Permission-based RBAC
**Status:** Accepted

Use roles to aggregate permissions and enforce permissions at the API boundary.

## ADR-008 — Redis + BullMQ
**Status:** Accepted

Use Redis and BullMQ for asynchronous jobs and retryable background processing.

## ADR-009 — Object storage
**Status:** Accepted

Store large media in object storage and serve through a CDN.

## ADR-010 — Payment provider abstraction
**Status:** Accepted

Use a provider interface so bKash/Nagad/Stripe implementations remain replaceable.

## ADR-011 — PostgreSQL search initially
**Status:** Accepted

Start with PostgreSQL indexes/search. Introduce a dedicated search engine only when demonstrated requirements justify it.
