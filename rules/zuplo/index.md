---
name: Zuplo API Gateway Development Rules
description: Comprehensive best practices for building and deploying API gateways on the Zuplo platform
---
## Rules Overview

This ruleset provides best practices for developers building API gateways on Zuplo, covering:

- **Gateway Setup**: Route configuration, handlers, and environment management
- **Security**: Authentication, authorization, rate limiting, and policy implementation  
- **Performance**: Optimization techniques for edge computing and global distribution
- **Deployment**: GitOps workflows, CI/CD, and environment management

### Key Principles

- **Security First**: Always implement authentication and rate limiting for production APIs
- **Edge-Optimized**: Leverage Zuplo's global edge network for low-latency performance
- **GitOps Driven**: Store all configuration in version control with proper CI/CD workflows
- **Environment Aware**: Use environment variables and separate configs for different stages
- **Policy Focused**: Use Zuplo's policy system for cross-cutting concerns like auth and validation

### Target Use Cases

These rules apply when:
- Building API gateways that proxy to backend services
- Implementing authentication, rate limiting, and request validation
- Setting up multi-environment deployments with CI/CD
- Optimizing for global performance and scalability
- Managing API security and compliance requirements

### Quick Start

1. Start with basic gateway setup using URL Forward handlers
2. Add security policies (authentication + rate limiting) 
3. Configure environment variables for different deployment stages
4. Implement GitOps workflows for deployment automation
5. Optimize for performance using caching and edge distribution

Apply these rules consistently to build robust, secure, and performant API gateways on Zuplo.
