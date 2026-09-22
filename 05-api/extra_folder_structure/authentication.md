# Authentication Architecture

Meetly has separate user and administrator authentication entry points while reusing low-level authentication infrastructure.

```text
auth/
├── user/        # OTP-based user authentication
├── admin/       # Password + MFA administrator authentication
├── otp/         # Shared OTP infrastructure
└── tokens/      # Shared token infrastructure
```

## User authentication

```text
POST /api/v1/auth/user/request-otp
POST /api/v1/auth/user/verify-otp
POST /api/v1/auth/user/refresh
POST /api/v1/auth/user/logout
```

Flow:

```text
User
 ↓
UserAuthController
 ↓
UserAuthService
 ├── UserService
 ├── OtpService
 └── NotificationService
```

## Admin authentication

```text
POST /api/v1/auth/admin/login
POST /api/v1/auth/admin/mfa/verify
POST /api/v1/auth/admin/refresh
POST /api/v1/auth/admin/logout
```

Flow:

```text
Admin
 ↓
AdminAuthController
 ↓
AdminAuthService
 ├── AdminService
 ├── PasswordService
 └── MfaService
 ↓
Admin access token
```

## Domain ownership

Authentication does not own user/admin domain entities.

```text
auth/         → authentication
users/        → user domain
admin/        → administrator domain
roles/        → roles
permissions/  → permissions
```

Shared services can handle OTP generation/hashing/expiry, token rotation/revocation, password hashing, and MFA verification.
