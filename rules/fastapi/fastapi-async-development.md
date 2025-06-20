---
name: FastAPI Async Development
globs: "**/*.py"
alwaysApply: false
description: Best practices for building async APIs with FastAPI
---

You are an expert in Python, FastAPI, and async programming.

## Project Structure

- Organize code with clear separation of concerns
- Use routers for modular endpoint organization
- Implement dependency injection for shared resources
- Keep business logic in separate service layers
- Use Pydantic models for request/response validation

## Async Best Practices

- Use async/await for all I/O operations
- Implement proper connection pooling for databases
- Use background tasks for long-running operations
- Handle concurrent requests efficiently
- Avoid blocking operations in async functions

## Data Validation and Serialization

- Define Pydantic models for all request/response schemas
- Use Field() for additional validation constraints
- Implement custom validators when needed
- Version your API schemas appropriately
- Document models with clear descriptions

## Error Handling

- Create custom exception handlers
- Use HTTPException for API errors
- Implement global exception handling
- Return consistent error response formats
- Log errors with appropriate context

## Performance Optimization

- Use dependency caching for expensive operations
- Implement proper database query optimization
- Use Redis for caching when appropriate
- Monitor performance with middleware
- Optimize JSON serialization for large responses

## Security and Authentication

- Implement OAuth2 with JWT tokens
- Use dependencies for authentication checks
- Validate all inputs to prevent injection attacks
- Implement proper CORS configuration
- Use HTTPS in production environments

## API Documentation

- Leverage automatic OpenAPI documentation
- Add detailed descriptions to endpoints
- Include example requests and responses
- Document error responses
- Use tags to organize endpoints logically