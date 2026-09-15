# Entity Relationship Diagram

```mermaid
erDiagram
    USER ||--o{ ORDER : places
    USER ||--o{ TICKET : owns
    USER ||--o{ FAVORITE : saves
    USER ||--o{ REVIEW : writes
    USER ||--o{ NOTIFICATION : receives
    USER ||--o{ EVENT_REQUEST : submits

    ADMIN }o--o{ ROLE : assigned
    ROLE }o--o{ PERMISSION : grants
    ADMIN ||--o{ AUDIT_LOG : creates

    EVENT ||--|| LOCATION : occurs_at
    EVENT }o--|| ORGANIZER : organized_by
    EVENT }o--|| CATEGORY : categorized_as
    EVENT ||--o{ EVENT_IMAGE : contains
    EVENT ||--o{ TICKET_TYPE : offers
    EVENT ||--o{ ORDER : contains
    EVENT ||--o{ TICKET : issues
    EVENT ||--o{ FAVORITE : saved_as
    EVENT ||--o{ REVIEW : reviewed

    ORDER ||--o{ ORDER_ITEM : contains
    ORDER ||--o{ PAYMENT : has
    ORDER ||--o{ TICKET : produces

    TICKET_TYPE ||--o{ TICKET_RESERVATION : reserves
    TICKET_TYPE ||--o{ ORDER_ITEM : purchased_as
    TICKET_TYPE ||--o{ TICKET : issued_as

    TICKET ||--o{ TICKET_CHECK_IN : checked

    USER ||--o{ REFRESH_TOKEN : owns
```

## Cardinality notes
- A user can have many orders.
- An order can have many order items.
- An event can have many ticket types.
- A ticket type can appear in many orders.
- A user/event favorite pair is unique.
- Roles and permissions are many-to-many.
- Admins and roles are many-to-many.

Recommendation: use join tables for many-to-many relations and explicit indexes on all foreign-key columns used in filtering.
