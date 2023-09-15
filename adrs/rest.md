# API Standard implementation

## Decision

- We aim for an API standard that makes it easy for us to build a system that provides better responsiveness and usability for our web and 
mobile apps, which supports simple CRUD operations and revolves more about data/resources.

## Pros:

- REST leverages the standard HTTP protocol, which is widely supported and well-understood and can map REST operations to familiar HTTP methods (simplicity)
- REST is often considered more interoperable because it uses standard HTTP methods and can be easily consumed by a wide range of client libraries and tools (interoperability)
- REST's stateless nature and resource-centric design make it well-suited for building scalable systems (scalability)
- Matured, tested easily adaptable (adaptability)

## Cons:

- REST primarily relies on a limited set of HTTP methods (GET, POST, PUT, DELETE, etc.) to perform actions on resources 
- Lower performance compared to alternatives (e.g. gRPC)
- Over-fetching data could be use a solution like GraphQL to tailor response for mobile users

## Justification:

- REST API take a more resource oriented approach and is an architectural style that favors scalability and interoperability and
therefore is dynamic in nature.  
- RPC-oriented solution are commonly used in communication between back-end systems and is less common when intercating with
front-end clients since commonly revolve around methods/action oriented API, and usually are statically defined ahead of time 
by some IDL. Therefore designing an API that is more data-centric is a better fit for REST architectural style 


## Other Considerations:

Alternative approaches such as GraphQL or gRPC may be worth considering. GraphQL APIs can be more complex to set up and 
maintain compared to REST APIs and may not always be the best fit for scenarios that require simple APIs, or where a 
request-response pattern aligns well with the problem domain. On the other hand gRPC also introduces additional complexity 
compared to simpler communication methods like REST, and relies on HTTP/2 as its underlying transport protocol which could
limit its usability, and as an RPC-oriented protocol can lead to tight coupling between client and server implementations.