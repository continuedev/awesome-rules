---
name: Zuplo Performance Optimization Best Practices  
description: Guidelines for optimizing API gateway performance on Zuplo platform
---
## Rules

### Do this

- Leverage Zuplo's edge runtime for low-latency global distribution
- Use connection pooling by configuring handlers properly
- Cache responses where appropriate using outbound policies
- Minimize custom policy logic to reduce processing overhead
- Use environment variables to route traffic to nearest backend regions
- Configure proper timeout values for backend services
- Monitor and optimize rate limiting policies for performance vs protection balance
- Use WebSocket handlers for real-time applications requiring persistent connections
- Implement circuit breakers for resilient backend communication
- Choose appropriate handler types (URL Forward vs URL Rewrite) based on your needs

### Don't do this

- Don't implement complex business logic in gateway policies - keep it lightweight
- Don't set extremely low rate limits that impact legitimate users
- Don't ignore timeout configurations - they affect user experience
- Don't route all traffic through a single backend region when you have global distribution
- Don't over-engineer custom policies when built-in ones suffice
- Don't forget to test performance under load before production deployment
- Don't mix synchronous and asynchronous operations incorrectly in custom code

## Examples

### Good

```json
{
  "path": "/api/fast-endpoint",
  "handler": {
    "export": "urlForwardHandler",
    "module": "@zuplo/runtime",
    "options": {
      "forwardTo": "${env.REGIONAL_BACKEND_URL}",
      "timeout": 5000
    }
  },
  "policies": {
    "inbound": [
      {
        "name": "rate-limit-optimized",
        "export": "@zuplo/runtime",
        "module": "./policies/rate-limit-inbound",
        "options": {
          "requestsPerPeriod": 1000,
          "periodInSeconds": 60,
          "keyGenerator": "ip-address"
        }
      }
    ],
    "outbound": [
      {
        "name": "cache-response",
        "export": "@zuplo/runtime",
        "module": "./policies/response-cache-outbound",
        "options": {
          "ttl": 300,
          "varyBy": ["query", "headers.authorization"]
        }
      }
    ]
  }
}
```

### Bad

```json
{
  "path": "/api/slow-endpoint",
  "handler": {
    "export": "customHandler",
    "module": "./modules/heavy-processing-handler"
  },
  "policies": {
    "inbound": [
      {
        "name": "heavy-computation", 
        "export": "./policies/complex-business-logic",
        "options": {
          "processLargeDataSets": true,
          "performHeavyCalculations": true
        }
      }
    ]
  }
}
```
