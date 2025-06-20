---
name: Check SOLID
alwaysApply: false
---

Please analyze the provided code and evaluate how well it adheres to each of the SOLID principles on a scale of 1-10, where:

1 = Completely violates the principle
10 = Perfectly implements the principle

For each principle, provide:

- Numerical rating (1-10)
- Brief justification for the rating
- Specific examples of violations (if any)
- Suggestions for improvement
- Positive aspects of the current design

## Single Responsibility Principle (SRP)

Rate how well each class/function has exactly one responsibility and one reason to change.
Consider:

- Does each component have a single, well-defined purpose?
- Are different concerns properly separated (UI, business logic, data access)?
- Would changes to one aspect of the system require modifications across multiple components?

## Open/Closed Principle (OCP)

Rate how well the code is open for extension but closed for modification.
Consider:

- Can new functionality be added without modifying existing code?
- Is there effective use of abstractions, interfaces, or inheritance?
- Are extension points well-defined and documented?
- Are concrete implementations replaceable without changes to client code?

## Liskov Substitution Principle (LSP)

Rate how well subtypes can be substituted for their base types without affecting program correctness.
Consider:

- Can derived classes be used anywhere their base classes are used?
- Do overridden methods maintain the same behavior guarantees?
- Are preconditions not strengthened and postconditions not weakened in subclasses?
- Are there any type checks that suggest LSP violations?

## Interface Segregation Principle (ISP)

Rate how well interfaces are client-specific rather than general-purpose.
Consider:

- Are interfaces focused and minimal?
- Do clients depend only on methods they actually use?
- Are there "fat" interfaces that should be split into smaller ones?
- Are there classes implementing methods they don't need?

## Dependency Inversion Principle (DIP)

Rate how well high-level modules depend on abstractions rather than concrete implementations.
Consider:

- Do components depend on abstractions rather than concrete classes?
- Is dependency injection or inversion of control used effectively?
- Are dependencies explicit rather than hidden?
- Can implementations be swapped without changing client code?

## Overall SOLID Score

Calculate an overall score (average of the five principles) and provide a summary of the major strengths and weaknesses.

Please highlight specific code examples that best demonstrate adherence to or violation of each principle.
