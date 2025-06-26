# Awesome Rules [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

This collection focuses on rules written in standard markdown format with YAML frontmatter, compatible with various AI coding assistants like Cursor, Continue.dev, and others following the [amplified.dev](https://amplified.dev/) standard.

## Why Rules?

Rules are more than just suggestions; they’re essential building blocks that shape how your assistant interprets your requests. Clear, actionable rules help the agent consistently produce code that meets your standards, avoids common pitfalls, and aligns with your team’s workflows.

> [Read the Anatomy of Good Rules](https://blog.continue.dev/the-anatomy-of-rules-writing-effective-boundaries-for-ai-agents-in-ruby/)

## Rules
### General
- [Agent Enablement](./rules/agent-enablement)
- [Coding Standards](./rules/coding-standards)
- [Error Handling](./rules/error-handling)
- [Performance](./rules/performance)
- [Security](./rules/security)
- [Task Management](./rules/task-management/)

### Language Specific
- [Erlang](./rules/erlang)
- [Go](./rules/go)
- [Lua](./rules/lua)
- [Python](./rules/python)
- [Ruby](./rules/ruby/)
- [Rust](./rules/rust)
- [TypeScript](./rules/typescript)
- [Zig](./rules/zig)

### Framework Specific
- [Express](./rules/express)
- [FastAPI](./rules/fastapi)
- [Next.js](./rules/nextjs)
- [React](./rules/react)
- [Supabase](./rules/supabase)
- [LanceDB](./rules/lancedb/)
- [tailwind](./rules/tailwind)
- [trpc](./rules/trpc)
- [Vue.js](./rules/vue)
- [Zuplo](./rules/zuplo/)
- [cognee](./rules/cognee/)

### Code Quality

- [Clean Code](./rules/clean-code)
- [ESLint Configuration](./rules/eslint-config)
- [Prettier Formatting](./rules/prettier-standards)
- [Type Safety Guidelines](./rules/type-safety)
- [Code Review Standards](./rules/code-review)
- [Refactoring Patterns](./rules/refactoring-patterns)


### Documentation

- [API Documentation](./rules/api-docs)
- [Changelog](./rules/changelog)
- [Code Comments](./rules/code-comments)
- [Post-mortems](./rules/postmortems)
- [README Standards](./rules/readme-standards)

### Testing

- [Jest Testing](./rules/jest-testing)
- [Unit Testing Guidelines](./rules/unit-testing)
- [Integration Testing](./rules/integration-testing)
- [End-to-End Testing](./rules/e2e-testing)
- [Test Data Management](./rules/test-data)
- [TDD Guidelines](./rules/tdd-guidelines)
- [Cypress Testing](./rules/cypress-testing)
- [React Testing Library](./rules/react-testing-library)
- [Recurse ML](./rules/recurse-ml/rml-verify.md)

### DevOps

- [CI/CD](./rules/cicd)
- [Docker](./rules/docker)
- [Monitoring](./rules/monitoring)
- [Terraform](./rules/terraform)

## Using Rules Locally

### [`rules` CLI](https://rules.so)

The `rules` CLI helps you fetch and manage rules locally, across any AI coding assistant.

### Install `rules`

The `rules` CLI can be installed using NPM:

```bash
npm i -g rules-cli
```

### Adding Rules to Your Project

To download rules to your repository you can use `rules add`. For example:

```bash
rules add starter/nextjs-rules
```

This will add them to your project in a local `.rules` folder.

You can also download from GitHub rather than the rules registry:

```bash
rules add gh:continuedev/rules
```

From there you can use `rules render` to translate into the format of your choice:

**For Cursor:**
```bash
rules render cursor
```

will create the following folder structure:

```
your-project/
├── .cursor/
    └── rules/
        ├── coding-standards.mdc
        ├── testing-guidelines.mdc
        └── documentation-rules.mdc
```

**For Continue:**
```bash
rules render continue
```

will create the following folder structure:

```
your-project/
├── .continue/
│   └── rules/
│       ├── coding-standards.md
│       ├── testing-guidelines.md
│       └── documentation-rules.md
```

**For other AI assistants:**
See [the docs](https://www.rules.so/#render-rules) for the full list of supported formats.

## Contributing

We welcome contributions, especially if you have great rules to share. 

1. Fork this repository
2. Create your rule in the `rules` folder. The folder name should follow this pattern: `technology-focus-description` For example: `typescript-type-standards-practices`
4. Update the main README.md file, adding your contribution to the appropriate category.
5. Ensure your contribution follows the guidelines in the `CONTRIBUTING.md` file in the `.continue/rules` file at the root of this repository.
6. Submit a pull request with a description, PRs with no description or clear title will be marked as spam and closed.

Please refer to the `CONTRIBUTING.md` file in the `.continue/rules` for details on how to submit rules, report issues, and contribute to the project.

## License

This project is licensed under [CC0 1.0 Universal](LICENSE) - see the LICENSE file for details.

## Acknowledgments

- [amplified.dev](https://amplified.dev/), the coding manifesto that inspired this repo
- [PatrickJS/awesome-cursorrules](https://github.com/PatrickJS/awesome-cursorrules) was an inspiration for the structure of this repo
- All contributors who help make this list awesome

---

**Note**: This is a community-maintained collection of rules. To read and sign the amplified.dev pledge, visit [amplified.dev](https://amplified.dev/).
