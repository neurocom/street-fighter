# CQRS

## Decision:

Command Query Responsibility Segregation (CQRS) is an architectural pattern that separates 
the read and write sides of an application's data model. This pattern can provide several advantages, 
but it also introduces complexities and challenges. 

Command Query Responsibility Segregation (CQRS) is an architectural pattern that separates the read and write sides 
of an application's data model. 

## Pros:

- Optimizing a database with high load of Read and Update operations, by splitting command and query 
concerns.  This can lead to improved performance and responsiveness, as write operations do not 
compete with read operations for resources (Performance)

- You can allocate resources according to the specific needs of each side, improving performance 
and resource utilization (Scalability)

- One Write Model, N Read Models (Decoupling).The write side can use a different data model and schema from the read side, 
allowing for more flexibility in designing the data structures and relationships to meet the specific needs of each 
side especially for complex or frequently accessed data (extensibility)

## Cons :

- Implementing CQRS introduces additional complexity to the application. Developers need to 
manage the communication between the read and write sides (complexity). Ensuring data consistency 
between the read and write sides can be challenging (eventual consistency).

- Require a shift in mindset compared to more traditional approaches    
Building and maintaining two separate sides of the application can require more development 
effort and coordination. Changes to the data model may need to be reflected on both sides.
(development overhead)

- CQRS might be overkill for simpler applications that don't require the level of scalability and separation it offers. 
Applying CQRS to a straightforward CRUD application can lead to unnecessary complexity (over-engineering)

- Increased inherent cost either in terms of hardware or if a cloud provider is used utilization expense (cost)

## Justification:

Concurrent operations to the same records or tables contend with each other making all operations slow. Essentially
you can optimize a database only for one type of operation at the expense of the other. All write operations that 
change Reservations are handled by the Reservation Manager and all read operations are serviced by the Reservation Collector.
Essentially every time there is a change in data stored on Reservation Manager, the change is published as event to be
consumed by the Reservation Collector. Furthermore to avoid read own writes concerns we employ an In-Memory database
in upper layer that hides eventual consistency inherent to CQRS architecture. On the same note Reservation Collector 
can model entities efficiently for read purposes such as using trips as collections of reservations and utilizing
NoSQL document databases for fast retrieval.
