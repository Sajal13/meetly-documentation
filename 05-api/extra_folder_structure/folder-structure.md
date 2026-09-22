# NestJS API Folder Structure

```text
apps/api/
├── src/
│   ├── main.ts
│   ├── app.module.ts
│   │
│   ├── config/
│   │   ├── config.module.ts
│   │   ├── config.service.ts
│   │   ├── configuration.ts
│   │   ├── env.validation.ts
│   │   └── constants/
│   │       ├── app.constants.ts
│   │       ├── auth.constants.ts
│   │       └── cache.constants.ts
│   │
│   ├── database/
│   │   ├── database.module.ts
│   │   ├── database.config.ts
│   │   ├── migrations/
│   │   └── seeds/
│   │       ├── seed.ts
│   │       ├── admin.seed.ts
│   │       ├── role.seed.ts
│   │       └── permission.seed.ts
│   │
│   ├── common/
│   │   ├── decorators/
│   │   │   ├── current-user.decorator.ts
│   │   │   ├── current-admin.decorator.ts
│   │   │   ├── public.decorator.ts
│   │   │   ├── permissions.decorator.ts
│   │   │   └── roles.decorator.ts
│   │   ├── guards/
│   │   │   ├── user-auth.guard.ts
│   │   │   ├── admin-auth.guard.ts
│   │   │   ├── permissions.guard.ts
│   │   │   └── roles.guard.ts
│   │   ├── interceptors/
│   │   │   ├── logging.interceptor.ts
│   │   │   └── transform.interceptor.ts
│   │   ├── filters/http-exception.filter.ts
│   │   ├── pipes/validation.pipe.ts
│   │   ├── middleware/request-id.middleware.ts
│   │   ├── dto/
│   │   │   ├── pagination.dto.ts
│   │   │   └── api-response.dto.ts
│   │   ├── exceptions/
│   │   │   ├── business.exception.ts
│   │   │   └── error-codes.ts
│   │   ├── types/
│   │   │   ├── auth.types.ts
│   │   │   └── request.types.ts
│   │   └── utils/
│   │       ├── date.util.ts
│   │       ├── pagination.util.ts
│   │       └── crypto.util.ts
│   │
│   ├── auth/
│   │   ├── auth.module.ts
│   │   ├── user/
│   │   │   ├── user-auth.controller.ts
│   │   │   ├── user-auth.service.ts
│   │   │   ├── dto/
│   │   │   │   ├── request-otp.dto.ts
│   │   │   │   ├── verify-otp.dto.ts
│   │   │   │   ├── refresh-token.dto.ts
│   │   │   │   └── logout.dto.ts
│   │   │   ├── strategies/
│   │   │   │   ├── user-access.strategy.ts
│   │   │   │   └── user-refresh.strategy.ts
│   │   │   └── guards/
│   │   │       ├── user-access.guard.ts
│   │   │       └── user-refresh.guard.ts
│   │   ├── admin/
│   │   │   ├── admin-auth.controller.ts
│   │   │   ├── admin-auth.service.ts
│   │   │   ├── dto/
│   │   │   │   ├── admin-login.dto.ts
│   │   │   │   ├── admin-mfa.dto.ts
│   │   │   │   ├── refresh-admin-token.dto.ts
│   │   │   │   └── admin-logout.dto.ts
│   │   │   ├── strategies/
│   │   │   │   ├── admin-access.strategy.ts
│   │   │   │   └── admin-refresh.strategy.ts
│   │   │   └── guards/
│   │   │       ├── admin-access.guard.ts
│   │   │       └── admin-refresh.guard.ts
│   │   ├── otp/
│   │   │   ├── otp.service.ts
│   │   │   ├── otp.repository.ts
│   │   │   └── otp.entity.ts
│   │   ├── tokens/
│   │   │   ├── token.service.ts
│   │   │   ├── token.repository.ts
│   │   │   └── refresh-token.entity.ts
│   │   └── auth.types.ts
│   │
│   ├── users/
│   │   ├── users.module.ts
│   │   ├── users.controller.ts
│   │   ├── users.service.ts
│   │   ├── users.repository.ts
│   │   ├── entities/user.entity.ts
│   │   └── dto/
│   │       ├── update-user.dto.ts
│   │       ├── user-query.dto.ts
│   │       └── user-response.dto.ts
│   │
│   ├── admin/
│   │   ├── admin.module.ts
│   │   ├── admin.controller.ts
│   │   ├── admin.service.ts
│   │   ├── admin.repository.ts
│   │   ├── entities/admin.entity.ts
│   │   └── dto/
│   │       ├── create-admin.dto.ts
│   │       ├── update-admin.dto.ts
│   │       └── admin-query.dto.ts
│   │
│   ├── roles/
│   │   ├── roles.module.ts
│   │   ├── roles.controller.ts
│   │   ├── roles.service.ts
│   │   ├── roles.repository.ts
│   │   ├── entities/role.entity.ts
│   │   └── dto/
│   │       ├── create-role.dto.ts
│   │       ├── update-role.dto.ts
│   │       └── role-query.dto.ts
│   │
│   ├── permissions/
│   │   ├── permissions.module.ts
│   │   ├── permissions.controller.ts
│   │   ├── permissions.service.ts
│   │   ├── permissions.repository.ts
│   │   ├── entities/permission.entity.ts
│   │   └── dto/
│   │       ├── create-permission.dto.ts
│   │       └── update-permission.dto.ts
│   │
│   ├── events/
│   ├── event-requests/
│   ├── categories/
│   ├── organizers/
│   ├── locations/
│   ├── tickets/
│   ├── reservations/
│   ├── orders/
│   ├── payments/
│   ├── favorites/
│   ├── reviews/
│   ├── notifications/
│   ├── uploads/
│   └── audit-logs/
│
├── test/
│   ├── unit/
│   ├── integration/
│   └── e2e/
├── nest-cli.json
├── tsconfig.json
└── package.json
```

The remaining domain folders follow the module pattern in `domain-module-pattern.md`.
