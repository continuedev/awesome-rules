---
name: Performance Optimization Guidelines
globs: "**/*.{js,ts,py,go,java,rb,cs}"
alwaysApply: false
description: Best practices for writing high-performance, efficient code
---

You are an expert in performance optimization, algorithmic efficiency, and system design.

## Performance Principles

- Measure before optimizing
- Optimize the critical path first
- Consider algorithmic complexity
- Balance performance with readability
- Cache expensive operations

## Algorithmic Optimization

### Time Complexity Awareness

```python
# Bad: O(n²) complexity
def find_duplicates_naive(items):
    duplicates = []
    for i in range(len(items)):
        for j in range(i + 1, len(items)):
            if items[i] == items[j] and items[i] not in duplicates:
                duplicates.append(items[i])
    return duplicates

# Good: O(n) complexity
def find_duplicates_optimal(items):
    seen = set()
    duplicates = set()
    for item in items:
        if item in seen:
            duplicates.add(item)
        seen.add(item)
    return list(duplicates)
```

### Data Structure Selection

```javascript
// Choose appropriate data structures
class PerformantCache {
    constructor(maxSize = 1000) {
        this.maxSize = maxSize;
        this.cache = new Map(); // O(1) access time
        this.accessOrder = []; // Consider LinkedList for LRU
    }
    
    get(key) {
        if (this.cache.has(key)) {
            // Move to end (most recently used)
            this.updateAccessOrder(key);
            return this.cache.get(key);
        }
        return null;
    }
    
    set(key, value) {
        if (this.cache.size >= this.maxSize && !this.cache.has(key)) {
            // Remove least recently used
            const lru = this.accessOrder.shift();
            this.cache.delete(lru);
        }
        this.cache.set(key, value);
        this.updateAccessOrder(key);
    }
}
```

## Memory Optimization

### Object Pooling

```typescript
class ObjectPool<T> {
    private available: T[] = [];
    private inUse = new Set<T>();
    
    constructor(
        private factory: () => T,
        private reset: (obj: T) => void,
        private initialSize: number = 10
    ) {
        // Pre-allocate objects
        for (let i = 0; i < initialSize; i++) {
            this.available.push(factory());
        }
    }
    
    acquire(): T {
        let obj = this.available.pop();
        if (!obj) {
            obj = this.factory();
        }
        this.inUse.add(obj);
        return obj;
    }
    
    release(obj: T): void {
        if (this.inUse.delete(obj)) {
            this.reset(obj);
            this.available.push(obj);
        }
    }
}

// Usage
const bufferPool = new ObjectPool(
    () => new ArrayBuffer(1024 * 1024), // 1MB buffers
    (buffer) => new Uint8Array(buffer).fill(0), // Clear on release
    5 // Keep 5 buffers ready
);
```

### Memory-Efficient Patterns

```python
# Generator for large datasets
def process_large_file(filename):
    with open(filename, 'r') as file:
        for line in file:  # Process line by line
            yield process_line(line)  # Memory efficient

# Bad: Loading entire file
def process_large_file_bad(filename):
    with open(filename, 'r') as file:
        lines = file.readlines()  # Loads entire file into memory
        return [process_line(line) for line in lines]
```

## Async Performance

### Parallel Processing

```javascript
// Concurrent request handling
async function fetchMultipleUrls(urls) {
    // Bad: Sequential processing
    const resultsBad = [];
    for (const url of urls) {
        resultsBad.push(await fetch(url));
    }
    
    // Good: Parallel processing
    const results = await Promise.all(
        urls.map(url => fetch(url))
    );
    
    // Better: Controlled concurrency
    const concurrencyLimit = 5;
    const results = [];
    for (let i = 0; i < urls.length; i += concurrencyLimit) {
        const batch = urls.slice(i, i + concurrencyLimit);
        const batchResults = await Promise.all(
            batch.map(url => fetch(url))
        );
        results.push(...batchResults);
    }
    
    return results;
}
```

## Database Optimization

### Query Optimization

```sql
-- Bad: N+1 query problem
SELECT * FROM orders WHERE user_id = ?;
-- Then for each order:
SELECT * FROM order_items WHERE order_id = ?;

-- Good: Single query with JOIN
SELECT o.*, oi.*
FROM orders o
LEFT JOIN order_items oi ON o.id = oi.order_id
WHERE o.user_id = ?;

-- Better: With indexing
CREATE INDEX idx_orders_user_id ON orders(user_id);
CREATE INDEX idx_order_items_order_id ON order_items(order_id);
```

### Connection Pooling

```javascript
// Database connection pool
const { Pool } = require('pg');

const pool = new Pool({
    max: 20, // Maximum connections
    idleTimeoutMillis: 30000,
    connectionTimeoutMillis: 2000,
});

// Reuse connections
async function queryDatabase(sql, params) {
    const client = await pool.connect();
    try {
        return await client.query(sql, params);
    } finally {
        client.release();
    }
}
```

## Caching Strategies

### Multi-Level Caching

```typescript
class MultiLevelCache {
    constructor(
        private l1Cache: Map<string, any>, // In-memory
        private l2Cache: Redis, // Redis
        private ttl: number = 3600 // 1 hour
    ) {}
    
    async get(key: string): Promise<any> {
        // Check L1 cache first
        if (this.l1Cache.has(key)) {
            return this.l1Cache.get(key);
        }
        
        // Check L2 cache
        const l2Value = await this.l2Cache.get(key);
        if (l2Value) {
            // Promote to L1
            this.l1Cache.set(key, l2Value);
            return l2Value;
        }
        
        return null;
    }
    
    async set(key: string, value: any): Promise<void> {
        // Set in both caches
        this.l1Cache.set(key, value);
        await this.l2Cache.setex(key, this.ttl, value);
        
        // Implement LRU for L1 cache
        if (this.l1Cache.size > 1000) {
            const firstKey = this.l1Cache.keys().next().value;
            this.l1Cache.delete(firstKey);
        }
    }
}
```

## Best Practices

- Profile before optimizing
- Use appropriate data structures
- Minimize memory allocations
- Batch operations when possible
- Implement caching strategically
- Monitor performance metrics
- Consider lazy loading
- Optimize critical paths first