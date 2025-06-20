---
name: Erlang Concurrent Programming
globs: "**/*.erl"
alwaysApply: false
description: Concurrent programming patterns and best practices in Erlang
---

# Erlang Concurrent Programming

## Process Creation

- Use `spawn` for simple process creation
- Use `spawn_link` for linked processes
- Use `spawn_monitor` for monitored processes
- Keep processes lightweight and focused
- Avoid creating processes unnecessarily

## Message Passing

- Design clear message protocols
- Use pattern matching for message handling
- Implement proper message ordering when needed
- Handle unexpected messages gracefully
- Use selective receive for specific message patterns

## Process Synchronization

- Use message passing instead of locks
- Implement proper synchronization barriers
- Use `receive` with timeouts for non-blocking operations
- Design for eventual consistency
- Avoid shared mutable state

## Concurrency Patterns

### Producer-Consumer
- Use message queues for decoupling
- Implement backpressure mechanisms
- Handle slow consumers gracefully

### Worker Pools
- Create pools of worker processes
- Use load balancing for work distribution
- Implement proper worker lifecycle management

### Pipeline Processing
- Chain processes for data transformation
- Use message passing between pipeline stages
- Handle pipeline failures appropriately

## Process Communication

- Use registered names for well-known processes
- Implement proper process discovery mechanisms
- Use process groups for broadcasting
- Handle process termination notifications
- Design for location transparency

## Performance Considerations

- Monitor process mailbox sizes
- Avoid message queue buildup
- Use appropriate process priorities
- Profile concurrent systems thoroughly
- Implement proper flow control

## Distributed Concurrency

- Handle network delays and failures
- Use distributed process monitoring
- Implement proper node discovery
- Design for network partitions
- Use distributed algorithms appropriately

## Common Pitfalls

- **Mailbox Overflow**: Monitor and limit message queue sizes
- **Process Leaks**: Ensure proper process cleanup
- **Deadlocks**: Design communication patterns to avoid deadlocks
- **Race Conditions**: Use proper synchronization techniques
- **Hot Spots**: Distribute load across multiple processes

## Testing Concurrent Code

- Use property-based testing for concurrency
- Test with various timing scenarios
- Verify message ordering properties
- Test process lifecycle management
- Use tools like QuickCheck for concurrent testing