---
name: Rust Async Programming
globs: "**/*.rs"
alwaysApply: false
description: Guidelines for asynchronous programming patterns in Rust
---

# Rust Async Programming

## Async/Await Fundamentals

- Use `async fn` for functions that perform asynchronous operations
- Always `.await` async function calls within async contexts
- Prefer `tokio` runtime for most async applications
- Use `async move` closures when moving ownership into async blocks

## Task Management

- Spawn tasks with `tokio::spawn()` for concurrent execution
- Use `tokio::select!` for waiting on multiple async operations
- Implement proper cancellation with `CancellationToken`
- Avoid blocking operations in async functions

## Error Handling

- Use `Result` types consistently in async functions
- Prefer `?` operator for error propagation in async contexts
- Handle timeout scenarios with `tokio::time::timeout`
- Use `anyhow` for application-level async error handling

## Common Patterns

### Async Streams
- Use `tokio_stream` for working with async iterators
- Implement `Stream` trait for custom async data sources
- Use `StreamExt` methods for stream transformations

### Channels
- Use `tokio::sync::mpsc` for multi-producer, single-consumer channels
- Use `tokio::sync::broadcast` for broadcasting to multiple receivers
- Use `tokio::sync::oneshot` for single-value communication

## Performance Guidelines

- Minimize `.await` points to reduce context switching overhead
- Use `tokio::task::yield_now()` to yield control in CPU-intensive loops
- Profile async code with `tokio-console` for runtime insights
- Batch operations when possible to reduce async overhead

## Best Practices

- Keep async functions focused and composable
- Use `#[tokio::test]` for testing async functions
- Avoid mixing blocking and async code
- Use `spawn_blocking` for CPU-intensive or blocking operations
- Structure async code to avoid excessive nesting

## Common Anti-Patterns

- **Blocking in Async**: Never use `std::thread::sleep` in async functions
- **Excessive Spawning**: Don't spawn tasks for every small operation
- **Missing Error Handling**: Always handle errors in spawned tasks
- **Resource Leaks**: Ensure proper cleanup of async resources