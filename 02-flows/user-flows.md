# User Flows

Each flow should be implemented as a contract between product behavior, database state, API operations, notifications, and security.

## 1. User registration/login

```mermaid
sequenceDiagram
    participant U as User
    participant A as API
    participant O as OTP Provider
    participant DB as PostgreSQL

    U->>A: request OTP
    A->>DB: create hashed OTP
    A->>O: deliver OTP
    U->>A: verify OTP
    A->>DB: verify one-time code
    A->>DB: create/login user
    A-->>U: access + refresh credentials
```

Failure cases: expired OTP, incorrect code, max attempts, resend cooldown, rate limit.

## 2. Browse events

```mermaid
flowchart LR
    G[Guest/User] --> E[Events API]
    E --> S[Search + Filters]
    S --> L[Event List]
    L --> D[Event Details]
```

Public endpoint: `GET /api/v1/events`.

## 3. Event request approval

```mermaid
flowchart LR
    U[User] --> R[Event Request]
    R --> A[Admin Review]
    A -->|Reject| X[Rejected]
    A -->|Approve| C[Create Event]
    C --> DR[Draft]
    DR --> P[Admin Publishes]
    P --> PU[Public Event]
```

Approval should be transactional so the request state and resulting event cannot diverge.

## 4. Ticket purchase

```mermaid
sequenceDiagram
    participant U as User
    participant API as API
    participant DB as PostgreSQL
    participant P as Payment Provider

    U->>API: create order
    API->>DB: transaction + lock inventory
    API->>DB: create reservation/order
    API-->>U: payment instructions
    U->>P: pay
    P->>API: webhook
    API->>API: verify + idempotency
    API->>DB: confirm payment/order
    API->>DB: generate tickets
    API-->>U: notification
```

Failure: payment failure/timeout releases reservation.

## 5. Event cancellation
Admin cancels event → stop sales → cancel eligible reservations → identify paid orders → initiate refunds → notify users → write audit log.

## 6. Ticket check-in
Staff/Admin scans QR → validate signature/token → locate ticket → validate event → validate ticket status → reject reused/cancelled ticket → atomically mark checked in.

## 7. Admin login
Email/password → credential validation → MFA/TOTP → issue admin session/tokens → dashboard.

## Cross-flow requirements
Every flow must document:
- Purpose
- Actors
- Preconditions
- Trigger
- Happy path
- Alternatives
- Failure cases
- DB mutations
- APIs
- Notifications
- Security controls
