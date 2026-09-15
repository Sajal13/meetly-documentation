# Notifications & Background Jobs

## Channels
- In-app
- Email
- SMS
- Push

## Notification events
- OTP
- Event request submitted
- Event approved
- Event rejected
- Order created
- Payment success
- Payment failure
- Ticket generated
- Event reminder
- Event cancelled
- Event updated
- Refund completed

## BullMQ jobs
- OTP delivery
- Email
- SMS
- Push notifications
- QR/ticket generation
- Reservation expiration
- Event reminders
- Payment webhook processing
- Reports

## Job reliability
Every job should define:
- deterministic input
- retry policy
- exponential backoff where appropriate
- maximum attempts
- idempotency behavior
- observability
- failure handling
- dead-letter strategy

A failed notification should not roll back a successfully completed purchase.
