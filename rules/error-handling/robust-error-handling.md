---
name: Robust Error Handling
globs: "**/*.{js,ts,py,go,java,rb,cs}"
alwaysApply: true
description: Guidelines for implementing comprehensive error handling strategies
---

You are an expert in error handling, defensive programming, and building resilient applications.

## Error Handling Principles

- Fail fast and fail clearly
- Provide actionable error messages
- Log errors with appropriate context
- Handle errors at the right level
- Never swallow errors silently

## Error Types and Handling

### JavaScript/TypeScript

```typescript
// Define custom error types
class ValidationError extends Error {
    constructor(message: string, public field?: string) {
        super(message);
        this.name = 'ValidationError';
    }
}

class NetworkError extends Error {
    constructor(message: string, public statusCode?: number) {
        super(message);
        this.name = 'NetworkError';
    }
}

// Comprehensive error handling
async function fetchUserData(userId: string): Promise<User> {
    try {
        if (!userId || !isValidUUID(userId)) {
            throw new ValidationError('Invalid user ID format', 'userId');
        }

        const response = await fetch(`/api/users/${userId}`);
        
        if (!response.ok) {
            throw new NetworkError(
                `Failed to fetch user: ${response.statusText}`,
                response.status
            );
        }

        const data = await response.json();
        return validateUser(data);
        
    } catch (error) {
        // Log with context
        logger.error('Failed to fetch user data', {
            userId,
            error: error instanceof Error ? error.message : 'Unknown error',
            stack: error instanceof Error ? error.stack : undefined,
        });
        
        // Re-throw or transform based on error type
        if (error instanceof ValidationError) {
            throw error; // Let caller handle validation errors
        }
        
        if (error instanceof NetworkError && error.statusCode === 404) {
            throw new Error('User not found');
        }
        
        // Wrap unexpected errors
        throw new Error('Unable to retrieve user data. Please try again later.');
    }
}
```

### Python

```python
# Custom exceptions
class BusinessLogicError(Exception):
    """Raised when business rules are violated"""
    pass

class DataIntegrityError(Exception):
    """Raised when data consistency is compromised"""
    pass

# Context managers for resource handling
from contextlib import contextmanager
import logging

@contextmanager
def database_transaction():
    conn = None
    try:
        conn = get_connection()
        conn.begin()
        yield conn
        conn.commit()
    except DatabaseError as e:
        if conn:
            conn.rollback()
        logging.error(f"Database transaction failed: {e}")
        raise DataIntegrityError("Failed to complete transaction") from e
    except Exception as e:
        if conn:
            conn.rollback()
        logging.error(f"Unexpected error in transaction: {e}")
        raise
    finally:
        if conn:
            conn.close()

# Graceful degradation
def get_user_preferences(user_id: str) -> dict:
    try:
        return fetch_from_cache(user_id)
    except CacheError:
        logging.warning(f"Cache miss for user {user_id}, falling back to database")
        try:
            return fetch_from_database(user_id)
        except DatabaseError:
            logging.error(f"Failed to fetch preferences for user {user_id}")
            return get_default_preferences()  # Graceful degradation
```

## Error Recovery Strategies

### Retry Logic

```typescript
async function resilientApiCall<T>(
    fn: () => Promise<T>,
    options: {
        maxRetries?: number;
        backoffMs?: number;
        retryableErrors?: (error: any) => boolean;
    } = {}
): Promise<T> {
    const { 
        maxRetries = 3, 
        backoffMs = 1000,
        retryableErrors = (error) => error.code === 'NETWORK_ERROR'
    } = options;
    
    let lastError: any;
    
    for (let attempt = 0; attempt <= maxRetries; attempt++) {
        try {
            return await fn();
        } catch (error) {
            lastError = error;
            
            if (attempt === maxRetries || !retryableErrors(error)) {
                throw error;
            }
            
            const delay = backoffMs * Math.pow(2, attempt);
            console.log(`Retry attempt ${attempt + 1} after ${delay}ms`);
            await new Promise(resolve => setTimeout(resolve, delay));
        }
    }
    
    throw lastError;
}
```

### Circuit Breaker Pattern

```javascript
class CircuitBreaker {
    constructor(
        private fn: Function,
        private threshold: number = 5,
        private timeout: number = 60000
    ) {
        this.failures = 0;
        this.nextAttempt = Date.now();
    }
    
    async call(...args: any[]) {
        if (this.failures >= this.threshold) {
            if (Date.now() < this.nextAttempt) {
                throw new Error('Circuit breaker is OPEN');
            }
            this.failures = 0;
        }
        
        try {
            const result = await this.fn(...args);
            this.failures = 0;
            return result;
        } catch (error) {
            this.failures++;
            if (this.failures >= this.threshold) {
                this.nextAttempt = Date.now() + this.timeout;
            }
            throw error;
        }
    }
}
```

## Best Practices

- Use try-catch-finally blocks appropriately
- Create error boundaries in UI components
- Implement global error handlers
- Validate early and fail fast
- Provide user-friendly error messages
- Log errors with sufficient context
- Monitor and alert on error patterns
- Test error scenarios explicitly