---
name: Lua Performance Optimization
globs: "**/*.lua"
alwaysApply: false
description: Performance optimization techniques and patterns for Lua
---

# Lua Performance Optimization

## General Optimization Principles

- Profile before optimizing to identify bottlenecks
- Use LuaJIT for performance-critical applications
- Minimize memory allocations in hot paths
- Cache expensive computations when possible
- Use appropriate data structures for access patterns

## Variable Access Optimization

- Localize global variables and functions
- Use local variables instead of table lookups in loops
- Cache table field access in local variables
- Minimize upvalue access in nested functions
- Use numeric indices instead of string keys when possible

## Table Optimization

- Pre-allocate tables with known sizes
- Use array-style tables for sequential data
- Avoid mixed array/hash tables when possible
- Use `table.concat` for string concatenation
- Implement object pooling for frequently created tables

## Function Call Optimization

- Minimize function call overhead in tight loops
- Use tail call optimization where appropriate
- Inline small functions in performance-critical paths
- Cache function references in local variables
- Use direct table access instead of getter functions

## String Optimization

- Use `string.format` instead of concatenation
- Cache compiled string patterns
- Use `string.find` with plain text flag when possible
- Minimize string creation in loops
- Use rope data structures for large string operations

## Loop Optimization

- Use `ipairs` for array iteration
- Use `pairs` for hash table iteration
- Minimize work inside loop bodies
- Use break statements to exit loops early
- Unroll small loops when beneficial

## Memory Management

- Understand Lua's garbage collection behavior
- Use weak references to avoid memory leaks
- Minimize table churn in hot paths
- Use object pooling for frequently allocated objects
- Monitor memory usage with `collectgarbage`

## LuaJIT Specific Optimizations

- Keep hot code paths simple for JIT compilation
- Avoid table creation in compiled loops
- Use FFI for C data structure access
- Use bit operations library for numeric operations
- Profile with LuaJIT profiler to identify de-optimizations

## Coroutine Performance

- Use coroutines for cooperative multitasking
- Minimize coroutine creation overhead
- Use coroutine pools for frequently used coroutines
- Avoid deep coroutine nesting
- Use proper coroutine cleanup patterns

## IO Optimization

- Buffer IO operations appropriately
- Use `io.lines` for efficient file reading
- Minimize file handle creation
- Use binary mode for non-text files
- Implement asynchronous IO patterns when needed

## Profiling and Measurement

- Use built-in profiling tools
- Measure actual performance, not theoretical
- Profile with realistic data sets
- Use timing functions for micro-benchmarks
- Monitor memory allocation patterns

## Common Performance Anti-Patterns

- **Global Variable Access**: Avoid accessing globals in tight loops
- **Table Creation in Loops**: Don't create tables unnecessarily
- **String Concatenation**: Avoid `..` operator in loops
- **Unnecessary Function Calls**: Cache results of expensive operations
- **Mixed Table Types**: Don't mix array and hash access patterns

## Optimization Strategies

- Start with algorithmic improvements
- Optimize data structures before micro-optimizations
- Use appropriate algorithms for problem size
- Consider trade-offs between memory and CPU usage
- Benchmark different approaches with real data