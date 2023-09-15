# Message Broker

## Decision:

Usage of message broker as a central component of the event-driven architecture to capitalize its inherent 
features needed to build scalable, responsive, and loosely coupled systems that enable the asynchronous communication 
and coordination of events among different parts of a system

## Pros:

- Facilitates asynchronous communication between different parts of a system, declouping services (loose coupling, fault tolerance)
- Absorb traffic spikes (availability)
- Allows for easy scale of the system (scalability)
- Decouple the sender of a message (producer) from its receiver (consumer) (interoperability)

## Cons:

- Performance implications due to increased latency(indirection) in the communication of services (performance)- 
- Running and maintaining a message broker can be resource-intensive (cost)

## Justification:

Message brokers remain a valuable tool for building scalable, responsive, and loosely coupled systems. 
Rightfully considered an essential part of an architecture that favors availability and fault tolerance, since
their asynchronous nature means that even if one component becomes temporarily unavailable, the system can continue 
to process messages and events, improving overall availability.
With proper setup, redundancy planning are an integral part of an architecture that aims for high availability.