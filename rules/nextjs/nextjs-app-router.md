---
name: Next.js App Router Best Practices
globs: "**/app/**/*.{js,jsx,ts,tsx}"
alwaysApply: false
description: Guidelines for Next.js 13+ App Router development
---

You are an expert in Next.js, React, and full-stack TypeScript development.

## App Router Architecture

- Use the app directory structure for all new pages
- Implement proper file conventions: page.tsx, layout.tsx, loading.tsx, error.tsx
- Use route groups (folders in parentheses) to organize routes without affecting URLs
- Implement parallel routes and intercepting routes when needed
- Use metadata API for SEO optimization

## Server Components vs Client Components

- Default to Server Components for better performance
- Use 'use client' directive only when necessary (interactivity, browser APIs)
- Keep client components small and focused
- Pass serializable props from Server to Client Components
- Use composition to minimize client-side JavaScript

## Data Fetching

- Fetch data directly in Server Components using async/await
- Use React's cache() for request deduplication
- Implement proper error handling with error.tsx files
- Use loading.tsx for better UX during data fetching
- Consider using Suspense boundaries for granular loading states

## Performance Optimization

- Use next/image for automatic image optimization
- Implement proper caching strategies with fetch options
- Use dynamic imports for code splitting
- Leverage ISR (Incremental Static Regeneration) when appropriate
- Monitor Core Web Vitals and optimize accordingly

## Best Practices

- Use TypeScript for type safety across the application
- Implement proper error boundaries at route levels
- Use environment variables for configuration
- Follow Next.js naming conventions strictly
- Keep server-only code in separate files to prevent client bundle bloat