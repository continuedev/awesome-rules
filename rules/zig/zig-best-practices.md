---
name: Zig Best Practices
globs: "**/*.zig"
alwaysApply: false
description: Best practices and coding standards for Zig development
---

# Zig Best Practices

## Core Principles

- **Explicit over Implicit**: Make intentions clear in code
- **No Hidden Control Flow**: Avoid hidden allocations and exceptions
- **Memory Safety**: Use Zig's safety features to prevent common bugs
- **Performance**: Write efficient code with predictable behavior
- **Simplicity**: Prefer simple, readable solutions

## Memory Management

- Use appropriate allocators for different use cases
- Prefer `std.heap.page_allocator` for testing
- Use `std.heap.GeneralPurposeAllocator` for debug builds
- Use arena allocators for temporary allocations
- Always handle allocation failures explicitly

## Error Handling

- Use `!` syntax for functions that can fail
- Prefer `try` keyword for error propagation
- Use `catch` for error handling and recovery
- Create custom error types for domain-specific errors
- Handle all possible error cases explicitly

## Type System

- Use comptime for type-level programming
- Prefer explicit types over `var` when clarity is important
- Use optionals (`?T`) instead of null pointers
- Leverage Zig's powerful struct and enum types
- Use tagged unions for variant types

## Comptime Programming

- Use comptime for compile-time code generation
- Prefer comptime over runtime when possible
- Use `@This()` for self-referential types
- Implement generic data structures with comptime
- Use comptime reflection judiciously

## Performance Guidelines

- Profile code with built-in benchmarking tools
- Use `@inlineCall` and `@noInlineCall` strategically
- Prefer stack allocation over heap allocation
- Use SIMD operations for data-parallel code
- Optimize hot paths with compiler intrinsics

## Code Organization

- Use `const` for compile-time constants
- Organize code into logical modules
- Use `pub` keyword for public interfaces
- Keep functions focused and small
- Use meaningful names for variables and functions

## Testing

- Write tests using `std.testing`
- Use `zig test` for running test suites
- Test error conditions explicitly
- Use fuzzing for robust testing
- Write property-based tests when appropriate

## Common Patterns

- Use defer for resource cleanup
- Prefer slices over arrays for function parameters
- Use `std.ArrayList` for dynamic arrays
- Implement proper iterator patterns
- Use `std.HashMap` for key-value storage

## Safety Guidelines

- Enable safety checks in debug builds
- Use `@intCast` for explicit integer conversions
- Handle integer overflow explicitly
- Use `@ptrCast` carefully and document assumptions
- Validate assumptions with `std.debug.assert`