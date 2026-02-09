# README Generator Plugin for Claude Code

A professional README.md generator skill for Claude Code that creates comprehensive, well-structured documentation with consistent quality across any project type.

## Features

- **Auto-detection**: Automatically identifies project type (Terraform, Python, Node.js, Go, Rust, Docker, etc.)
- **Comprehensive Structure**: Generates READMEs with 13+ sections covering all aspects of a project
- **Consistent Quality**: Follows best practices for documentation structure and content
- **Project-Aware**: Extracts real commands, configurations, and examples from your codebase
- **Flexible**: Can update existing READMEs while preserving valuable content, or create new ones from scratch

## Installation

### Quick Installation (Recommended)

The simplest way to use this skill is to copy it directly to your Claude Code skills directory:

```bash
# Clone the repository
git clone https://github.com/Cenarkion/readme-generator-plugin.git

# Copy the skill to your Claude skills directory
cp -r readme-generator-plugin/skills/readme-generator ~/.claude/skills/

# Verify installation
ls ~/.claude/skills/readme-generator/
```

The skill is now available in any Claude Code session. Just type `/readme-generator` in any project!

### Updating the Skill

To get the latest version:

```bash
# Navigate to your cloned repository
cd readme-generator-plugin

# Pull latest changes
git pull

# Copy updated skill
cp -r skills/readme-generator ~/.claude/skills/
```

### Team Installation

Share these instructions with your team, or add to your team documentation:

```bash
# One-time setup per developer
git clone https://github.com/Cenarkion/readme-generator-plugin.git
cp -r readme-generator-plugin/skills/readme-generator ~/.claude/skills/
```

Each team member will then have the `/readme-generator` skill available in all their projects.

## Usage

Navigate to any project directory and run:

```bash
# Generate README with auto-detection
/readme-generator

# Specify project type
/readme-generator terraform

# Focus on specific areas
/readme-generator python deployment troubleshooting
```

## What Gets Generated

The skill creates comprehensive READMEs with these sections:

1. **Project Overview** - Description, purpose, key features
2. **Critical Constraints** - Size limits, prerequisites, warnings
3. **Common Commands** - Building, deploying, testing workflows
4. **Architecture** - Repository structure, system design, versions
5. **Configuration & Setup** - Environment variables, config files
6. **Development Workflow** - Getting started, build process, quality checks
7. **CI/CD Pipeline** - Stages, branch strategy, deployment flow
8. **Deployment & Operations** - Step-by-step deployment, rollback
9. **Recent Work & Current State** - Ongoing initiatives, known issues
10. **Working With [Technology]** - Technology-specific guidance
11. **Testing & Validation** - Running tests, coverage, validation
12. **Troubleshooting** - Common issues, debugging, getting help
13. **Governance Notes** - Ownership boundaries, manual vs automated

## Supported Project Types

- **Infrastructure as Code**: Terraform, CloudFormation, Pulumi
- **Applications**: Node.js, Python, Go, Rust, Java
- **Libraries/Packages**: npm, PyPI, crates, Maven
- **CLI Tools**: Command-line applications
- **Container Projects**: Docker, docker-compose

## Quality Standards

The generator:
- Uses actual commands and examples from your codebase (no placeholders)
- Preserves valuable existing content when updating
- Maintains all reference links (Confluence, Jira, ServiceNow, etc.)
- Verifies commands exist in Makefiles or package.json
- Includes proper code formatting with language-specific syntax highlighting
- Balances detail with scannability

## Examples

### Terraform Project
Generates comprehensive docs covering:
- Backend configuration and state management
- Deployment commands for each environment
- Expected Terraform plan output
- Manual vs automated processes
- Policy size limits and constraints

### Node.js Application
Generates docs covering:
- Installation via npm/yarn
- Environment variable configuration
- API endpoints and request examples
- Development and production builds
- Testing and deployment

### Python Package
Generates docs covering:
- Installation via pip
- API documentation with code examples
- Development setup with virtual environments
- Publishing to PyPI
- Testing with pytest

## Configuration

The skill respects these optional arguments:

- **First argument**: Project type (if you want to override auto-detection)
  - Options: `terraform`, `python`, `nodejs`, `go`, `rust`, `docker`, `cloudformation`, `pulumi`

- **Remaining arguments**: Specific sections to emphasize
  - Options: `architecture`, `deployment`, `troubleshooting`, `api`, `testing`, `security`

## Requirements

- Claude Code CLI installed
- Access to project files for analysis

## Contributing

Contributions are welcome! Please ensure:
- Skill instructions remain clear and comprehensive
- Quality standards are maintained
- Examples are practical and project-specific
- Updates preserve backward compatibility

## Changelog

See [CHANGELOG.md](CHANGELOG.md) for version history.

## License

MIT License - See LICENSE file for details

## Author

TfNSW Cloud Centre of Excellence

## Support

For issues or questions:
- Create an issue on GitHub
- Contact the TfNSW Cloud Centre of Excellence team
