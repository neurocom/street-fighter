# Reservation Orchestrator Quantum

The following diagram describes the architecture for creating and updating reservations triggerd by events from the [Travel Updates Receiver](travel_updates_receiver_quantum.md) and [User Agent](user_agent.md) Quanta, as well as managing trips
<p style="text-align:center">
<img width="1000" src="../assets/reservation-orchestrator.png">
</p>

## Components

### Reservation Manager

Stateful component that consumes curated events from downstream Event Filterer component and Reservation API
component.
- Utilizes a specialized DB that handles efficiently write-intensive workloads
- Emit events to a dedicated topic/queue containing updated reservation records

### Reservation Collector

Stateful component that consumes reservation record events
- Utilizes a specialized DB that is optimized for read-intensive workloads
- Groups reservations to Trips to be presented in the UIs/dashboard

### Reservation API
Service that exposes an API interface for communicating with the internal systems.
- Acts as a communication layer between the reservation orchestrator and the other Quanta
- Contains logic for performing CRUD operations on reservations and trips
- Maintain a cache (In-Memory Database) for improved performance and latency

### Notification Creator

Stateless module that curates reservation record events to produce a notification to the end user

### Notification Sender

Stateless module that handles the delivery of notification through multiple notification channels
(email,sms,mobile-app)

# Alternative 
## Related ADRs
- [ADR08 CQRS](../adrs/cqrs.md)
- [ADR09 Message Broker](../adrs/message-broker.md)
- [ADR10 Specialized DBs](../adrs/specialized-dbs.md)
