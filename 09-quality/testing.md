# Testing Strategy

## Test levels

### Unit
At minimum:
- AuthService
- EventService
- EventRequestService
- OrderService
- PaymentService
- TicketService

Focus on business rules and state transitions.

### Integration
Cover:
- OTP verification
- event approval
- order creation
- payment webhook
- ticket generation
- ticket check-in
- inventory concurrency

### E2E
Critical path:
`Signup → Login → Browse Event → Select Ticket → Reserve → Order → Payment → Ticket → QR → Check-in`

## High-value concurrency tests
Simulate two or more buyers attempting to purchase the last available ticket. Assert:
- inventory never becomes negative
- at most the available number of tickets is sold
- failed reservations release correctly
- order/payment states remain consistent.

## Test data
Recommendation:
- isolated test database
- deterministic seed data
- provider mocks for payment/SMS/email
- controlled clock for expiry tests
- disposable object storage namespace

## CI quality gates
- typecheck
- lint
- unit tests
- integration tests
- E2E smoke suite
- migration validation
- build
