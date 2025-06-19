# Awesome Rules [![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)

This collection focuses on rules written in standard markdown format with YAML frontmatter, compatible with various AI coding assistants like Cursor, Continue.dev, and others following the [amplified.dev](https://amplified.dev/) standard.

## Why Rules?

Rules are more than just suggestions; they’re essential building blocks that shape how your assistant interprets your requests. Clear, actionable rules help the agent consistently produce code that meets your standards, avoids common pitfalls, and aligns with your team’s workflows.

> [Read the Anatomy of Good Rules](https://blog.continue.dev/the-anatomy-of-rules-writing-effective-boundaries-for-ai-agents-in-ruby/)

## Rules
### General
- [Task Management](./rules/task-management/)

<!-- Examples for General -->
<!-- - **Coding Standards** - Enforce consistent code style and best practices -->
<!-- - **Error Handling** - Guidelines for robust error handling patterns -->
<!-- - **Performance** - Rules for writing efficient code -->
<!-- - **Security** - Security-focused development practices -->
<!-- - **Agent Enablement** - AI enablement and guidelines  -->

### Language Specific
- [Ruby](.rules/ruby/)

<!-- Examples for Language Specific -->
<!-- - **Coding Standards** - Enforce consistent code style and best practices -->
<!-- - **Error Handling** - Guidelines for robust error handling patterns -->
<!-- - **Performance** - Rules for writing efficient code -->
<!-- - **Security** - Security-focused development practices -->
<!-- - **Agent Enablement** - AI enablement and guidelines  -->

### Framework Specific
- [Zuplo](.rules/zuplo/)

<!-- Examples for Language Specific -->
<!-- - **Coding Standards** - Enforce consistent code style and best practices -->
<!-- - **Error Handling** - Guidelines for robust error handling patterns -->
<!-- - **Performance** - Rules for writing efficient code -->
<!-- - **Security** - Security-focused development practices -->
<!-- - **Agent Enablement** - AI enablement and guidelines  -->

### Code Quality

<!-- // remove examples after first contirbution. -->

- **Linting Rules** - Integration with ESLint, Prettier, and other tools
- **Type Safety** - Strict typing guidelines
- **Code Review** - Automated code review suggestions
- **Refactoring** - Safe refactoring patterns


### Documentation

<!-- // remove examples after first contirbution. -->

- **API Documentation** - Standards for documenting APIs
- **Code Comments** - When and how to write effective comments
- **README Standards** - Project documentation guidelines
- **Changelog** - Maintaining project history

### Testing

<!-- // remove examples after first contirbution. -->

- **Unit Testing** - Test structure and coverage guidelines
- **Integration Testing** - End-to-end testing patterns
- **Test Data** - Managing test fixtures and mocks
- **TDD Guidelines** - Test-driven development practices

### DevOps

<!-- // remove examples after first contirbution. -->

- **CI/CD** - Continuous integration and deployment rules
- **Docker** - Container best practices
- **Infrastructure** - Infrastructure as code guidelines
- **Monitoring** - Observability and logging standards

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
Check your specific tool's documentation for the correct folder structure.

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
