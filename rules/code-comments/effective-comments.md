---
name: Effective Code Comments
globs: "**/*.{js,ts,py,go,java,rb,cs}"
alwaysApply: false
description: Guidelines for writing meaningful and maintainable code comments
---

You are an expert in clean code practices, documentation, and code readability.

## When to Comment

- Explain WHY, not WHAT the code does
- Document complex business logic or algorithms
- Clarify non-obvious implementations
- Warn about potential gotchas or side effects
- Provide context for future maintainers

## Comment Types and Usage

### Good Comments

```javascript
// Using exponential backoff to avoid overwhelming the API
// during high traffic periods (see incident report #1234)
const delay = Math.min(1000 * Math.pow(2, retryCount), 30000);

// WORKAROUND: Chrome bug #123456 requires explicit height
// Remove when Chrome 120+ adoption reaches 95%
element.style.height = 'auto';

// Performance: Caching results reduces API calls by ~70%
// based on production metrics from 2023-Q4
const cachedResult = cache.get(key);
```

### Bad Comments

```javascript
// BAD: Obvious comment
// Increment counter by 1
counter++;

// BAD: Outdated comment
// Send email to user (actually sends SMS now)
await notificationService.send(user);

// BAD: Commented-out code without context
// user.setStatus('active');
// user.save();
```

## Documentation Comments

### JavaScript/TypeScript

```typescript
/**
 * Calculates compound interest with monthly contributions.
 * Uses the formula: A = P(1 + r/n)^(nt) + PMT × (((1 + r/n)^(nt) - 1) / (r/n))
 * 
 * @param principal - Initial investment amount
 * @param rate - Annual interest rate (as decimal, e.g., 0.05 for 5%)
 * @param time - Investment period in years
 * @param contribution - Monthly contribution amount
 * @returns Total value after the investment period
 * 
 * @example
 * // Calculate 10-year investment with 5% annual return
 * const total = calculateCompoundInterest(10000, 0.05, 10, 500);
 * console.log(total); // 96,859.57
 */
function calculateCompoundInterest(
  principal: number,
  rate: number,
  time: number,
  contribution: number
): number {
  // Implementation
}
```

### Python

```python
def process_transaction(transaction: Transaction) -> ProcessResult:
    """
    Process a financial transaction with fraud detection and validation.
    
    This method performs multiple checks before processing:
    1. Validates transaction format and required fields
    2. Checks against fraud detection rules
    3. Verifies account balance and limits
    4. Processes through payment gateway
    
    Args:
        transaction: Transaction object containing payment details
        
    Returns:
        ProcessResult with status and any error messages
        
    Raises:
        ValidationError: If transaction format is invalid
        FraudException: If transaction triggers fraud rules
        InsufficientFundsError: If account balance is too low
        
    Note:
        Transactions over $10,000 require additional verification
        per compliance policy FIN-2023-001.
    """
```

## TODO Comments

```python
# TODO(john): Implement retry logic for network failures
# TODO(security): Add rate limiting before v2.0 release
# FIXME: Handle edge case when user has multiple accounts
# HACK: Temporary fix until database migration completes
```

## Best Practices

- Keep comments concise and relevant
- Update comments when code changes
- Use consistent comment style across the codebase
- Avoid humor or cultural references that may not translate
- Review comments during code reviews