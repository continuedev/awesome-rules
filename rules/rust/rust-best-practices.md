---
name: Rust Best Practices
globs: "**/*.rs"
alwaysApply: false
description: Best practices and coding standards for Rust development
---

# Rust Best Practices

## Key Principles

- **Memory Safety**: Leverage Rust's ownership system to prevent memory-related bugs
- **Zero-Cost Abstractions**: Use high-level constructs without runtime overhead
- **Fearless Concurrency**: Write safe concurrent code using Rust's type system
- **Error Handling**: Use `Result` and `Option` types for robust error handling
- **Performance**: Write efficient code with predictable performance characteristics

## Coding Standards

- Use `cargo fmt` for consistent code formatting
- Run `cargo clippy` to catch common mistakes and improve code quality
- Write comprehensive tests with `cargo test`
- Use descriptive variable and function names
- Prefer immutable bindings by default (`let` over `let mut`)
- Use `snake_case` for variables and functions, `PascalCase` for types
- Keep functions small and focused on a single responsibility

## Ownership and Borrowing

- Understand the three rules of ownership: each value has one owner, only one owner at a time, value is dropped when owner goes out of scope
- Use borrowing (`&`) instead of moving when you don't need ownership
- Prefer borrowing over cloning for performance
- Use `Rc<RefCell<T>>` or `Arc<Mutex<T>>` sparingly for shared ownership
- Leverage lifetime annotations to express relationships between references

## Error Handling

- Use `Result<T, E>` for recoverable errors
- Use `Option<T>` for nullable values instead of null pointers
- Prefer `?` operator for error propagation
- Create custom error types using `thiserror` crate
- Use `anyhow` for application-level error handling
- Avoid `unwrap()` and `expect()` in production code

## Dependencies

- **Core Libraries**: `serde`, `tokio`, `clap`, `thiserror`, `anyhow`
- **Development**: `cargo-watch`, `cargo-audit`, `cargo-tarpaulin`
- **Testing**: Built-in test framework, `proptest` for property testing
- **Linting**: `clippy`, `rustfmt`

## Performance Guidelines

- Use `Vec<T>` for dynamic arrays, prefer `&[T]` for function parameters
- Use `String` for owned strings, `&str` for string slices
- Prefer iterators over explicit loops for better performance and readability
- Use `collect()` judiciously - consider streaming operations
- Profile with `cargo bench` and `perf` tools
- Avoid unnecessary allocations and clones

## Conventions

1. **Project Structure**: Use `src/lib.rs` for libraries, `src/main.rs` for binaries
2. **Module Organization**: One module per file, use `mod.rs` for module directories
3. **Documentation**: Write doc comments with `///` for public APIs
4. **Testing**: Place unit tests in the same file using `#[cfg(test)]`
5. **Integration Tests**: Place in `tests/` directory
6. **Examples**: Provide runnable examples in `examples/` directory
7. **Cargo.toml**: Keep dependencies minimal and well-documented
8. **Version Pinning**: Use semantic versioning and appropriate version constraints