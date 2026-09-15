# Risk Register

| Risk | Category | Probability | Impact | Severity | Mitigation |
|---|---|---:|---:|---:|---|
| Ticket overselling | Inventory | Medium | Critical | Critical | Transaction + row locking/atomic update + concurrency tests |
| Payment webhook failure | Payments | Medium | Critical | Critical | Retry, idempotency, reconciliation |
| Duplicate payment | Payments | Medium | Critical | Critical | Provider transaction uniqueness + idempotent state machine |
| OTP abuse | Security | High | High | High | Rate limits, attempt limits, cooldowns, hashing |
| Token theft | Security | Medium | Critical | High | Secure cookies, rotation, revocation, short access lifetime |
| Admin privilege escalation | Security | Low | Critical | High | Permission guards, least privilege, audit |
| Cancellation/refund complexity | Business | Medium | High | High | Explicit state machine + refund ledger/state |
| Database failure | Infrastructure | Low | Critical | High | Backups, monitoring, restore drills |
| Queue failure | Infrastructure | Medium | High | High | retries, DLQ, monitoring |
| Notification failure | Integration | Medium | Medium | Medium | async delivery, retry, provider abstraction |
| Storage failure | Infrastructure | Low | High | High | durable object storage + backups/versioning where appropriate |
| Ticket launch traffic spike | Performance | Medium | Critical | High | caching, DB tuning, queueing, load testing |
