# API Catalog

## Public Events

* `GET /api/v1/events`
* `GET /api/v1/events/:id`
* `GET /api/v1/events/slug/:slug`
* `GET /api/v1/categories`
* `GET /api/v1/organizers/:id`
* `GET /api/v1/events/:id/tickets`

## User

* `GET /api/v1/me`
* `PATCH /api/v1/me`
* `GET /api/v1/me/orders`
* `GET /api/v1/me/tickets`
* `GET /api/v1/me/favorites`
* `GET /api/v1/me/event-requests`

## Authentication

### User Authentication

User authentication is OTP-based.

* `POST /api/v1/auth/user/request-otp`
* `POST /api/v1/auth/user/verify-otp`
* `POST /api/v1/auth/user/refresh`
* `POST /api/v1/auth/user/logout`
* `GET /api/v1/auth/user/me`

The shared `OtpService` is responsible for OTP generation, hashing, expiry,
attempt tracking, and verification.

OTP delivery may use email or SMS depending on the configured authentication
channel.

### Admin Authentication

Admin authentication uses email/password followed by TOTP-based MFA.

* `POST /api/v1/auth/admin/login`
* `POST /api/v1/auth/admin/mfa/verify`
* `POST /api/v1/auth/admin/refresh`
* `POST /api/v1/auth/admin/logout`
* `GET /api/v1/auth/admin/me`

The admin authentication flow is:

1. Validate administrator email and password.
2. Create a pending MFA authentication state.
3. Validate the submitted TOTP code.
4. Issue authenticated access and refresh tokens.

Admin TOTP verification is handled by the dedicated `MfaService`.

Admin MFA does not use the shared `OtpService` and does not depend on email or
SMS delivery for the MFA code. TOTP codes are generated locally by the
administrator's authenticator application.

## Event Requests

* `POST /api/v1/event-requests`
* `GET /api/v1/event-requests`
* `GET /api/v1/event-requests/:id`
* `POST /api/v1/event-requests/:id/cancel`

## Favorites

* `POST /api/v1/events/:eventId/favorite`
* `DELETE /api/v1/events/:eventId/favorite`

## Orders

* `POST /api/v1/orders`
* `GET /api/v1/orders`
* `GET /api/v1/orders/:id`
* `POST /api/v1/orders/:id/cancel`

## Tickets

* `GET /api/v1/tickets`
* `GET /api/v1/tickets/:id`
* `GET /api/v1/tickets/:id/qr`

## Notifications

* `GET /api/v1/notifications`
* `POST /api/v1/notifications/:id/read`
* `POST /api/v1/notifications/read-all`

## Admin

### Dashboard

* `GET /api/v1/admin/dashboard`

### Users

* `GET /api/v1/admin/users`
* `GET /api/v1/admin/users/:id`
* `PATCH /api/v1/admin/users/:id`
* `POST /api/v1/admin/users/:id/block`
* `POST /api/v1/admin/users/:id/unblock`

### Events

* `GET /api/v1/admin/events`
* `GET /api/v1/admin/events/:id`
* `POST /api/v1/admin/events`
* `PATCH /api/v1/admin/events/:id`
* `DELETE /api/v1/admin/events/:id`
* `POST /api/v1/admin/events/:id/publish`
* `POST /api/v1/admin/events/:id/unpublish`
* `POST /api/v1/admin/events/:id/cancel`
* `POST /api/v1/admin/events/:id/duplicate`

### Event Requests

* `GET /api/v1/admin/event-requests`
* `GET /api/v1/admin/event-requests/:id`
* `POST /api/v1/admin/event-requests/:id/approve`
* `POST /api/v1/admin/event-requests/:id/reject`

### Event Tickets

* `GET /api/v1/admin/events/:eventId/tickets`
* `POST /api/v1/admin/events/:eventId/tickets`
* `PATCH /api/v1/admin/tickets/:id`
* `DELETE /api/v1/admin/tickets/:id`
* `POST /api/v1/admin/tickets/:id/check-in`

### Orders

* `GET /api/v1/admin/orders`
* `GET /api/v1/admin/orders/:id`
* `POST /api/v1/admin/orders/:id/refund`

### Administrators

* `GET /api/v1/admin/admins`
* `GET /api/v1/admin/admins/:id`
* `POST /api/v1/admin/admins`
* `PATCH /api/v1/admin/admins/:id`
* `POST /api/v1/admin/admins/:id/disable`
* `POST /api/v1/admin/admins/:id/enable`
* `DELETE /api/v1/admin/admins/:id`

### Roles

* `GET /api/v1/admin/roles`
* `GET /api/v1/admin/roles/:id`
* `POST /api/v1/admin/roles`
* `PATCH /api/v1/admin/roles/:id`
* `DELETE /api/v1/admin/roles/:id`

### Permissions

* `GET /api/v1/admin/permissions`

### Analytics

* `GET /api/v1/admin/analytics/overview`
* `GET /api/v1/admin/analytics/revenue`
* `GET /api/v1/admin/analytics/tickets`
* `GET /api/v1/admin/analytics/events`
* `GET /api/v1/admin/analytics/users`

### Audit Logs

* `GET /api/v1/admin/audit-logs`
* `GET /api/v1/admin/audit-logs/:id`

## Authentication Architecture

The authentication API uses two distinct authentication mechanisms.

### User Authentication

```text
User
  │
  ▼
POST /api/v1/auth/user/request-otp
  │
  ▼
OtpService
  │
  ├── Generate OTP
  ├── Hash OTP
  ├── Store OTP
  └── Deliver OTP
  │
  ▼
POST /api/v1/auth/user/verify-otp
  │
  ▼
OtpService
  │
  ├── Validate hash
  ├── Validate expiry
  ├── Validate attempts
  └── Mark OTP verified
  │
  ▼
TokenService
  │
  ├── Access Token
  └── Refresh Token
```

### Admin Authentication

```text
Administrator
  │
  ▼
POST /api/v1/auth/admin/login
  │
  ▼
AdminAuthService
  │
  ├── Validate email
  ├── Validate password
  └── Create pending MFA state
  │
  ▼
POST /api/v1/auth/admin/mfa/verify
  │
  ▼
MfaService
  │
  └── Validate TOTP
  │
  ▼
TokenService
  │
  ├── Access Token
  └── Refresh Token
```

## Route Conventions

Authentication routes intentionally use the following structure:

```text
/api/v1/auth/user/...
/api/v1/auth/admin/...
```

Administrative resource routes use:

```text
/api/v1/admin/...
```

The `/api/v1/admin/auth/...` route structure is not used.

This separation keeps authentication concerns under the `auth` namespace while
administrative resource operations remain under the `admin` namespace.
