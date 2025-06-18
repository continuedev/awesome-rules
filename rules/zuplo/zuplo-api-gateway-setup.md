---
name: Zuplo API Gateway Setup Best Practices
description: Essential practices for setting up and configuring API gateways on Zuplo
---
## Rules

### Do this

- Always define routes in `routes.oas.json` with clear summaries and proper HTTP methods
- Use environment variables for backend URLs (e.g., `${env.BASE_URL}`) to support multiple environments
- Start with the URL Forward Handler for simple proxying scenarios
- Test routes immediately after creation using the built-in test console
- Configure CORS settings appropriately for your client applications
- Use descriptive path names that reflect your API's purpose
- Save your configuration files frequently (CMD+S) while editing
- Set up proper environment variables for different deployment stages (dev, staging, prod)

### Don't do this

- Don't hardcode backend URLs directly in route configurations
- Don't skip testing routes after configuration changes
- Don't use generic or unclear route summaries - they become your API documentation
- Don't forget to configure CORS if your API will be called from browsers
- Don't deploy without verifying your environment variables are properly set
- Don't create routes without understanding the target backend service

## Examples

### Good

```json
{
  "path": "/api/users/:userId",
  "methods": ["GET", "PUT", "DELETE"],
  "summary": "User management operations",
  "handler": {
    "export": "urlForwardHandler", 
    "module": "@zuplo/runtime",
    "options": {
      "forwardTo": "${env.USER_SERVICE_URL}"
    }
  },
  "corsPolicy": "allow-all-origins"
}
```

### Bad

```json
{
  "path": "/path-0",
  "methods": ["GET"],
  "summary": "",
  "handler": {
    "export": "urlForwardHandler",
    "module": "@zuplo/runtime", 
    "options": {
      "forwardTo": "https://hardcoded-prod-url.com"
    }
  }
}
```
