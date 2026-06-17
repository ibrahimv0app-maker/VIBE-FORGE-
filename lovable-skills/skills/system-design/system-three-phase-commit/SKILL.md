---
name: system-three-phase-commit
description: Use when designing a 3PC for non-blocking commit. Always addresses scale, availability, consistency, latency, and cost. Key considerations: canCommit, preCommit, doCommit.
---

# System Design: Three Phase Commit

3pc for non-blocking commit.

## Requirements
### Functional
- List the core features the system must support

### Non-Functional
- Scale: users / requests / data
- Availability: % uptime
- Latency: p50, p99
- Consistency: strong / eventual
- Cost: budget

## Capacity Estimation
- Traffic (requests/sec)
- Storage (TB / PB)
- Bandwidth (Mbps)
- Memory (GB)

## High-Level Architecture
Describe the components and their interactions:
- Client → CDN → Load Balancer → API Gateway → Services → Data stores

## Detailed Component Design
For each component:
- Responsibility
- Technology choice
- Scaling strategy
- Failure modes

## Data Model
- Tables / collections
- Indexes
- Relationships
- Sharding keys

## API Design
- Endpoints
- Request / response shapes
- Authentication

## Scaling Strategy
- Vertical vs horizontal scaling
- Caching layers
- Database sharding
- Async processing

## Availability Strategy
- Multi-AZ / multi-region
- Failover
- Graceful degradation
- Disaster recovery

## Consistency Strategy
- Strong vs eventual
- Conflict resolution
- Idempotency

## Security
- Authentication / authorization
- Encryption (in transit, at rest)
- Rate limiting
- Audit logs

## Monitoring
- Metrics
- Logs
- Traces
- Alerts

## Cost Optimization
- Right-sizing
- Reserved capacity
- Spot instances
- Storage tiers

## Output Format
1. Requirements summary
2. Architecture diagram (textual)
3. Component design
4. Data model
5. Scaling / availability / consistency strategy

