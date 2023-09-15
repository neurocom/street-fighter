# Hybrid: Microservices - Event Driven Architecture 

## Decision: 

- Microservices organizes our business logic as a collection of loosely coupled fine-grained services promoting
Single Responsibility Principle (SRP), while event driven architecture favors higher scalability by ensuring
easy decoupling of services by exhanging messages asynchronously and promoting availability and fault tolerance.

## Pros:

- Services can be scaled horizontally easily, adding more instanses for targeted services utilizing cost-efficient infrastructure (scalability, elasticity)
- Better availability, since infrastructure setup can cope with delays on requests and achieve better fault isolation, isolate the problem and mitigate it (avaialbility, fault tolerance, loose coupling)
- Improving engineering velocity and organizational decoupling, since services can be implemented seperately have smaller codebase and also deployed in their own timeline (testability, deployability)

## Cons:

- Microservices introduce complexity in terms of managing multiple services, inter-service communication, and data consistency (performance,data consistency)
- Combining microservices and event-driven architecture can introduce a significant level of complexity to your system (over-engineering)

## Justification:

Microservices inherently embrace the idea of distributed systems, and event-driven architecture aligns well with the challenges and requirements of distributed systems.
Event-driven systems allow for asynchronous processing of tasks promoting loose coupling and availability. Also each microservice can be responsible for specific business functionality and therefore it is easier to evolve, modify, or replace individual microservices without affecting the entire system.