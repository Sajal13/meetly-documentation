# Authorization and RBAC

Meetly uses backend-enforced permission-based RBAC.

```text
Admin
 ↓
Roles
 ↓
Permissions
```

Example permissions:

```text
events.read
events.create
events.update
events.delete
events.publish
events.cancel

users.read
users.update
users.block

orders.read
orders.refund

tickets.read
tickets.checkin

admins.manage
roles.manage
permissions.manage

analytics.read
audit_logs.read
```

Typical request flow:

```text
Request
 ↓
Admin Access Guard
 ↓
Authenticated Admin
 ↓
Permissions Guard
 ↓
Required Permission
 ↓
Controller
```

Conceptual usage:

```ts
@UseGuards(AdminAccessGuard, PermissionsGuard)
@Permissions('events.create')
@Post()
createEvent() {}
```

The frontend is never an authorization boundary. The API is authoritative.
