# Diagrams

## Sequence Diagrams

>Version: 1.0.0

- The MVP version doesn't include any message queue application like Kafka.
- It is assumed that the diff engine will be taking a long time to process the data.
- Hence, the API gateway will be waiting for the diff engine to return the result.
- Resulting in longer response time.

```mermaid
sequenceDiagram
autonumber
  actor C as Client
  participant API as APIGateway 
  participant DE as Diff Engine
  C->>API : Enter Versioned Data
  activate API
  alt is Valid data
    API->>DE : Forward Byte Data & Metadata
    activate DE
  else
    API-->>C: Invalid Data Format 
  end
  DE-->>API : Return Diff Byte
  deactivate DE
  API-->>C : Return Diff JSON
  deactivate API
```
