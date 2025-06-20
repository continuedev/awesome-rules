---
name: TypeScript Type Safety
globs: "**/*.{ts,tsx}"
alwaysApply: false
description: Advanced type safety patterns and practices in TypeScript
---

# TypeScript Type Safety

## Strict Mode Configuration

- Enable all strict mode flags in `tsconfig.json`
- Use `noImplicitAny` to catch untyped variables
- Enable `strictNullChecks` for null safety
- Use `noImplicitReturns` for complete function returns
- Enable `noImplicitThis` for proper context typing

## Type Guards

- Implement custom type guards for runtime validation
- Use `typeof` guards for primitive type checking
- Use `instanceof` guards for class type checking
- Create assertion functions for type validation
- Use discriminated unions with type guards

## Null Safety

- Use optional chaining (`?.`) for safe property access
- Use nullish coalescing (`??`) for default values
- Prefer explicit null checks over implicit ones
- Use strict null checks in TypeScript configuration
- Implement proper null handling patterns

## Type Assertions

- Use type assertions only when necessary
- Prefer type guards over type assertions
- Document assumptions when using assertions
- Use `as const` for literal type inference
- Avoid double assertions unless absolutely necessary

## Advanced Type Patterns

### Branded Types
```typescript
type UserId = string & { __brand: 'UserId' };
type Email = string & { __brand: 'Email' };
```

### Exhaustiveness Checking
```typescript
function assertNever(x: never): never {
    throw new Error("Unexpected value: " + x);
}
```

### Safe Property Access
```typescript
function get<T, K extends keyof T>(obj: T, key: K): T[K] {
    return obj[key];
}
```

## Generic Constraints

- Use `extends` for generic type constraints
- Implement conditional types for complex constraints
- Use mapped types for object transformations
- Create utility types with proper constraints
- Use keyof constraints for safe property access

## Union and Intersection Types

- Use union types for value alternatives
- Use intersection types for type composition
- Implement discriminated unions for state management
- Use type narrowing with union types
- Create tagged unions for better type safety

## Template Literal Types

- Use template literal types for string manipulation
- Create type-safe string building patterns
- Implement path-based type systems
- Use template literals for API route typing
- Create compile-time string validation

## Error Prevention

- Use readonly modifiers for immutable data
- Implement proper encapsulation with private fields
- Use const assertions for immutable literals
- Create type-safe builders and factories
- Use phantom types for additional type safety

## Testing Type Safety

- Write type-level unit tests
- Use `@ts-expect-error` for negative test cases
- Test generic type constraints
- Verify type inference behavior
- Use type testing libraries for comprehensive coverage

## Common Anti-Patterns

- **Any Escape Hatches**: Avoid using `any` type
- **Unsafe Assertions**: Don't assert without validation
- **Implicit Any**: Always type function parameters
- **Mutation of Readonly**: Respect readonly contracts
- **Type Pollution**: Keep types focused and specific