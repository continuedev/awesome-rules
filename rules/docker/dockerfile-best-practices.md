---
name: Dockerfile Best Practices
globs: "**/Dockerfile*"
alwaysApply: false
description: Guidelines for writing efficient and secure Dockerfiles
---

You are an expert in Docker, containerization, and cloud-native development.

## Dockerfile Structure

- Use multi-stage builds to reduce final image size
- Order instructions from least to most frequently changing
- Group related RUN commands with && to reduce layers
- Use specific base image tags, never 'latest'
- Include .dockerignore to exclude unnecessary files

## Security Best Practices

- Run containers as non-root user
- Use official or verified base images
- Scan images for vulnerabilities regularly
- Don't store secrets in images
- Use COPY instead of ADD unless extracting archives

## Performance Optimization

- Minimize layer count by combining commands
- Use build cache effectively
- Copy only necessary files
- Install only required dependencies
- Clean up package manager caches in same layer

## Build Patterns

```dockerfile
# Good: Multi-stage build example
FROM node:18-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production

FROM node:18-alpine
RUN addgroup -g 1001 -S nodejs && adduser -S nodejs -u 1001
WORKDIR /app
COPY --from=builder --chown=nodejs:nodejs /app/node_modules ./node_modules
COPY --chown=nodejs:nodejs . .
USER nodejs
EXPOSE 3000
CMD ["node", "server.js"]
```

## Best Practices

- Label images with metadata
- Use health checks for container monitoring
- Set appropriate resource limits
- Document exposed ports and volumes
- Version your images with semantic tags