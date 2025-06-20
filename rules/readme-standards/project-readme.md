---
name: Project README Standards
globs: "**/README.md"
alwaysApply: false
description: Guidelines for creating comprehensive project README files
---

You are an expert in technical documentation, open source best practices, and developer experience.

## README Structure

A well-structured README should include these sections in order:

1. Project Title and Description
2. Badges (build status, version, license)
3. Key Features
4. Screenshots/Demo (if applicable)
5. Quick Start
6. Installation
7. Usage Examples
8. API Reference (or link to docs)
9. Configuration
10. Contributing
11. License

## Essential Sections

### Project Header

```markdown
# Project Name

> One-line description of what this project does

[![Build Status](https://img.shields.io/github/actions/workflow/status/user/repo/ci.yml)](https://github.com/user/repo/actions)
[![npm version](https://img.shields.io/npm/v/package-name)](https://www.npmjs.com/package/package-name)
[![License](https://img.shields.io/github/license/user/repo)](LICENSE)

Brief paragraph explaining the project's purpose, main features, and why someone would want to use it.
```

### Quick Start

```markdown
## Quick Start

Get up and running in less than 5 minutes:

\`\`\`bash
npm install package-name
npm run dev
\`\`\`

Visit http://localhost:3000 to see the application.
```

### Installation

```markdown
## Installation

### Prerequisites

- Node.js 18+ 
- PostgreSQL 14+
- Redis 6.2+

### Install from npm

\`\`\`bash
npm install package-name
\`\`\`

### Install from source

\`\`\`bash
git clone https://github.com/user/repo.git
cd repo
npm install
npm run build
\`\`\`
```

### Usage Examples

```markdown
## Usage

### Basic Example

\`\`\`javascript
import { Widget } from 'package-name';

const widget = new Widget({
  apiKey: 'your-api-key',
  theme: 'dark'
});

widget.render('#app');
\`\`\`

### Advanced Example

\`\`\`javascript
// Custom configuration with error handling
const widget = new Widget({
  apiKey: process.env.API_KEY,
  theme: 'dark',
  onError: (error) => {
    console.error('Widget error:', error);
  }
});

// Add custom event handlers
widget.on('ready', () => {
  console.log('Widget is ready');
});

widget.render('#app');
\`\`\`
```

## Best Practices

- Keep the README focused and concise
- Use clear, simple language
- Include code examples that actually work
- Add visuals when they help understanding
- Link to more detailed documentation
- Keep examples up-to-date with the code
- Test your installation instructions regularly

## Common Mistakes to Avoid

- Don't assume reader knowledge
- Don't skip the Quick Start section
- Don't use jargon without explanation
- Don't forget to update version numbers
- Don't include sensitive information

## Formatting Tips

- Use consistent heading levels
- Include a table of contents for long READMEs
- Use code blocks with language highlighting
- Add alt text to images
- Use tables for comparing options
- Include emoji sparingly and purposefully