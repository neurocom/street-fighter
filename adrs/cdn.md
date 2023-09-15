# Usage of CDN

## Decision:

CDNs have servers distributed globally, located in strategic places enabling content to be delivered quickly to users regardless 
of their geographic location. This allows for significant improvement in client's perceived performance. We favor push based
strategy to upload our content since we do not expect static content to change frequently


## Pros:

- CDN caching minimizes the time required to load  assets like images, stylesheets, scripts, resulting in faster page load times. (performance)
- CDNs can reduce bandwidth costs because they offload a significant portion of traffic from the origin server (cost) while employ efficient compression 
algorithms on cached content (mobile-friendly)
- CDNs are designed to handle high traffic loads and can easily scale to accommodate increased demand (scalability)

## Cons:

- Using a CDN service itself comes at a price (cost)
- Caching can sometimes become an issue leading to outdated content until the cache is purged (complexity)
- CDN means relinquishing some control over content delivery to a third-party provider.

## Justification:

CDN is a service used in conjuction with our system to improve user experience, lower maintenance costs on our part, and most 
importantly speed up content delivery to end users that are geographically distributed 
