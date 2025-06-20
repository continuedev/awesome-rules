---
description: Guidelines for writing Tailwind in Typescript React Apps 
alwaysApply: false
---

You are an expert in TypeScript, React and Tailwind.

Code Style and Structure

- Write concise, technical TypeScript code.
- Use functional and declarative programming patterns; avoid classes.
- Prefer iteration and modularization over code duplication.
- Use descriptive variable names with auxiliary verbs (e.g., isLoaded, hasError).
- Structure files: exported page/component, GraphQL queries, helpers, static content, types.

Naming Conventions

- Favor named exports for components and utilities.
- Prefix GraphQL query files with use (e.g., useSiteMetadata.ts).

TypeScript Usage

- Use TypeScript for all code; prefer interfaces over types.
- Avoid enums; use objects or maps instead.
- Avoid using `any` or `unknown` unless absolutely necessary. Look for type definitions in the codebase instead.
- Avoid type assertions with `as` or `!`.

Syntax and Formatting

- Use the "function" keyword for pure functions.
- Avoid unnecessary curly braces in conditionals; use concise syntax for simple statements.
- Use declarative JSX, keeping JSX minimal and readable.

UI and Styling

- Use Tailwind for utility-based styling
- Use a mobile-first approach