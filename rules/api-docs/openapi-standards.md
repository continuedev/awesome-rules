---
name: OpenAPI Documentation Standards
globs: "**/*.{yaml,yml,json}"
alwaysApply: false
description: Best practices for API documentation using OpenAPI/Swagger
---

You are an expert in API design, OpenAPI specification, and technical documentation.

## OpenAPI Structure

- Use OpenAPI 3.0+ for modern API documentation
- Organize spec files logically (by domain or service)
- Include comprehensive API metadata
- Define reusable components for schemas and parameters
- Version your API documentation alongside code

## API Description Best Practices

- Write clear, concise endpoint summaries
- Include detailed descriptions with examples
- Document all possible response codes
- Explain authentication requirements
- Include rate limiting information

## Schema Documentation

```yaml
components:
  schemas:
    User:
      type: object
      description: Represents a user in the system
      required:
        - id
        - email
        - createdAt
      properties:
        id:
          type: string
          format: uuid
          description: Unique identifier for the user
          example: "123e4567-e89b-12d3-a456-426614174000"
        email:
          type: string
          format: email
          description: User's email address
          example: "user@example.com"
        name:
          type: string
          description: User's full name
          example: "John Doe"
        createdAt:
          type: string
          format: date-time
          description: Timestamp when the user was created
          example: "2023-01-01T00:00:00Z"
```

## Endpoint Documentation

```yaml
paths:
  /users/{userId}:
    get:
      summary: Get user by ID
      description: |
        Retrieves detailed information about a specific user.
        Requires authentication and appropriate permissions.
      operationId: getUserById
      tags:
        - Users
      parameters:
        - name: userId
          in: path
          required: true
          description: The ID of the user to retrieve
          schema:
            type: string
            format: uuid
      responses:
        '200':
          description: User found successfully
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/User'
        '404':
          description: User not found
        '401':
          description: Authentication required
```

## Best Practices

- Use consistent naming conventions
- Include request/response examples
- Document edge cases and error scenarios
- Keep documentation in sync with implementation
- Use tools for documentation generation and validation