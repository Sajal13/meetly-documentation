# Security Architecture

## Authentication
### User
OTP-based authentication with:
- hashed OTP
- five-minute expiry
- resend cooldown
- maximum attempts
- rate limiting
- one-time verification
- abuse prevention

### Admin
Separate email/password authentication followed by MFA/TOTP.

## Authorization
Use:
- `JwtAuthGuard`
- `PermissionsGuard`
- `@RequirePermissions(...)`

Permissions are checked server-side on every protected administrative action.

## Token security
Recommendation:
- short-lived access tokens
- rotating refresh tokens
- hashed refresh-token persistence
- token-family/session revocation
- secure, HttpOnly cookies for browser sessions where appropriate

## API hardening
- Helmet
- CORS
- ValidationPipe
- schema validation
- rate limiting
- brute-force protection
- secure headers
- controlled error messages
- secret management

## Payment security
- verify webhook signatures
- make webhook processing idempotent
- never accept frontend payment success as truth
- use transaction boundaries for state transitions

## Never trust frontend values
Never trust:
- userId
- role
- price
- total
- inventory
- payment status
- permissions

## Audit
Audit important administrative operations including event approval/rejection, event CRUD, publication, cancellation, refunds, admin management, role/permission changes, and user blocking.
