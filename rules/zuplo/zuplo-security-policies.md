---
name: Zuplo Security and Authentication Best Practices
description: Security best practices for API gateways built on Zuplo platform
---
## Rules

### Do this

- Always implement authentication policies (API key, OAuth2, or JWT) for production APIs
- Apply rate limiting policies to prevent abuse and ensure service availability
- Use IP allowlisting policies for internal or restricted APIs
- Implement request validation policies to sanitize and validate incoming data
- Apply policies at the route level for fine-grained control
- Use inbound policies for authentication, validation, and rate limiting
- Use outbound policies for response transformation and data masking
- Store sensitive configuration values as encrypted environment variables
- Validate JWT tokens at the edge before hitting your backend
- Use mTLS for high-security scenarios requiring client certificates

### Don't do this

- Don't expose APIs without authentication in production environments
- Don't skip rate limiting - even authenticated APIs need protection
- Don't store API keys or secrets in plain text configuration
- Don't allow unvalidated input to reach your backend services
- Don't apply blanket policies where route-specific policies are more appropriate
- Don't forget to test authentication flows before deployment
- Don't use weak API key generation or management practices

## Examples

### Good

```json
{
  "path": "/api/sensitive-data",
  "policies": {
    "inbound": [
      {
        "name": "api-key-auth",
        "export": "@zuplo/runtime",
        "module": "./policies/api-key-inbound",
        "options": {
          "allowAnonymous": false
        }
      },
      {
        "name": "rate-limit",
        "export": "@zuplo/runtime", 
        "module": "./policies/rate-limit-inbound",
        "options": {
          "requestsPerPeriod": 100,
          "periodInSeconds": 60
        }
      }
    ]
  }
}
```

### Bad

```json
{
  "path": "/api/sensitive-data",
  "handler": {
    "export": "urlForwardHandler",
    "module": "@zuplo/runtime",
    "options": {
      "forwardTo": "https://backend.internal.com"
    }
  }
}
```
