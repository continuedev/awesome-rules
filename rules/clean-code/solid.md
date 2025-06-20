---
name: SOLID design principles
---

# SOLID Design Principles - Coding Assistant Guidelines

When generating, reviewing, or modifying code, follow these guidelines to ensure adherence to SOLID principles:

## 1. Single Responsibility Principle (SRP)

- Each class must have only one reason to change.
- Limit class scope to a single functional area or abstraction level.
- When a class exceeds 100-150 lines, consider if it has multiple responsibilities.
- Separate cross-cutting concerns (logging, validation, error handling) from business logic.
- Create dedicated classes for distinct operations like data access, business rules, and UI.
- Method names should clearly indicate their singular purpose.
- If a method description requires "and" or "or", it likely violates SRP.
- Prioritize composition over inheritance when combining behaviors.

## 2. Open/Closed Principle (OCP)

- Design classes to be extended without modification.
- Use abstract classes and interfaces to define stable contracts.
- Implement extension points for anticipated variations.
- Favor strategy patterns over conditional logic.
- Use configuration and dependency injection to support behavior changes.
- Avoid switch/if-else chains based on type checking.
- Provide hooks for customization in frameworks and libraries.
- Design with polymorphism as the primary mechanism for extending functionality.

## 3. Liskov Substitution Principle (LSP)

- Ensure derived classes are fully substitutable for their base classes.
- Maintain all invariants of the base class in derived classes.
- Never throw exceptions from methods that don't specify them in base classes.
- Don't strengthen preconditions in subclasses.
- Don't weaken postconditions in subclasses.
- Never override methods with implementations that do nothing or throw exceptions.
- Avoid type checking or downcasting, which may indicate LSP violations.
- Prefer composition over inheritance when complete substitutability can't be achieved.

## 4. Interface Segregation Principle (ISP)

- Create focused, minimal interfaces with cohesive methods.
- Split large interfaces into smaller, more specific ones.
- Design interfaces around client needs, not implementation convenience.
- Avoid "fat" interfaces that force clients to depend on methods they don't use.
- Use role interfaces that represent behaviors rather than object types.
- Implement multiple small interfaces rather than a single general-purpose one.
- Consider interface composition to build up complex behaviors.
- Remove any methods from interfaces that are only used by a subset of implementing classes.

## 5. Dependency Inversion Principle (DIP)

- High-level modules should depend on abstractions, not details.
- Make all dependencies explicit, ideally through constructor parameters.
- Use dependency injection to provide implementations.
- Program to interfaces, not concrete classes.
- Place abstractions in a separate package/namespace from implementations.
- Avoid direct instantiation of service classes with 'new' in business logic.
- Create abstraction boundaries at architectural layer transitions.
- Define interfaces owned by the client, not the implementation.

## Implementation Guidelines

- When starting a new class, explicitly identify its single responsibility.
- Document extension points and expected subclassing behavior.
- Write interface contracts with clear expectations and invariants.
- Question any class that depends on many concrete implementations.
- Use factories, dependency injection, or service locators to manage dependencies.
- Review inheritance hierarchies to ensure LSP compliance.
- Regularly refactor toward SOLID, especially when extending functionality.
- Use design patterns (Strategy, Decorator, Factory, Observer, etc.) to facilitate SOLID adherence.

## Warning Signs

- God classes that do "everything"
- Methods with boolean parameters that radically change behavior
- Deep inheritance hierarchies
- Classes that need to know about implementation details of their dependencies
- Circular dependencies between modules
- High coupling between unrelated components
- Classes that grow rapidly in size with new features
- Methods with many parameters
