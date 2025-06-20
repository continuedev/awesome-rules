---
name: General Coding Standards
globs: "**/*.{js,ts,py,go,java,rb,cs}"
alwaysApply: true
description: Universal coding standards applicable across all programming languages
---

You are an expert in software engineering, clean code principles, and best practices.

## Naming Conventions

- Use descriptive and meaningful names
- Be consistent with naming patterns
- Avoid abbreviations and single letters (except loop counters)
- Use searchable names for constants
- Make the purpose clear from the name

### Examples

```javascript
// Good
const MAX_RETRY_ATTEMPTS = 3;
const userAuthenticationToken = generateToken();
function calculateCompoundInterest(principal, rate, time) {}

// Bad
const max = 3;
const tkn = generateToken();
function calc(p, r, t) {}
```

## Function Design

- Keep functions small and focused (single responsibility)
- Limit function parameters (ideally 3 or fewer)
- Use descriptive function names that indicate action
- Avoid side effects when possible
- Return early to reduce nesting

```python
# Good
def calculate_order_total(items: List[OrderItem]) -> Decimal:
    if not items:
        return Decimal('0.00')
    
    subtotal = sum(item.price * item.quantity for item in items)
    return apply_taxes(subtotal)

# Bad
def process(data):
    # 200 lines of mixed concerns
    # Multiple responsibilities
    # Hidden side effects
```

## Code Organization

- Group related functionality together
- Use consistent file structure
- Separate concerns into modules/classes
- Keep files focused and reasonably sized
- Use clear folder hierarchies

```
project/
├── src/
│   ├── controllers/
│   ├── services/
│   ├── models/
│   ├── utils/
│   └── config/
├── tests/
├── docs/
└── scripts/
```

## Error Prevention

- Validate inputs at boundaries
- Use type systems when available
- Handle edge cases explicitly
- Fail fast with clear messages
- Use defensive programming techniques

```typescript
function divideNumbers(dividend: number, divisor: number): number {
    if (divisor === 0) {
        throw new Error('Division by zero is not allowed');
    }
    if (!Number.isFinite(dividend) || !Number.isFinite(divisor)) {
        throw new Error('Invalid number provided');
    }
    return dividend / divisor;
}
```

## Code Readability

- Write code for humans to read
- Use consistent formatting
- Add whitespace for visual separation
- Limit line length (80-120 characters)
- Use meaningful variable names

## DRY Principle

- Don't Repeat Yourself
- Extract common functionality
- Use configuration over duplication
- Create reusable components
- Balance DRY with clarity

## SOLID Principles

- **Single Responsibility**: One reason to change
- **Open/Closed**: Open for extension, closed for modification
- **Liskov Substitution**: Subtypes must be substitutable
- **Interface Segregation**: Many specific interfaces
- **Dependency Inversion**: Depend on abstractions

## Best Practices

- Prefer composition over inheritance
- Write tests for your code
- Refactor regularly
- Use version control effectively
- Document architectural decisions