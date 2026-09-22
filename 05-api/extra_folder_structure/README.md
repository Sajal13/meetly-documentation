# Meetly API Architecture

Recommended NestJS backend architecture for Meetly.

## Documents

- [Folder Structure](./folder-structure.md)
- [Authentication Architecture](./authentication.md)
- [Authorization and RBAC](./authorization.md)
- [Domain Module Pattern](./domain-module-pattern.md)
- [Request and Transaction Flow](./request-and-transaction-flow.md)

## Principles

- Controllers own HTTP contracts and validation boundaries.
- Services/use cases own business rules and orchestration.
- Repositories own persistence queries and transaction-aware access.
- Entities map persistence models.
- Providers/adapters isolate external integrations.
- User and admin authentication are separate flows.
- Shared authentication infrastructure is reusable where appropriate.
- Financial and inventory-sensitive operations have explicit transaction boundaries.
