# Multiple Specialized Databases for Microservices

## Decision

Polyglot persistence architecture, can provide a well-rounded solution that leverages the strengths of databases 
designed and optimized for specific use cases, data models, and workloads. Since microservices are fine-grained,
loosely coupled and can be deployed independently there are a perfect fit for such an approach

## Pros

- Specialized databases are often tailored for specific performance requirements (performance)
- More suitable for high-traffic or data-intensive applications (responsiveness,elasticity)
- Easier to scale since individual databases don’t impact other services in the context of microservices (scalability)

## Cons

- Maintaining multiple databases, and their replicas introduces significant costs (cost, feasibility)
- Data duplication is possible across different microservices and keeping duplicated data in sync could mean eventual consistency models (data consistency)
- Lack of ACID Transactions (data integrity)

## Justification

Adopting microservices architectural style we feel that the specialized database per service should be the preferred approach,
since specialized databases excel in their targeted domains. Therefore, we should target databases that fit the use cases, data requirements, 
and performance considerations of each microservice.

## Other Considerations

Use general purpose relational databases instead of targeted specialized NoSQL databases. Following our architectural principles
that promote availability, scalability but also taking and to consideration performance and general responsiveness of the system
as stated in requirements we concluded that the correct approach was to use specialized databases. On the same note some architectural 
decisions like using CQRS software architectural pattern that separates the responsibility for handling read operations (queries) 
from write operations (commands)  made prohibitive the use of general purpose relational databases for specific workloads.