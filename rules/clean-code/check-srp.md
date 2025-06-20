---
name: Check SRP
alwaysApply: false
---

Please analyze the provided code and rate it on a scale of 1-10 for how well it follows the Single Responsibility Principle (SRP), where:

1 = The code completely violates SRP, with many unrelated responsibilities mixed together
10 = The code perfectly follows SRP, with each component having exactly one well-defined responsibility

In your analysis, please consider:

1. Primary responsibility: Does each class/function have a single, well-defined purpose?
2. Cohesion: How closely related are the methods and properties within each class?
3. Reason to change: Are there multiple distinct reasons why the code might need to be modified?
4. Dependency relationships: Does the code mix different levels of abstraction or concerns?
5. Naming clarity: Do the names of classes/functions clearly indicate their single responsibility?

Please provide:

- Numerical rating (1-10)
- Brief justification for the rating
- Specific examples of SRP violations (if any)
- Suggestions for improving SRP adherence
- Any positive aspects of the current design

Rate more harshly if you find:

- Business logic mixed with UI code
- Data access mixed with business rules
- Multiple distinct operations handled by one method
- Classes that are trying to do "everything"
- Methods that modify the system in unrelated ways

Rate more favorably if you find:

- Clear separation of concerns
- Classes/functions with focused, singular purposes
- Well-defined boundaries between different responsibilities
- Logical grouping of related functionality
- Easy-to-test components due to their single responsibility
