
# User Facing API Gateway

## Decision: 

- Establish single entry point for client applications, an API management service that sits between the client app and the collection of the internal services and allow us to make internal changes to our system, completely seamlessly and transparently to our API consumers.

## Pros:

- The API Gateway can abstract and encapsulate our internal APIs offering a single API and implementing a software architectural pattern called *API composition*. The client applications essentially interface one single service API and can execute a single call to the API Gateway, which would then route the request to all the appropriate services and return the response. (workflow, avoids tight coupling)
- Consolidate all security aspects of the system in one single place. Also performance benefits due to perhaps implementing SSL termination, and avoiding the overhead of authenticating each request with each service ( security, performance)
- Improved monitoring since all requests and traffic are handled by API Gateway enhancing our system's observability and traceability capabilities (observability)
- Protocol translation both for requests handled internally, but also for services exposed externally (e.g. consumption of analytics reports) so as to be flexible to integrate with other systems that may bring us additional revenue. (interoperability)

## Cons:

- API Gateway may become a Single Point of Failure
- Performance overhead due to another layer of abstraction and routing of requests
- Require to support and maintain an additional service 

## Justification:

We typically benefit more than we sacrifice in terms of performance, and Single Point of Failure concerns can be mitigated  by deploying multiple instance of the service behind a Load Balancer without incurring significant cost 

## Other Considerations:

We can also break the API Gateway into multiple services e.g. WebAPI gateway, Mobile gateway and third party gateway
(more specialized and lightweight), but this initially looks like over-engineering and adding development overhead.