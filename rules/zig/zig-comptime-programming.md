---
name: Zig Comptime Programming
globs: "**/*.zig"
alwaysApply: false
description: Comptime programming patterns and metaprogramming in Zig
---

# Zig Comptime Programming

## Comptime Fundamentals

- Use `comptime` keyword for compile-time evaluation
- Leverage comptime for type-level programming
- Use comptime parameters for generic programming
- Understand comptime vs runtime execution contexts
- Use `@TypeOf` for type introspection

## Generic Programming

- Create generic functions with comptime parameters
- Use `anytype` for flexible parameter types
- Implement generic data structures
- Use comptime type checking for constraints
- Create type-safe generic interfaces

## Type Introspection

- Use `@typeInfo` for runtime type information
- Implement type-based dispatch with comptime
- Use `@hasDecl` and `@hasField` for capability testing
- Create type-safe serialization with comptime
- Use `@field` for dynamic field access

## Code Generation

- Generate code with comptime evaluation
- Use comptime loops for repetitive patterns
- Create compile-time string manipulation
- Generate lookup tables at compile time
- Use comptime for configuration-driven code

## Metaprogramming Patterns

### Compile-Time Dispatch
```zig
fn dispatch(comptime T: type, value: T) void {
    switch (@typeInfo(T)) {
        .Int => handleInt(value),
        .Float => handleFloat(value),
        else => @compileError("Unsupported type"),
    }
}
```

### Generic Containers
```zig
fn Container(comptime T: type) type {
    return struct {
        items: []T,
        // Container implementation
    };
}
```

### Compile-Time Validation
```zig
fn validate(comptime value: anytype) void {
    if (@typeInfo(@TypeOf(value)) != .Struct) {
        @compileError("Expected struct type");
    }
}
```

## Best Practices

- Keep comptime code simple and readable
- Use compile-time errors for constraint validation
- Document comptime parameters clearly
- Avoid excessive comptime complexity
- Use comptime for performance-critical code paths

## Performance Considerations

- Comptime evaluation happens at compile time
- Use comptime to eliminate runtime overhead
- Generate optimal code with comptime specialization
- Cache comptime results when possible
- Profile compile times for complex comptime code

## Common Use Cases

- Generic data structures and algorithms
- Compile-time configuration and feature flags
- Type-safe serialization and deserialization
- Code generation from external data
- Compile-time string processing and validation

## Error Handling

- Use `@compileError` for compile-time failures
- Provide clear error messages for constraint violations
- Validate comptime parameters early
- Use type system to catch errors at compile time
- Document comptime constraints clearly

## Testing Comptime Code

- Test comptime functions with different type parameters
- Verify compile-time error conditions
- Test generated code correctness
- Use comptime assertions for validation
- Test with various input combinations