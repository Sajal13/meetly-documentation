# Analytics & Audit

## Admin analytics
### Overview
- total users
- new users
- total events
- published events
- tickets sold
- revenue
- orders
- conversion rate

### Content
- popular events
- popular categories

### Time series
- ticket sales over time

## Metric definitions
Each metric must have a written definition before implementation. Example:

**Revenue**
Recommendation: define whether this means gross successful payment amount, net after refunds, or another accounting measure. Do not let different dashboards calculate it differently.

## Audit logging
Track:
- approve event
- reject event
- create/update/delete event
- publish/unpublish
- cancel event
- refund order
- create/disable admin
- change roles
- change permissions
- block user

Audit fields:
`adminId`, `action`, `entityType`, `entityId`, `oldValue`, `newValue`, `ipAddress`, `userAgent`, `createdAt`.

Sensitive values should be redacted before persistence.
