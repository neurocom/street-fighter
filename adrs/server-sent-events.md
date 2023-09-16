# Server-Sent Events (SSE)

## Decision

Usage of a Server-Sent Events based solution to push real-time data updates to the client utilizing unidirectional communication protocol 
over a single HTTP connection.

## Pros

- Significantly reduces the latency associated with traditional long-polling mechanisms (responsiveness)
- Connections are resilient to network interruptions (e.g., mobile apps where network connectivity is intermittent or unreliable) 
and can automatically reconnect when the connection is lost (mobile-friendly)
- Text-based protocol that relies on a simple event-stream format (Simplicity)

## Cons

- You need to use JavaScript and the EventSource API to establish SSE connections (development overhead)
- Large number of concurrent clients, managing these long-lived connections can consume server resources and limit scalability (cost,scalability)

## Justification

SSE is well-suited for specific use cases where unidirectional, server-initiated updates are needed,
and are  well-suited for event-driven architectures

## Other considerations

Usage of a Web-Sockets based solution utilizing bidirectional communication over a single, long-lived connection was considered, 
but the needs of our systems do not require bidirectional communication. Also web sockets are subject to require continuous network connectivity,
which is not always the case with travellers using their mobile apps.


