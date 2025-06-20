---
name: Lua Best Practices
globs: "**/*.lua"
alwaysApply: false
description: Best practices and coding standards for Lua development
---

# Lua Best Practices

## Code Style

- Use 2 spaces for indentation consistently
- Use `snake_case` for variables and functions
- Use `PascalCase` for modules and classes
- Keep line length under 80 characters when possible
- Use meaningful variable and function names

## Variable Declarations

- Prefer `local` variables over global variables
- Initialize variables at declaration when possible
- Use proper scoping to minimize variable lifetime
- Group related variable declarations together
- Avoid unused variables (use `_` for intentionally unused)

## Function Design

- Keep functions small and focused
- Use descriptive function names
- Document function parameters and return values
- Prefer multiple return values over complex data structures
- Use proper error handling patterns

## Table Usage

- Use tables for arrays, maps, and objects
- Initialize tables with appropriate size hints when known
- Use array-style indexing (1-based) for sequences
- Use string keys for associative arrays
- Prefer `ipairs` for arrays and `pairs` for maps

## Module Organization

- Use proper module patterns for code organization
- Return tables from modules for public interfaces
- Keep module internals private with local scope
- Use consistent module structure across codebase
- Document module APIs and usage examples

## Error Handling

- Use `pcall` and `xpcall` for protected calls
- Return error values as multiple return values
- Use `assert` for precondition checking
- Implement proper error messages with context
- Handle errors at appropriate levels

## Performance Guidelines

- Localize frequently used global functions
- Use table preallocation for known sizes
- Avoid string concatenation in loops
- Use appropriate data structures for use cases
- Profile code with LuaJIT profiling tools

## Memory Management

- Be aware of table references and garbage collection
- Use weak references when appropriate
- Avoid creating unnecessary temporary objects
- Clean up resources explicitly when needed
- Monitor memory usage in long-running applications

## String Handling

- Use string.format for complex string formatting
- Use table.concat for efficient string concatenation
- Use string methods appropriately for text processing
- Handle UTF-8 strings properly when needed
- Cache compiled patterns for regular expressions

## Common Patterns

- Use metatables for object-oriented programming
- Implement iterator patterns with coroutines
- Use closures for encapsulation and state management
- Create factory functions for object creation
- Use configuration tables for flexible APIs