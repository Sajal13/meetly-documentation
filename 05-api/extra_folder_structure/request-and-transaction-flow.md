# Request and Transaction Flow

## General request flow

```text
HTTP Request
 ↓
Controller
 ↓
Authentication / Authorization
 ↓
Service / Use Case
 ↓
Repository
 ↓
TypeORM
 ↓
PostgreSQL
```

External integrations use adapters/providers:

```text
Service / Use Case
 ↓
Provider / Adapter
 ↓
External System
```

## Ticket purchase example

```text
POST /api/v1/orders
 ↓
OrdersController
 ↓
OrdersService
 ├── EventsService
 ├── ReservationsService
 ├── TicketService
 └── PaymentsService
```

## Inventory-sensitive transaction

```text
BEGIN TRANSACTION

  validate event
  validate ticket type
  lock inventory
  create reservation
  create order

COMMIT
```

Critical transaction boundaries must be explicit rather than hidden across unrelated services.

## Payment boundary

External payment providers do not participate in the local PostgreSQL transaction.

```text
Create Order
 ↓
Create Payment
 ↓
External Payment Provider
 ↓
Verified Webhook
 ↓
Idempotent Payment Processing
 ↓
Order Confirmation
 ↓
Ticket Generation
```

Webhook processing must be idempotent so duplicate provider events do not create duplicate financial state changes or tickets.
