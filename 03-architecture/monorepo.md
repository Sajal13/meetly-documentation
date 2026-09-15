# Monorepo Architecture

```text
meetly/
├── apps/
│   ├── api/
│   ├── web/
│   ├── admin/
│   └── mobile/
├── packages/
│   ├── api-client/
│   ├── types/
│   ├── validation/
│   ├── config/
│   ├── eslint-config/
│   ├── typescript-config/
│   └── ui/
├── infrastructure/
│   └── docker/
├── package.json
├── pnpm-workspace.yaml
└── turbo.json
```

## Applications
### API
Owns authentication, authorization, business rules, persistence, payments, ticketing, notifications, uploads, analytics, and audit logging.

### Web
Public/user-facing Next.js application consuming the user API.

### Mobile
React Native user application consuming the same user API.

### Admin
Next.js internal administration application using admin authentication and admin authorization.

## Shared packages
- `api-client`: typed API client and transport helpers.
- `types`: shared contracts that are safe to share.
- `validation`: shared schemas where client/server reuse is beneficial.
- `config`: shared configuration primitives.
- `eslint-config`: repository linting rules.
- `typescript-config`: shared TS configuration.
- `ui`: reusable UI components appropriate for shared applications.

## Dependency rules
- Apps may depend on packages.
- Packages should not import from apps.
- Domain/business logic stays in API modules rather than shared UI packages.
- Secrets and server-only configuration never enter client packages.
