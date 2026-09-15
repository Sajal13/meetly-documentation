# Payment State Diagram

```mermaid
stateDiagram-v2
    [*] --> PENDING
    PENDING --> PROCESSING
    PROCESSING --> SUCCESS
    PROCESSING --> FAILED
    PENDING --> CANCELLED
    SUCCESS --> REFUNDED
    SUCCESS --> PARTIALLY_REFUNDED
```
