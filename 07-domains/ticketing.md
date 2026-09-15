# Ticketing & Inventory

## Ticket types
Support VIP, Premium, Regular, and future ticket categories.

Core fields:
- name
- description
- price
- currency
- quantity
- soldQuantity
- maxPerOrder
- salesStart
- salesEnd
- status

## Reservation lifecycle
```text
SELECT
  ↓
RESERVE
  ↓
WAIT FOR PAYMENT
  ├── SUCCESS → SOLD
  └── FAILURE/TIMEOUT → RELEASE
```

## Overselling prevention
The inventory operation must be transactional.

Recommendation: use a PostgreSQL transaction with row-level locking (`SELECT ... FOR UPDATE`) or an atomic conditional update that guarantees the remaining quantity cannot become negative.

Do not:
1. read available inventory,
2. release the DB lock,
3. calculate locally,
4. update later.

That pattern is race-prone.

## Reservation expiration
BullMQ should periodically process expired reservations. Expiration must be idempotent because the same job may be retried.

## Ticket generation
Only after authoritative payment success:
`Order CONFIRMED → Generate Ticket → Generate Ticket Number → Generate QR → Notify User`.

## QR validation
QR data should not expose sensitive data unnecessarily. Recommendation: use a signed opaque ticket token rather than embedding mutable authorization data directly.

Validation must reject:
- unknown ticket
- cancelled ticket
- ticket for another event
- already checked-in ticket
- invalid signature/token

Check-in must be atomic to prevent two scanners from accepting the same ticket concurrently.
