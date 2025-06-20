---
name: Rust Ownership and Borrowing Guidelines
globs: "**/*.rs"
alwaysApply: false
description: Guidelines for effective ownership and borrowing patterns in Rust
---

# Rust Ownership and Borrowing Guidelines

## Ownership Principles

- **Single Owner**: Each value has exactly one owner at any given time
- **Move Semantics**: Values are moved by default, not copied
- **RAII**: Resources are automatically cleaned up when owners go out of scope
- **No Garbage Collector**: Memory management happens at compile time

## Borrowing Best Practices

### Immutable Borrowing
- Use `&T` for read-only access to data
- Multiple immutable borrows are allowed simultaneously
- Prefer immutable borrows when you don't need to modify data
- Pass `&str` instead of `String` for function parameters when possible

### Mutable Borrowing
- Use `&mut T` for exclusive write access
- Only one mutable borrow allowed at a time
- No other borrows (mutable or immutable) can coexist with a mutable borrow
- Keep mutable borrow scopes as small as possible

## Common Patterns

### Function Parameters
```rust
// Prefer borrowing over ownership
fn process_data(data: &[u8]) -> Result<(), Error> { /* ... */ }

// Use owned types when you need to store or transform
fn store_data(data: String) -> Result<(), Error> { /* ... */ }
```

### Return Values
- Return owned types when creating new data
- Return borrowed types when referencing existing data
- Use lifetime parameters when returning references

### Collections
- Use `Vec<T>` for owned collections
- Use `&[T]` for borrowed slices
- Use `HashMap<K, V>` for owned key-value pairs

## Lifetime Guidelines

### Explicit Lifetimes
- Use lifetime parameters when compiler cannot infer relationships
- Keep lifetime annotations minimal and clear
- Use descriptive lifetime names (`'a`, `'input`, `'output`)

### Lifetime Elision
- Rely on lifetime elision rules when possible
- Understand when explicit lifetimes are required
- Single input lifetime is assigned to all outputs

## Anti-Patterns to Avoid

- **Excessive Cloning**: Don't clone unnecessarily to avoid borrow checker
- **Reference Cycles**: Avoid `Rc<RefCell<T>>` cycles that cause memory leaks
- **Fighting the Borrow Checker**: Restructure code instead of using unsafe
- **Premature Arc/Mutex**: Use shared ownership only when necessary

## Advanced Patterns

### Interior Mutability
- Use `Cell<T>` for `Copy` types that need interior mutability
- Use `RefCell<T>` for runtime borrow checking
- Use `Mutex<T>` for thread-safe interior mutability

### Smart Pointers
- `Box<T>` for heap allocation and owned data
- `Rc<T>` for reference counting in single-threaded contexts
- `Arc<T>` for atomic reference counting in multi-threaded contexts

## Common Solutions

### Multiple Mutable References
- Split borrows using index access or separate methods
- Restructure data to avoid borrowing conflicts
- Use interior mutability patterns when appropriate

### Lifetime Issues
- Avoid returning references to local variables
- Use owned types when lifetime relationships are complex
- Consider using lifetime bounds on generic types

## Testing Ownership Patterns

- Write tests that verify memory safety properties
- Test edge cases with borrowing and lifetimes  
- Use `cargo miri` to catch undefined behavior
- Profile memory usage patterns in complex applications