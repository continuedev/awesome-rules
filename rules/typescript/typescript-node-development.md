---
name: TypeScript Node Development
globs: "**/*.{ts,js}"
alwaysApply: false
description: TypeScript patterns and practices for Node.js development
---

# TypeScript Node Development

## Project Setup

- Use `@types/node` for Node.js type definitions
- Configure `tsconfig.json` for Node.js target environment
- Use ES modules with proper TypeScript configuration
- Set up proper module resolution for Node.js
- Configure build and development scripts appropriately

## Module System

- Use ES6 imports/exports with TypeScript
- Configure path mapping for clean imports
- Use proper module resolution strategies
- Implement barrel exports for public APIs
- Handle CommonJS interoperability when needed

## Environment Configuration

- Type environment variables with proper interfaces
- Use configuration objects with TypeScript types
- Implement environment-specific configurations
- Use dotenv with TypeScript support
- Validate environment configuration at startup

## Error Handling

- Use typed error classes for different error types
- Implement proper async error handling patterns
- Use Result types for explicit error handling
- Create error middleware with proper typing
- Handle unhandled promise rejections appropriately

## API Development

- Use Express with TypeScript types
- Type request and response objects properly
- Implement type-safe middleware patterns
- Use validation libraries with TypeScript support
- Create typed route handlers and controllers

## Database Integration

- Use TypeScript with ORMs like Prisma or TypeORM
- Type database queries and results
- Implement proper connection management
- Use migrations with TypeScript support
- Create typed repository patterns

## Testing

- Use Jest with TypeScript configuration
- Type test fixtures and mocks properly
- Use `@types/jest` for test typing
- Implement integration tests with proper typing
- Use supertest for API testing with types

## Performance Considerations

- Configure TypeScript compilation for production
- Use proper bundling strategies
- Implement lazy loading patterns
- Profile TypeScript compilation performance
- Optimize build times with incremental compilation

## Dependency Management

- Type third-party dependencies properly
- Use DefinitelyTyped for missing types
- Create ambient declarations when needed
- Keep dependencies and dev dependencies organized
- Use dependency injection with proper typing

## Common Patterns

- Create typed service layers
- Implement factory patterns with generics
- Use decorators for metadata and validation
- Create type-safe configuration systems
- Implement proper logging with structured types