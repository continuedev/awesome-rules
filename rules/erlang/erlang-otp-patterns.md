---
name: Erlang OTP Patterns
globs: "**/*.erl"
alwaysApply: false
description: OTP design patterns and best practices for Erlang development
---

# Erlang OTP Patterns

## OTP Behaviors

- Use `gen_server` for stateful server processes
- Use `gen_statem` for complex state machines
- Use `supervisor` for fault-tolerant process trees
- Use `gen_event` for event handling systems

## GenServer Best Practices

- Keep state minimal and well-structured
- Use `handle_call` for synchronous operations
- Use `handle_cast` for asynchronous operations
- Implement proper timeout handling
- Always return appropriate tuples from callbacks

## Supervision Trees

- Design supervision trees with clear restart strategies
- Use `one_for_one` for independent child processes
- Use `one_for_all` when child processes are interdependent
- Set appropriate maximum restart frequencies
- Structure supervisors hierarchically

## Application Design

- Separate applications by domain boundaries
- Use application environment for configuration
- Implement proper application start/stop callbacks
- Use releases for deployment packaging
- Follow OTP application principles

## Error Handling

- Follow "let it crash" philosophy
- Use supervisors for error recovery
- Log errors appropriately with proper severity
- Handle expected errors gracefully
- Use `try-catch` sparingly, prefer pattern matching

## Process Communication

- Use message passing for inter-process communication
- Design clear message protocols
- Use registered names for well-known processes
- Implement proper message handling patterns
- Consider using `gen_statem` for complex protocols

## Performance Guidelines

- Avoid creating unnecessary processes
- Use ETS tables for shared data storage
- Implement proper backpressure mechanisms
- Profile with built-in tools like `fprof` and `eprof`
- Monitor process mailbox sizes

## Common Patterns

- Use process dictionaries sparingly
- Implement proper cleanup in terminate callbacks
- Use monitors and links appropriately
- Handle system messages in custom processes
- Implement proper hot code loading support