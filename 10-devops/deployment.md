# DevOps & Deployment

## Environments
- Local
- Development
- Staging
- Production

## Containerization
Docker should provide reproducible local and deployment environments.

## Production components
- Web application
- Admin application
- API
- PostgreSQL
- Redis
- BullMQ workers
- Object storage
- CDN
- external payment providers
- notification providers

## CI/CD
Pipeline recommendation:
1. Install dependencies with pnpm lockfile.
2. Lint.
3. Typecheck.
4. Unit tests.
5. Integration tests.
6. Build affected apps/packages.
7. Build container images where applicable.
8. Deploy to staging.
9. Run smoke tests.
10. Promote to production with approval.

## Database
- Run migrations explicitly.
- Back up production before risky schema operations.
- Test restore procedures.
- Never rely on `synchronize=true` in production.

## Observability
Track:
- API latency/error rate
- DB health
- Redis health
- queue depth/failures
- payment webhook failures
- reservation expiry failures
- notification failures
- application logs
- audit logs

## Reliability
Recommendation: define RPO/RTO targets before final infrastructure selection.
