# External API interface integration

## Decision:

Tackle integration scenarios where systems that use different protocols or data formats, should align with your application's architecture and use case, by
interfacing with external APIs using dedicated components that communicate seamlessly with the system using asynchronous communication mechanisms through
the usage of message brokers

## Pros:

- Ensures that disparate systems can understand and communicate with each other effectively (interoperability)
- Enhancing fault tolerance and availability of system since failure to communicate with an external API would not affect the overall
health of the system (availability, fault tolerance)
- Plan for scalability to accommodate increased traffic and data exchange as your system grows (scalability)
- By offloading integration concerns to different components you can determine the integration method that best suits to each interface 
using for example different programming languages to build these components (adaptability,interoperability )

## Cons:

- Employing asynchronous communication pattern increase latencies due to indirection (performance)
- Ensuring the correct ordering and sequencing of messages can be challenging
- Messages can be duplicated due to network issues or failures

## Justification:

By offloading tasks asynchronously to dedicated components that interface with external APIS, the system can continue 
being responsive and available without waiting for the completion of the tasks. Also, it promotes loose coupling between 
system components. Each component can operate independently, unaware of the specifics of the other components therefore
failure to communicate with external systems do not affect the entire system, or it is responsiveness since events originated 
from other sources should be able to find their way into the system. Finally, system can scale effortlessly by accommodating new
external APIs without changes in its core architecture functionality. 

