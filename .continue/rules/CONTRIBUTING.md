---
description: Rules for contributing
alwaysApply: true
---
# Awesome Rules For Contributing

## General Guidelines

Always use Markdown for documentation and README files. Maintain the existing structure of the README.md file and follow consistent formatting throughout the repository.

## README.md Structure

Maintain the following structure in the README.md file

## Organization of Rules

Organize rule files into the following main categories within the 'community' directory:

## Rule Categories

### General

- **Coding Standards** - Enforce consistent code style and best practices
- **Error Handling** - Guidelines for robust error handling patterns
- **Performance** - Rules for writing efficient code
- **Security** - Security-focused development practices
- **Agent Enablement** - AI enablement and guidelines

### Language Specific

- **TypeScript/JavaScript** - Modern JS/TS development patterns
- **Python** - Python best practices and conventions
- **Go** - Go idioms and standard library usage
- **Rust** - Memory safety and Rust-specific patterns
- **Java** - Enterprise Java development guidelines

### Framework Specific

- **React** - Component architecture and hooks patterns
- **Next.js** - Full-stack React development
- **Vue.js** - Vue composition API and best practices
- **Angular** - Angular architecture and RxJS patterns
- **Express** - Node.js backend development
- **FastAPI** - Python API development

### Code Quality

- **Linting Rules** - Integration with ESLint, Prettier, and other tools
- **Type Safety** - Strict typing guidelines
- **Code Review** - Automated code review suggestions
- **Refactoring** - Safe refactoring patterns

### Documentation

- **API Documentation** - Standards for documenting APIs
- **Code Comments** - When and how to write effective comments
- **README Standards** - Project documentation guidelines
- **Changelog** - Maintaining project history

### Testing

- **Unit Testing** - Test structure and coverage guidelines
- **Integration Testing** - End-to-end testing patterns
- **Test Data** - Managing test fixtures and mocks
- **TDD Guidelines** - Test-driven development practices

### DevOps

- **CI/CD** - Continuous integration and deployment rules
- **Docker** - Container best practices
- **Infrastructure** - Infrastructure as code guidelines
- **Monitoring** - Observability and logging standards

### File Organization

- Place each rule file directly in the 'rules' folder
- Use folder names that describe the category and content of the file
- Follow the pattern: `technology-focus-rules-file`
- Refer to the README in each folder for guidance on naming conventions
- Folders are encourage based on the technology or context of the rules they contain

## Naming and Formatting

### File Naming Convention

Use descriptive names for rule files and their folders, following the pattern:
`technology-focus-rules-prompt-file`

Examples:
- `react-component-architecture-rules-file`
- `ruby-rails-development-rules-file`
- `typescript-best-practices-rules-file`

### README Formatting

- Maintain alphabetical order within each category in the README.md file
- Use consistent formatting for list items in the README.md file
- Ensure all links are relative and correct

## Content Guidelines

### Rule File Content

When creating or editing rule files, focus on:

- **Project-specific instructions** and best practices
- **Context about what you're building**: Include architectural decisions, project structure, and commonly-used methods
- **Style guidelines**: Coding standards, formatting preferences, naming conventions
- **Technology-specific patterns**: Framework-specific best practices and patterns

### Documentation Standards

- Include comments in rule files to explain complex rules or provide context
- Use clear and concise language in all documentation and rule files
- Provide practical examples and use cases

### Rule File Structure

Each rule file should follow this frontmatter format:

```yaml
---
name: Descriptive Rule Name
globs: "**/*.{ext,ext2}"
alwaysApply: false
description: Brief description of what this rule covers
---
```
# Rule Content Here

## Optional README for Credit and Description

Each rule file may have an accompanying README.md file in its folder to:

- Provide credit to the original author
- Give a brief description of the rule file's purpose
- Include usage examples or special considerations

## Maintenance and Updates

### Adding New Rules

1. Update the README.md file when adding new rule files
2. Place new rules in the correct category
3. Ensure the table of contents remains accurate
4. When adding new categories, update both the 'Contents' and 'Rules' sections

### Repository Maintenance

- Regularly review and update categorization as the repository grows
- Ensure all links in the README.md file are relative and correct
- Maintain consistency in capitalization and punctuation throughout

## Best Practices

### Consistency Standards

- Maintain consistency in capitalization and punctuation throughout the repository
- When referencing AI coding assistants, use correct capitalization and spacing
- Focus on practical use cases for AI coding assistant users

### Categorization Guidelines

- If a rule file fits multiple categories, place it in the most relevant one
- Cross-reference in other categories if necessary
- Keep the 'Other' category for rules that don't fit neatly into main categories

### Content Focus

- Rules should be repository-specific "Rules for AI"
- Focus on providing repo-level context and guidelines, not just general coding practices
- Include information about project structure, architectural decisions, and commonly used libraries
- Consider rules for handling specific file types or coding patterns unique to your project
- Cover both code generation and code understanding aspects for AI assistants

## Additional Insights

### Rule Placement and Usage

- Rule files should be placed in the root of the repository or in designated rule directories
- Rule content will be used by AI coding assistants to understand project context
- Rules should provide context that helps AI understand your specific project needs

### Rule Scope

Rules can include:

- Project architecture and structure guidelines
- Technology stack specific patterns
- Code style and formatting preferences
- Testing strategies and patterns
- Deployment and build processes
- Security considerations
- Performance optimization guidelines
- Documentation standards

### Quality Assurance

#### When reviewing or creating rules

- Ensure rules are actionable and specific
- Avoid overly general advice that applies to all projects
- Include examples where helpful
- Test rules with your AI coding assistant to ensure they work as expected
- Keep rules updated as project requirements evolve

#### Do this
- Write function components with TypeScript interfaces for props
- Use descriptive component and prop names
- Implement proper error boundaries for components that might fail
- Export components as default exports
- Use React hooks for state management and side effects
- Write components that are easily testable

 #### Don't do this
- Don't use class components unless absolutely necessary
- Don't write components without proper TypeScript typing
- Don't create components with more than 300 lines of code
- Don't use any or unknown types for props
- Don't skip error handling for async operations