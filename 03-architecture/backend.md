# NestJS Backend Architecture

## Module map
- `auth`
- `users`
- `admin`
- `roles`
- `permissions`
- `events`
- `event-requests`
- `categories`
- `organizers`
- `locations`
- `tickets`
- `reservations`
- `orders`
- `payments`
- `favorites`
- `reviews`
- `notifications`
- `uploads`
- `audit-logs`
- `config`
- `database`
- `common`

## Domain-oriented structure

```text
events/
├── entities/
│   ├── event.entity.ts
│   └── event-image.entity.ts
├── dto/
│   ├── create-event.dto.ts
│   ├── update-event.dto.ts
│   └── event-query.dto.ts
├── events.controller.ts
├── events.service.ts
├── events.repository.ts
└── events.module.ts
```

Repeat this conceptual boundary for major domains.

## Layer responsibilities
Controller: HTTP contract, authentication context, validation boundary.

Service/use case: business rules and orchestration.

Repository: persistence queries and transaction-aware data access.

Entity: persistence mapping and database relationships.

Provider/adapter: external integrations such as payment, storage, email, SMS, or push.

## Transaction boundary
Financial and inventory-sensitive use cases must explicitly define their transaction boundary. Avoid hidden transactions spread across unrelated services.
