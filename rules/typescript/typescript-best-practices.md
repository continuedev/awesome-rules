---
name: TypeScript Best Practices
globs: "**/*.{ts,tsx}"
alwaysApply: false
description: Best practices and coding standards for TypeScript development
---

# TypeScript Best Practices

## Type Safety

- Enable strict mode in `tsconfig.json`
- Use explicit type annotations for function parameters and return types
- Avoid `any` type; use `unknown` for truly unknown types
- Use type guards for runtime type checking
- Prefer interfaces over type aliases for object shapes

## Interface Design

- Use descriptive interface names with consistent naming conventions
- Prefer composition over inheritance for interface design
- Use optional properties (`?`) appropriately
- Implement readonly properties for immutable data
- Use generic interfaces for reusable type definitions

## Function Types

- Use arrow functions for simple expressions
- Use function declarations for hoisted functions
- Type function parameters and return values explicitly
- Use generic functions for type-safe reusable code
- Implement proper function overloads when needed

## Error Handling

- Use `Result` or `Either` types for explicit error handling
- Implement custom error classes with proper typing
- Use discriminated unions for error states
- Handle async errors with proper Promise typing
- Use type guards for error type narrowing

## Utility Types

- Use built-in utility types (`Partial`, `Pick`, `Omit`, `Record`)
- Create custom utility types for domain-specific transformations
- Use conditional types for advanced type manipulation
- Implement mapped types for object transformations
- Use template literal types for string manipulation

## Module Organization

- Use ES6 modules with explicit imports and exports
- Organize related types in dedicated type files
- Use barrel exports for clean public APIs
- Implement proper module boundaries
- Use path mapping for clean import statements

## Generic Programming

- Use meaningful generic parameter names
- Add constraints to generic types when appropriate
- Use default generic parameters for better ergonomics
- Implement generic factories and builders
- Use generic types for container and utility functions

## Declaration Merging

- Use declaration merging for extending external libraries
- Implement ambient declarations for third-party modules
- Use module augmentation for extending existing modules
- Create proper type definitions for untyped dependencies
- Document declaration merging patterns clearly

## Performance Considerations

- Use type assertions sparingly and document assumptions
- Implement proper tree shaking with ES modules
- Use lazy loading for large type definitions
- Profile TypeScript compilation performance
- Optimize type checking with proper tsconfig settings

## Common Patterns

- Use discriminated unions for state management
- Implement builder patterns with fluent interfaces
- Use factory patterns with proper typing
- Create type-safe event systems
- Implement proper null safety patterns