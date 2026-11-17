# Distributed Systems

## What problem do distributed systems solve?

A single machine has limits in capacity, availability, geographic reach, and fault tolerance. A distributed system coordinates multiple independent machines so they can provide a service or manage data together.

## Why were they created?

As applications and organizations grew, one computer could no longer meet every requirement. Distributing work and data offered scale and resilience, but introduced new problems: machines fail independently, messages are delayed or lost, clocks disagree, and partial failure is normal.

## How to study a concept

Make assumptions explicit:
- What can fail?
- What communication guarantees exist?
- What consistency does the system promise?
- What happens during a network partition?
- How does the system recover?

Draw message timelines. They often reveal issues that component diagrams hide.

## Topics

- Partial failure, timeouts, retries, and backoff
- Replication and consistency models
- Leader election and consensus
- Quorums and membership
- Partitioning and rebalancing
- Idempotency and deduplication
- Message queues and event-driven systems
- Distributed transactions and sagas
- Observability and fault tolerance

**Labs:** build a small service with two instances. Simulate a timeout, duplicate message, process crash, and network partition. Record what each node believes happened. A timeout does not prove the remote operation did not execute.