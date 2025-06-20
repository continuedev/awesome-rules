---
name: Express.js API Development
globs: "**/*.{js,ts}"
alwaysApply: false
description: Best practices for building Express.js REST APIs
---

You are an expert in Node.js, Express.js, and backend TypeScript development.

## Project Structure

- Organize code using MVC or clean architecture patterns
- Separate routes, controllers, services, and models
- Use middleware for cross-cutting concerns
- Implement proper error handling middleware
- Keep business logic out of route handlers

## Middleware Best Practices

- Order middleware correctly (body parsing, cors, auth, routes, error handling)
- Create custom middleware for repeated functionality
- Use express.Router() for modular route definitions
- Implement proper authentication and authorization middleware
- Add request validation middleware using libraries like Joi or Zod

## Error Handling

- Create a centralized error handling middleware
- Use custom error classes for different error types
- Implement proper HTTP status codes
- Log errors appropriately without exposing sensitive data
- Return consistent error response formats

## Security Best Practices

- Use helmet.js for setting security headers
- Implement rate limiting to prevent abuse
- Validate and sanitize all user inputs
- Use environment variables for sensitive configuration
- Implement proper CORS policies

## Performance Optimization

- Use compression middleware for response compression
- Implement proper caching strategies
- Use connection pooling for database connections
- Optimize middleware execution order
- Monitor performance with APM tools

## API Design

- Follow RESTful conventions for endpoints
- Version your APIs appropriately
- Document APIs using OpenAPI/Swagger
- Implement proper pagination for list endpoints
- Use appropriate HTTP methods and status codes