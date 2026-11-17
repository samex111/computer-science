# System Design

## What problem does system design solve?

A useful feature must work for real users under constraints: traffic, latency, cost, reliability, security, data correctness, and changing requirements. System design is the process of choosing components and defining how they interact to meet those constraints.

## Why did this discipline emerge?

As software grew from small programs into services used by many people, local code decisions began affecting whole systems. Teams needed ways to reason about capacity, bottlenecks, failure, data ownership, and operations before and after deployment.

## How to approach a design

1. Clarify functional requirements: what must the system do?
2. Clarify non-functional requirements: scale, latency, availability, security, durability, and cost.
3. Estimate load and data size. State assumptions.
4. Define APIs and data models.
5. Draw the high-level architecture and request/data flows.
6. Identify bottlenecks and failure points.
7. Choose consistency, caching, partitioning, and communication patterns deliberately.
8. Explain trade-offs and how the system will be monitored and operated.

## Topics

- Requirements and capacity estimation
- API and schema design
- Monoliths, modular monoliths, and microservices
- Caching, CDNs, and load balancing
- Queues and background workers
- Database scaling and data partitioning
- Reliability, observability, and disaster recovery
- Security and access control
- Cost and operational trade-offs

**Practice:** design one familiar system at a time: URL shortener, file storage, notification service, chat, or a learning platform. Start simple. Add complexity only when a requirement or bottleneck justifies it.