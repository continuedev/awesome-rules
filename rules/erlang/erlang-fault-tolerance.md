---
name: Erlang Fault Tolerance
globs: "**/*.erl"
alwaysApply: false
description: Fault tolerance and reliability patterns in Erlang systems
---

# Erlang Fault Tolerance

## "Let It Crash" Philosophy

- Design processes to fail fast and recover quickly
- Use supervisors to restart failed processes
- Avoid defensive programming that masks errors
- Separate error handling from business logic
- Trust the supervision tree to handle failures

## Process Isolation

- Keep processes lightweight and focused
- Minimize shared state between processes
- Use message passing for process communication
- Isolate critical functionality in separate processes
- Design for independent process failures

## Supervision Strategies

### One-for-One
- Use when child processes are independent
- Restart only the failed process
- Suitable for worker processes

### One-for-All
- Use when child processes are interdependent
- Restart all children when one fails
- Suitable for tightly coupled systems

### Rest-for-One
- Restart failed process and all processes started after it
- Useful for ordered dependencies

## Error Recovery Patterns

- Implement exponential backoff for retries
- Use circuit breaker patterns for external dependencies
- Design graceful degradation mechanisms
- Implement proper resource cleanup
- Use timeouts to prevent hanging operations

## Monitoring and Observability

- Use process monitors to detect failures
- Implement proper logging with structured data
- Use telemetry for system metrics
- Monitor supervision tree health
- Track process restart frequencies

## Distributed Fault Tolerance

- Handle network partitions gracefully
- Use distributed supervisors appropriately
- Implement node failure detection
- Design for split-brain scenarios
- Use global registration carefully

## Common Anti-Patterns

- **Catch-All Error Handling**: Avoid catching all errors generically
- **Ignoring Supervisor Reports**: Monitor and act on supervisor logs
- **Complex Error Recovery**: Keep recovery logic simple
- **Synchronous Failures**: Avoid blocking operations in critical paths
- **Resource Leaks**: Ensure proper cleanup in all failure scenarios

## Testing Fault Tolerance

- Use fault injection for testing
- Test supervision tree behavior
- Verify error propagation patterns
- Test resource cleanup under failure
- Validate system behavior during cascading failures