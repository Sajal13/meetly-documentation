# Environment Contract

Recommendation: maintain a typed environment contract in the API.

## Categories
### Database
- `DATABASE_URL`

### Redis
- `REDIS_URL`

### Authentication
- access-token configuration
- refresh-token configuration
- OTP provider configuration
- admin MFA configuration

### Storage
- object-storage endpoint
- bucket
- credentials
- CDN base URL

### Payments
Provider-specific credentials should be isolated by adapter.

### Notifications
Email/SMS/push provider credentials.

## Rules
- Validate environment variables at application startup.
- Never commit secrets.
- Separate environment values by deployment environment.
- Prefer secret-manager injection in production.
