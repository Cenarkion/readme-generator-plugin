# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-02-09

### Added
- Initial release of README Generator skill
- Auto-detection of project type (Terraform, Python, Node.js, Go, Rust, Docker, etc.)
- Comprehensive README structure with 13+ sections
- Support for updating existing READMEs while preserving content
- Preservation of reference links (Confluence, Jira, ServiceNow, etc.)
- Project-specific adaptations for different technology stacks
- Quality guidelines ensuring real examples (no placeholders)
- Investigation phase that explores codebase before generating docs
- Support for Infrastructure as Code projects (Terraform, CloudFormation, Pulumi)
- Support for application projects (Node.js, Python, Go, Rust)
- Support for library/package projects
- Support for CLI tools
- Support for containerized projects (Docker)

### Features
- Extract real commands from Makefiles, package.json, scripts
- Analyze CI/CD pipelines and deployment processes
- Document architecture and repository structure
- Include configuration and environment setup
- Generate troubleshooting and operational guidance
- Maintain governance and boundary documentation

### Quality Standards
- No generic placeholder text
- Verified commands that actually exist
- Professional, scannable formatting
- Proper markdown with syntax highlighting
- Balance of depth and brevity
- Preservation of valuable existing content
