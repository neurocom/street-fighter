        
# Usage of CDN

## Decision:

CDNs have servers distributed globally, which means that content can be served from a server geographically closer to the user.
CDNs have a distributed network of servers around the world, enabling content to be delivered quickly to users regardless of their geographic location

## Pros:

- CDN caching minimizes the time required to load  assets like images, stylesheets, scripts, resulting in faster page load times. (performance)

- CDNs can reduce bandwidth costs for website owners because they offload a significant portion 
of traffic from the origin server. This can result in cost savings, particularly for websites with heavy traffic (cost)

    Scalability:
        CDNs are designed to handle high traffic loads and can easily scale to accommodate increased demand,
 making them suitable for websites and applications with fluctuating traffic patterns.

    Security:
        CDNs often include security features such as Distributed Denial of Service (DDoS) protection, 
web application firewalls (WAF), and SSL/TLS encryption to help protect against various online threats.
 
## Cons:

    Costs:
        While CDNs can save money on bandwidth costs, using a CDN service itself comes at a price. 
Costs can vary based on the amount of data transferred and the level of service provided.

    Caching Challenges:
        Caching can sometimes lead to issues with dynamic content updates. 
If not configured correctly, users may see outdated content until the cache expires or is purged.

    Limited Control:
        Using a CDN means relinquishing some control over content delivery to a third-party provider. This can lead to challenges in customizing and fine-tuning the delivery of content.

## Justification:

