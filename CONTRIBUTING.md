# Contributing to Kiro Powers - AWS Collection

Thank you for your interest in contributing to this project! We welcome contributions from the community.

## How to Contribute

### Reporting Issues

If you find a bug or have a suggestion:

1. Check if the issue already exists in [GitHub Issues](https://github.com/DavidDelOjo/kiro-powers-aws/issues)
2. If not, create a new issue with:
   - Clear title and description
   - Steps to reproduce (for bugs)
   - Expected vs actual behavior
   - Your environment (Kiro version, OS, AWS region)
   - Relevant logs or screenshots

### Suggesting Enhancements

We welcome ideas for new features or improvements:

1. Open an issue with the `enhancement` label
2. Describe the feature and its benefits
3. Provide use cases and examples
4. Discuss implementation approach if applicable

### Pull Requests

#### Before You Start

1. Fork the repository
2. Create a new branch from `main`:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. Make sure you have tested your changes with Kiro 0.7+

#### Making Changes

1. Follow the existing code and documentation structure
2. Update documentation if you change functionality
3. Add or update examples as needed
4. Test your changes thoroughly

#### Documentation Standards

- Use clear, concise language
- Include code examples where appropriate
- Update POWER.md files if changing power functionality
- Keep README.md up to date
- Add entries to CHANGELOG.md

#### Commit Guidelines

Use clear, descriptive commit messages:

```
feat: add new security check for S3 encryption
fix: correct pricing calculation for multi-region
docs: update installation instructions
chore: update dependencies
```

#### Submitting Pull Request

1. Push your changes to your fork
2. Create a Pull Request to the `main` branch
3. Fill out the PR template with:
   - Description of changes
   - Related issues
   - Testing performed
   - Screenshots (if applicable)
4. Wait for review and address feedback

### Code Review Process

1. Maintainers will review your PR
2. Address any requested changes
3. Once approved, your PR will be merged
4. Your contribution will be credited in the release notes

## Development Setup

### Prerequisites

```bash
# Install uv
curl -LsSf https://astral.sh/uv/install.sh | sh

# Configure AWS CLI
aws configure

# Install Kiro IDE
# Download from https://kiro.dev
```

### Testing Your Changes

1. Install the power locally in Kiro:
   ```
   Powers Panel → Add Custom Power → Local Directory
   ```

2. Test all documented workflows:
   - Installation process
   - Configuration steps
   - Example prompts
   - Error scenarios

3. Verify documentation accuracy:
   - All commands work as documented
   - Examples produce expected results
   - Troubleshooting steps are effective

## Adding New Powers

If you want to contribute a new AWS Power:

### Structure

```
new-power/
├── POWER.md          # Complete documentation
├── mcp.json          # MCP server configuration
└── steering/         # Optional steering files
    └── guide.md
```

### POWER.md Requirements

Include these sections:
- Frontmatter with metadata (name, displayName, description, keywords, author)
- Overview
- Key Features
- Prerequisites
- Available Tools
- Common Workflows
- Troubleshooting
- Best Practices
- Additional Resources

### MCP Configuration

```json
{
  "mcpServers": {
    "your-server-name": {
      "command": "uvx",
      "args": ["package-name@latest"],
      "env": {
        "AWS_PROFILE": "default",
        "AWS_REGION": "us-east-1",
        "FASTMCP_LOG_LEVEL": "ERROR"
      }
    }
  }
}
```

### Documentation Standards

- Write in clear, professional English
- Include practical examples
- Provide troubleshooting guidance
- Document IAM permissions required
- Add cost considerations if applicable

## Style Guidelines

### Documentation

- Use Markdown formatting
- Include code blocks with language specification
- Use bullet points for lists
- Keep paragraphs concise
- Add links to official documentation

### Code Examples

```bash
# Good: Clear, commented, complete
aws configure --profile my-profile
# Configure with your AWS credentials
```

```bash
# Avoid: Unclear, incomplete
aws configure
```

## Community Guidelines

### Be Respectful

- Be welcoming to newcomers
- Respect different viewpoints
- Provide constructive feedback
- Help others learn and grow

### Be Professional

- Keep discussions on-topic
- Avoid offensive language
- Focus on technical merit
- Credit others' contributions

## Questions?

- Open a [GitHub Discussion](https://github.com/DavidDelOjo/kiro-powers-aws/discussions)
- Join the [Kiro Discord](https://discord.gg/kiro) community
- Check existing issues and documentation

## License

By contributing, you agree that your contributions will be licensed under the Apache License 2.0.

## Recognition

Contributors will be:
- Listed in release notes
- Credited in the README
- Acknowledged in the community

Thank you for contributing to Kiro Powers - AWS Collection!

---

**Last Updated**: 2026-02-12
