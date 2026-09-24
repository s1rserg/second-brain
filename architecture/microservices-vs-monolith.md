# Why We Refused to Split into Microservices

## The Microservices Fallacy for Early Products
Most teams don't have a scalability problem; they have an organizational discipline problem.
- Splitting a 15,000-line codebase into 6 microservices when you have 4 engineers is self-sabotage. You trade simple in-memory function calls for distributed network latency, gRPC serialization overhead, and partial failure states.
- A modular monolith with clear folder boundaries and strict dependency rules gives you 90% of the isolation benefits with 0% of the DevOps nightmare.

## When Splitting Actually Makes Sense
I only consider decoupling a service if at least one of these two conditions is met:
1. **Dramatically asymmetrical scaling requirements:** E.g., an AI vector-embedding worker or PDF renderer that consumes 10x the CPU/RAM of the CRUD API.
2. **Autonomous deployment teams:** When multiple independent teams are stepping on each other’s git branches and blocking deployments.
