# Monitoring 

## Decision

Collect relevant metrics, such as response times, error rates, CPU and memory utilization, and custom application-specific metrics. 
Prometheus and Grafana form a widely adopted monitoring stack ideal for Microservices nad container-based deployed utilizing
service mesh infrastructure. Can also be enhanced with ecosystem  tools such as Grafana Loki (for logs capture and analysis) 
and Grafana Tempo (distributed tracing events). 

## Pros

- Open source and community-driven solution (cost)
- Prometheus provides a built-in alerting system that allows you to define alerting rules based on metrics and query expressions (observability)
- Prometheus has a wide range of integrations with popular systems and services, including cloud platforms, container orchestration tools (e.g., Kubernetes) (interoperability)
- Grafana is a highly customizable and user-friendly dashboard and visualization platform (usability)

## Cons

- Grafana or Prometheus does not provide long-term data storage (data retention)
- Need to provision infrastructure and resources for instrumentation (e.g. service mesh, exporters) (complexity)

## Justification

Should monitor Service Level Objectives (SLOs) and Service Level Indicators (SLIs) to measure system health and performance.
Monitoring is a critical aspect of managing a system, as it helps ensure the reliability, performance, and availability 
of individual microservices. It ensures that the mean-time-to-recovery (MTTR) a crucial metric for availability is minimized, 
since you can quickly react to failures. As a final note, continuously observing and collecting data about services is invaluable 
when diagnosing and debugging issues.

## Others Considerations

Managed services for monitoring, provided by cloud service providers or third-party vendors come with a cost, 
and the fees can scale with the volume of data ingested or the number of monitored resources.
ELK Stack (Elasticsearch, Logstash, Kibana) on the other hand is more log-oriented it may not be the best choice for comprehensive 
monitoring and observability of microservices and infrastructure.
