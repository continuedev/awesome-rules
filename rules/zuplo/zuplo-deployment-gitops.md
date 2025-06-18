---
name: Zuplo GitOps and Deployment Best Practices
description: Best practices for deploying and managing Zuplo API gateways with GitOps workflows
---
## Rules

### Do this

- Store all Zuplo configuration in Git repositories for version control and auditability  
- Use separate branches for different environments (dev, staging, production)
- Implement proper CI/CD pipelines that deploy changes through Git workflows
- Use environment-specific configuration files and variables
- Test configuration changes in preview environments before production
- Tag releases with semantic versioning for rollback capabilities
- Use pull request reviews for configuration changes
- Set up monitoring and alerting for deployment failures
- Document configuration changes in commit messages and pull requests
- Use Zuplo's unlimited preview environments for feature branch testing

### Don't do this

- Don't make configuration changes directly in production without version control
- Don't skip testing in preview environments before merging to main
- Don't deploy to production without proper review processes
- Don't hardcode environment-specific values in configuration files
- Don't ignore deployment failures or rollback procedures
- Don't mix configuration changes with feature development in the same commits
- Don't forget to clean up old preview environments and unused configurations

## Examples

### Good

```yaml
# .github/workflows/deploy-zuplo.yml
name: Deploy Zuplo Gateway
on:
  push:
    branches: [main, staging, dev]
  pull_request:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Deploy to Zuplo
        uses: zuplo/zuplo-deploy-action@v1
        with:
          environment: ${{ github.ref == 'refs/heads/main' && 'production' || 'staging' }}
          api-key: ${{ secrets.ZUPLO_API_KEY }}
```

```json
// config/environments/production.json
{
  "variables": {
    "BASE_URL": "https://api.production.com",
    "RATE_LIMIT": "1000", 
    "CACHE_TTL": "3600"
  },
  "policies": {
    "security": "strict",
    "logging": "full"
  }
}
```

### Bad

```json
// Hardcoded production config mixed with dev settings
{
  "variables": {
    "BASE_URL": "https://api.production.com", // No environment separation
    "DEBUG_MODE": true, // Debug enabled in prod
    "API_KEY": "sk-live-123abc..." // Secret in plaintext
  }
}
```

```bash
# Manual deployment without version control
curl -X POST https://api.zuplo.com/deploy \
  -H "Authorization: Bearer $TOKEN" \
  -d @config.json # Direct production deployment
```
