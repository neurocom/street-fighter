# Deploy Options

## Decision

Combining architectural styles of microservices and event-driven apps with containers offers a flexible and efficient approach to developing, 
deploying, and managing apps for our architectural quanta. Some services which are not core to our system, are stateless and do not 
require high availability can also be deployed using serverless architecture.

## Pros

- Containers are lightweight and can be easily scaled up or down to accommodate changing workloads
- Can be created deployed quickly, and are highly scalable  (either container or serverless apps)
- Pay-as-you-go model can be cost-effective (serverless apps)
- Advantages in terms of portability, isolation
- Can be used as a part of a service mesh since containerized microservices application can be accompanied by a sidecar container that runs the service mesh proxy

## Cons

- Orchestrating containers in a production environment can be complex familiarity with tools like Kubernetes may be needed
- Container networking can be complex, especially in scenarios where containers need to communicate with each other or with external services

## Justification

Containers have become a popular technology for modern application deployment due to their advantages in terms of portability, 
isolation, and scalability. Adopting best practices, using container orchestration tools, and using them as part of a service mesh
allows for advanced features and capabilities. On the other hand Serverless deployments provide several advantages such as cost savings,
that make them an attractive choice for certain types of services that are stateless and do not require to be available continuously.
