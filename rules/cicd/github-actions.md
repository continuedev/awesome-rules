---
name: GitHub Actions CI/CD
globs: "**/.github/workflows/*.{yml,yaml}"
alwaysApply: false
description: Best practices for GitHub Actions workflows
---

You are an expert in CI/CD, GitHub Actions, and DevOps automation.

## Workflow Structure

- Use descriptive workflow and job names
- Organize workflows by purpose (ci.yml, deploy.yml, release.yml)
- Implement proper job dependencies with needs
- Use matrix builds for testing multiple versions
- Keep workflows DRY using reusable workflows

## Security Best Practices

- Use GitHub Secrets for sensitive data
- Implement least privilege for GITHUB_TOKEN permissions
- Pin action versions to specific commits or tags
- Use OIDC for cloud provider authentication
- Scan for vulnerabilities in dependencies

## Performance Optimization

- Cache dependencies appropriately (npm, pip, etc.)
- Use artifacts efficiently between jobs
- Parallelize independent jobs
- Implement conditional workflows to avoid unnecessary runs
- Use concurrency groups to cancel outdated runs

## Error Handling

- Implement proper timeout values
- Add retry logic for flaky steps
- Use continue-on-error strategically
- Create informative failure messages
- Set up notifications for critical failures

## Best Practices

- Use composite actions for repeated tasks
- Document workflows with comments
- Implement branch protection rules
- Use environments for deployment stages
- Monitor workflow metrics and costs