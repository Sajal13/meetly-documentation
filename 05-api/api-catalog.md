# API Catalog

## Public events
- `GET /api/v1/events`
- `GET /api/v1/events/:id`
- `GET /api/v1/events/slug/:slug`
- `GET /api/v1/categories`
- `GET /api/v1/organizers/:id`
- `GET /api/v1/events/:id/tickets`

## User
- `GET /api/v1/me`
- `PATCH /api/v1/me`
- `GET /api/v1/me/orders`
- `GET /api/v1/me/tickets`
- `GET /api/v1/me/favorites`
- `GET /api/v1/me/event-requests`

## Authentication
- `POST /api/v1/auth/request-otp`
- `POST /api/v1/auth/verify-otp`
- `POST /api/v1/auth/refresh`
- `POST /api/v1/auth/logout`
- `GET /api/v1/auth/me`

## Event requests
- `POST /api/v1/event-requests`
- `GET /api/v1/event-requests`
- `GET /api/v1/event-requests/:id`
- `POST /api/v1/event-requests/:id/cancel`

## Favorites
- `POST /api/v1/events/:eventId/favorite`
- `DELETE /api/v1/events/:eventId/favorite`

## Orders
- `POST /api/v1/orders`
- `GET /api/v1/orders`
- `GET /api/v1/orders/:id`
- `POST /api/v1/orders/:id/cancel`

## Tickets
- `GET /api/v1/tickets`
- `GET /api/v1/tickets/:id`
- `GET /api/v1/tickets/:id/qr`

## Notifications
- `GET /api/v1/notifications`
- `POST /api/v1/notifications/:id/read`
- `POST /api/v1/notifications/read-all`

## Admin
- `GET /api/v1/admin/dashboard`
- `GET /api/v1/admin/users`
- `GET /api/v1/admin/users/:id`
- `PATCH /api/v1/admin/users/:id`
- `POST /api/v1/admin/users/:id/block`
- `POST /api/v1/admin/users/:id/unblock`
- `GET /api/v1/admin/events`
- `GET /api/v1/admin/events/:id`
- `POST /api/v1/admin/events`
- `PATCH /api/v1/admin/events/:id`
- `DELETE /api/v1/admin/events/:id`
- `POST /api/v1/admin/events/:id/publish`
- `POST /api/v1/admin/events/:id/unpublish`
- `POST /api/v1/admin/events/:id/cancel`
- `POST /api/v1/admin/events/:id/duplicate`
- `GET /api/v1/admin/event-requests`
- `GET /api/v1/admin/event-requests/:id`
- `POST /api/v1/admin/event-requests/:id/approve`
- `POST /api/v1/admin/event-requests/:id/reject`
- `GET /api/v1/admin/events/:eventId/tickets`
- `POST /api/v1/admin/events/:eventId/tickets`
- `PATCH /api/v1/admin/tickets/:id`
- `DELETE /api/v1/admin/tickets/:id`
- `POST /api/v1/admin/tickets/:id/check-in`
- `GET /api/v1/admin/orders`
- `GET /api/v1/admin/orders/:id`
- `POST /api/v1/admin/orders/:id/refund`
- `GET /api/v1/admin/admins`
- `GET /api/v1/admin/admins/:id`
- `POST /api/v1/admin/admins`
- `PATCH /api/v1/admin/admins/:id`
- `POST /api/v1/admin/admins/:id/disable`
- `POST /api/v1/admin/admins/:id/enable`
- `DELETE /api/v1/admin/admins/:id`
- `GET /api/v1/admin/roles`
- `GET /api/v1/admin/roles/:id`
- `POST /api/v1/admin/roles`
- `PATCH /api/v1/admin/roles/:id`
- `DELETE /api/v1/admin/roles/:id`
- `GET /api/v1/admin/permissions`
- `GET /api/v1/admin/analytics/overview`
- `GET /api/v1/admin/analytics/revenue`
- `GET /api/v1/admin/analytics/tickets`
- `GET /api/v1/admin/analytics/events`
- `GET /api/v1/admin/analytics/users`
- `GET /api/v1/admin/audit-logs`
- `GET /api/v1/admin/audit-logs/:id`

## Admin authentication
- `POST /api/v1/admin/auth/login`
- `POST /api/v1/admin/auth/mfa/verify`
- `POST /api/v1/admin/auth/refresh`
- `POST /api/v1/admin/auth/logout`
- `GET /api/v1/admin/auth/me`
