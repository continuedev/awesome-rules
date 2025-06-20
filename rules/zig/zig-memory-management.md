---
name: Zig Memory Management
globs: "**/*.zig"
alwaysApply: false
description: Memory management patterns and best practices in Zig
---

# Zig Memory Management

## Allocator Patterns

- Use `std.mem.Allocator` interface for all allocations
- Pass allocators as parameters to functions that allocate
- Choose appropriate allocator types for different scenarios
- Handle allocation failures explicitly with error handling
- Use allocator-aware data structures

## Allocator Types

### Page Allocator
- Use for simple applications and testing
- Direct system memory allocation
- No deallocation required
- Higher memory overhead

### General Purpose Allocator
- Use for debug builds and development
- Provides memory safety checks
- Detects memory leaks and use-after-free
- Higher runtime overhead

### Arena Allocator
- Use for temporary allocations
- Bulk deallocation at end of scope
- Excellent for request/response patterns
- No individual deallocation needed

### Fixed Buffer Allocator
- Use for stack-allocated buffers
- Predictable memory usage
- No heap allocation
- Limited by buffer size

## Memory Safety

- Always check allocation results
- Use `defer` for resource cleanup
- Avoid use-after-free with proper lifetime management
- Use optionals for potentially null pointers
- Validate pointer alignment assumptions

## Common Patterns

### RAII Pattern
```zig
defer allocator.free(memory);
```

### Error Handling with Allocation
```zig
const data = allocator.alloc(u8, size) catch |err| {
    // Handle allocation failure
    return err;
};
```

### Arena Pattern
```zig
var arena = std.heap.ArenaAllocator.init(allocator);
defer arena.deinit();
const arena_allocator = arena.allocator();
```

## Performance Considerations

- Minimize allocation frequency in hot paths
- Use stack allocation when possible
- Pool allocations for frequently used objects
- Consider allocation patterns for cache efficiency
- Profile memory usage patterns

## Testing Memory Management

- Use `std.testing.allocator` for tests
- Verify no memory leaks in test code
- Test allocation failure scenarios
- Use sanitizers for memory error detection
- Test with different allocator types

## Common Pitfalls

- **Forgetting to Free**: Always pair allocations with deallocations
- **Double Free**: Track allocation ownership carefully
- **Use After Free**: Validate pointer lifetimes
- **Allocation Failure Ignored**: Always handle allocation errors
- **Wrong Allocator**: Use appropriate allocator for the use case

## Best Practices

- Document allocation ownership in function signatures
- Use allocator-aware containers consistently
- Implement proper error propagation for allocation failures
- Profile memory usage in production scenarios
- Use debug allocators during development