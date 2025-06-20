---
name: AI Assistant Guidelines
globs: "**/*"
alwaysApply: true
description: Guidelines for working effectively with AI coding assistants
---

You are working with an AI coding assistant. Follow these guidelines to maximize productivity and code quality.

## Code Context and Structure

- Maintain clear, self-documenting code structure
- Use descriptive file and folder names
- Keep related functionality grouped together
- Add README files to complex directories
- Include type definitions and interfaces

## Documentation for AI Understanding

### File Headers

```typescript
/**
 * @file UserService.ts
 * @description Handles user authentication, profile management, and permissions
 * @dependencies Express, bcrypt, jsonwebtoken
 * @relatedFiles ./UserModel.ts, ./auth/AuthMiddleware.ts
 */
```

### Function Documentation

```python
def calculate_shipping_cost(
    weight: float,
    distance: float,
    shipping_type: str = "standard"
) -> Decimal:
    """
    Calculate shipping cost based on weight, distance, and shipping type.
    
    Business Rules:
    - Standard shipping: $0.50/lb + $0.10/mile
    - Express shipping: $1.00/lb + $0.20/mile
    - Overnight: Flat $25 + standard rates
    - Free shipping over $100 order value (standard only)
    
    Args:
        weight: Package weight in pounds
        distance: Shipping distance in miles
        shipping_type: One of "standard", "express", "overnight"
    
    Returns:
        Shipping cost as Decimal
    
    Raises:
        ValueError: If shipping_type is invalid or weight/distance < 0
    """
```

## Project Structure Best Practices

### Clear Architecture

```
project/
├── README.md          # Project overview and setup
├── ARCHITECTURE.md    # System design decisions
├── src/
│   ├── api/          # API endpoints
│   ├── services/     # Business logic
│   ├── models/       # Data models
│   ├── utils/        # Shared utilities
│   └── config/       # Configuration
├── tests/            # Mirroring src structure
└── docs/             # Additional documentation
```

### Configuration Documentation

```javascript
// config/database.js
/**
 * Database configuration
 * 
 * Environment Variables:
 * - DB_HOST: Database host (default: localhost)
 * - DB_PORT: Database port (default: 5432)
 * - DB_NAME: Database name (required)
 * - DB_USER: Database user (required)
 * - DB_PASSWORD: Database password (required)
 * 
 * Connection Pool Settings:
 * - max: 20 connections
 * - idleTimeoutMillis: 30 seconds
 * - connectionTimeoutMillis: 2 seconds
 */
export const dbConfig = {
    host: process.env.DB_HOST || 'localhost',
    port: parseInt(process.env.DB_PORT || '5432'),
    database: process.env.DB_NAME,
    user: process.env.DB_USER,
    password: process.env.DB_PASSWORD,
    max: 20,
    idleTimeoutMillis: 30000,
    connectionTimeoutMillis: 2000
};
```

## Code Patterns for AI Assistance

### Consistent Naming Conventions

```typescript
// Use clear, predictable naming patterns
interface UserDto {
    id: string;
    email: string;
    name: string;
}

class UserService {
    async createUser(data: CreateUserDto): Promise<UserDto> {}
    async getUserById(id: string): Promise<UserDto | null> {}
    async updateUser(id: string, data: UpdateUserDto): Promise<UserDto> {}
    async deleteUser(id: string): Promise<void> {}
}

// Event naming pattern
enum UserEvents {
    USER_CREATED = 'user.created',
    USER_UPDATED = 'user.updated',
    USER_DELETED = 'user.deleted'
}
```

### Error Context

```javascript
// Provide context for error handling
class OrderProcessingError extends Error {
    constructor(
        message: string,
        public orderId: string,
        public stage: 'validation' | 'payment' | 'fulfillment',
        public details?: any
    ) {
        super(message);
        this.name = 'OrderProcessingError';
    }
}

// Usage provides clear context
throw new OrderProcessingError(
    'Payment failed',
    order.id,
    'payment',
    { reason: 'insufficient_funds', amount: order.total }
);
```

## Testing Patterns

### Descriptive Test Cases

```python
import pytest

class TestShoppingCart:
    """Test shopping cart functionality including edge cases"""
    
    def test_add_item_to_empty_cart(self):
        """Adding an item to empty cart should create cart with single item"""
        cart = ShoppingCart()
        item = Product(id="123", name="Widget", price=10.00)
        
        cart.add_item(item, quantity=1)
        
        assert len(cart.items) == 1
        assert cart.total == 10.00
    
    def test_add_duplicate_item_increases_quantity(self):
        """Adding same item twice should increase quantity, not duplicate"""
        # Test implementation
    
    def test_remove_item_not_in_cart_raises_error(self):
        """Attempting to remove non-existent item should raise ValueError"""
        # Test implementation
```

## AI-Friendly Comments

### When to Comment

```typescript
// DO: Explain business logic
// Calculate discount with tiered pricing
// - 0-99 items: no discount
// - 100-499 items: 10% discount
// - 500+ items: 15% discount
const calculateBulkDiscount = (quantity: number): number => {
    if (quantity < 100) return 0;
    if (quantity < 500) return 0.10;
    return 0.15;
};

// DO: Explain workarounds
// WORKAROUND: Safari doesn't support ResizeObserver properly
// This polyfill ensures compatibility until Safari 15+ adoption
if (!window.ResizeObserver) {
    window.ResizeObserver = ResizeObserverPolyfill;
}

// DON'T: State the obvious
// DON'T: increment counter by 1
counter++;
```

## Best Practices

- Keep functions small and focused
- Use consistent code style throughout
- Document complex algorithms and business rules
- Maintain up-to-date dependencies list
- Include example usage in complex modules
- Add integration test scenarios
- Document API contracts clearly
- Keep error messages descriptive