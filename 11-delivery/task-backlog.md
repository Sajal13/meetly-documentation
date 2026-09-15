# Development Task Backlog

Task properties:
- Task
- Epic
- Domain
- Application
- Priority
- Status
- Assignee
- Dependency
- Estimated effort
- Sprint
- Documentation
- API
- Database
- Testing

Statuses:
Backlog, Ready, In Progress, Blocked, Review, Testing, Done.

Priorities:
P0, P1, P2, P3.

Applications:
API, Web, Admin, Mobile, Infrastructure, Shared.

## Initial P0 tasks
| ID | Task | App | Priority | Dependency |
|---|---|---|---|---|
| MLY-001 | Initialize Turborepo workspace | Shared | P0 | — |
| MLY-002 | Configure pnpm workspace | Shared | P0 | MLY-001 |
| MLY-003 | Bootstrap NestJS API | API | P0 | MLY-001 |
| MLY-004 | Configure PostgreSQL + TypeORM | API | P0 | MLY-003 |
| MLY-005 | Add Docker local infrastructure | Infrastructure | P0 | MLY-004 |
| MLY-006 | Add configuration/env validation | API | P0 | MLY-003 |
| MLY-007 | Add global validation/error handling | API | P0 | MLY-006 |
| MLY-008 | Add Swagger/OpenAPI | API | P0 | MLY-007 |
| MLY-009 | Add testing foundation | API | P0 | MLY-003 |
| MLY-010 | Create base User/Admin entities | API | P0 | MLY-004 |
| MLY-011 | Create migrations | API | P0 | MLY-010 |
| MLY-012 | Implement user OTP auth | API | P0 | MLY-010 |
| MLY-013 | Implement refresh-token lifecycle | API | P0 | MLY-012 |
| MLY-014 | Implement admin auth + MFA | API | P0 | MLY-010 |
| MLY-015 | Implement permission-based RBAC | API | P0 | MLY-014 |
