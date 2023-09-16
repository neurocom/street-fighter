# User Agent

The following diagram describes the architecture for the Web and mobile application, as well as the communication with each of the required services
<p style="text-align:center">
<img width="1000" src="../assets/user_agent.png">
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

### User Profile Manager
This component maintains specific information related to the user.
It manages: 
- Users personal details
- User specific configuration, such as locale (language, currency, etc.) and other preferences
- Privacy settings


## Related ADRs
- [ADR02 API-Gateway](../adrs/api-gateway.md)
- [ADR03 CDN](../adrs/cdn.md)
- [ADR04 Rest](../adrs/rest.md)
- [ADR05 Web and Native Mobile Apps](../adrs/web-mobile-application.md)
- [ADR06 Server Sent Events](../adrs/server-sent-events.md)
