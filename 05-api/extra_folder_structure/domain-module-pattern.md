# Domain Module Pattern

Major business domains use a consistent structure.

```text
events/
├── entities/
│   ├── event.entity.ts
│   └── event-image.entity.ts
├── dto/
│   ├── create-event.dto.ts
│   ├── update-event.dto.ts
│   └── event-query.dto.ts
├── enums/
│   └── event-status.enum.ts
├── types/
│   └── event.types.ts
├── events.controller.ts
├── events.service.ts
├── events.repository.ts
└── events.module.ts
```

## Layer responsibilities

### Controller

HTTP routes, request/response contracts, authentication context, and validation boundary.

### Service / Use Case

Business rules, domain orchestration, cross-domain coordination, and explicit transaction boundaries where required.

### Repository

Persistence queries, TypeORM access, complex queries, and transaction-aware data access.

### Entity

TypeORM persistence mapping, columns, relations, and database representation.

### Provider / Adapter

External integrations such as payments, object storage, email, SMS, and push notifications.

## Complex domains

For payments or other highly complex domains, a use-case structure may be introduced:

```text
payments/
├── controllers/
│   ├── payments.controller.ts
│   └── payment-webhook.controller.ts
├── use-cases/
│   ├── create-payment.use-case.ts
│   ├── verify-payment.use-case.ts
│   ├── process-webhook.use-case.ts
│   └── refund-payment.use-case.ts
├── entities/
│   └── payment.entity.ts
├── repositories/
│   ├── payment.repository.ts
│   └── payment.repository.interface.ts
├── providers/
│   ├── payment-provider.interface.ts
│   ├── stripe/
│   ├── bkash/
│   └── nagad/
├── dto/
└── types/
```

Do not introduce this level of ceremony to every module without a complexity reason.
