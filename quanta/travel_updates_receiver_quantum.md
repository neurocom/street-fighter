# Travel Updates Receiver Quantum

The following diagram describes the architecture for the Travel Updates Receiver sub-system, as well as the communication with each of the required services
<p style="text-align:center">
<img width="1000" src="../assets/travel-update-receiver.png">
</p>

## Components

### External Agency Interfaces

Independent component that implement multiple interfaces to interact with external APIS.
An abstraction layer to tackle integration scenarios where external systems use different protocols or data formats.
Essentially these components act as event sources for updates (e.g. cancellations,delays,updates) originated from external systems.

We can assume that Sabre and Apollo interfaces support push protocols for notifying external systems about updates.
We also consider that other external agency interfaces may support push or pull protocols for notifications.

### Event Filterer

Stateless component that handles filtering of events
- discards duplicate events (may receive same update from multiple external sources) using small in-memory cache
- filter events that are out of scope for our domain

### Reservation Manager

Stateful component that consumes curated events from downstream Event Filterer component and Reservation API
component.
- Utilizes a specialized DB that handles efficiently write-intensive workloads
- Emit events to a dedicated topic/queue containing updated reservation records

### Reservation Collector

Stateful component that consumes reservation record events
- Utilizes a specialized DB that is optimized for read-intensive workloads
- Groups reservations as Trips to be presented in the UIs/dashboard

### Notification Creator

Stateless module that curates reservation record events to produce a notification to the end user

### Notification Sender

Stateless module that handles the delivery of notification through multiple notification channels
(email,sms,mobile-app)

### Reservation API
Please refer to [Reservation API](user_interaction_quantum.md#reservation-api)

## Related ADRs
- [ADR01 External-API-Integration](../adrs/external-api-integration.md)
- [ADR02 CQRS](../adrs/cqrs.md)
- [ADR03 Message Broker](../adrs/message-broker.md)
- [ADR04 Specialized DBs](../adrs/specialized-dbs.md)