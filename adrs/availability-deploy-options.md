# Availability Deploy Options

## Decision

We should employ load balancers internally to our services and also consider Global Server Load Balancing (GSLB)
and deploying our system into data-centers on separate regions to ensure high availability, global scalability, 
and improved user experience for end users

## Pros

- LBs provide fault tolerance and high availability (availability, fault tolerance)
- LBs can route requests to the appropriate instance (e.g. based on available resources considerations) that can handle them most efficiently (performance)
- LBs support horizontal scaling by allowing new servers or instances to be added to the pool (scalability)
- GSLB routes client requests to the closest data center to improve the availability and responsiveness of services (responsiveness)

## Cons

- Introduce an additional network hop, which can increase latency (performance)
- Load balancing services have ongoing usage or hardware costs (cost)
- GSLB configurations can be complex, particularly in large and distributed environments with multiple data centers

## Justification

Ultimately we need to consider supporting multiple disparate geographic distributed data centers in multiple
regions. Since availability is a core quality attribute for our system, we need to ensure that our system can cope
with failures increased traffic and be responsive to globally distributed end users.
