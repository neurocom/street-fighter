# Web and Mobile application Quantum

The following diagram describes the architecture for the Web and mobile application, as well as the communication with each of the required services
<p align="center">
<img width="1000" src="../assets/web-mobile-app.png">
</p>


## Components

### User Facing API Gateway
This component provides a single entry point for client applications and acts as a central point of control, management, and security between the users and the internal services that exposes. 

Specifically it is responsible for:
- Security
- Communicating with multiple services to perform actions triggered by the user
- Collecting user Analytics data 
- Pushing notifications to the web and mobile applications
- Rate Limiting and Throttling

### Authentication Handler
Handles the Authentication and Authorization of each user.

### Reservation API
Service that exposes an API interface for communicating with internal systems.
- Contains logic for performing CRUD operations on reservations and trips.
- Maintain a cache (In-Memory Database) for improved performance and latency.

## Related ADRs
- [ADR01 API-Gateway](../adrs/api-gateway.md)
- [ADR02 CDN](../adrs/cdn.md)
- [ADR03 Rest](../adrs/rest.md)
- [ADR04 Web and Native Mobile Apps](../adrs/web-mobile-application.md)