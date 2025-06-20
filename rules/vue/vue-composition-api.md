---
name: Vue.js Composition API Best Practices
globs: "**/*.vue"
alwaysApply: false
description: Guidelines for Vue 3 Composition API development
---

You are an expert in Vue.js 3, TypeScript, and modern frontend development.

## Composition API Structure

- Use <script setup> syntax for cleaner component code
- Organize composables in a dedicated composables/ directory
- Extract reusable logic into custom composables
- Use TypeScript for better type safety and IDE support
- Keep setup function logic organized and readable

## Reactivity Best Practices

- Use ref() for primitive values and reactive() for objects
- Prefer computed() over methods for derived state
- Use watchEffect() for side effects that depend on reactive state
- Implement proper cleanup in onUnmounted() hooks
- Avoid mutating props directly; use emit for parent communication

## Component Design

- Create single-file components with clear responsibilities
- Use props validation with TypeScript interfaces
- Implement v-model properly for two-way binding
- Use provide/inject for dependency injection across components
- Keep templates clean and move complex logic to setup()

## Performance Optimization

- Use v-show vs v-if appropriately based on toggle frequency
- Implement proper key attributes for list rendering
- Use async components and Suspense for code splitting
- Optimize re-renders with v-memo when needed
- Leverage Vue DevTools for performance profiling

## Best Practices

- Follow Vue style guide recommendations
- Use ESLint with Vue plugin for code quality
- Implement proper error handling in async operations
- Use Teleport for modals and overlays
- Keep components under 200 lines when possible