---
name: readme-generator
description: Generate comprehensive README.md files with consistent structure and high quality. Use for creating or updating README documentation across any project type (Terraform, Python, Node.js, Go, etc.).
argument-hint: [project-type] [focus-areas]
allowed-tools: Read, Grep, Glob, Bash, Write, Edit, Task
disable-model-invocation: false
context: fork
---

# README Generator Skill

Generate high-quality, comprehensive README.md documentation for software projects with consistent structure and professional quality.

## Your Task

Create or update a README.md file for this project following established best practices and consistent structure.

### Input Arguments (Optional)

- **First argument**: Project type (e.g., "terraform", "python", "nodejs", "go", "rust", "docker")
  - If not provided, auto-detect from repository structure
- **Remaining arguments**: Specific focus areas or sections to emphasize
  - Examples: "architecture", "deployment", "troubleshooting", "api"

### Investigation Phase

Before generating the README, thoroughly explore the codebase:

1. **Repository Structure Analysis**
   - Use Glob to map the directory structure
   - Identify main files, configuration files, and key directories
   - Detect project type from file extensions and patterns
   - Find existing documentation files

2. **Configuration & Setup Discovery**
   - Read build/setup files (Makefile, package.json, setup.py, go.mod, terraform files, etc.)
   - Identify configuration files (.env examples, config directories, tfvars files)
   - Extract commands from Makefile or npm scripts
   - Find backend configurations, environment-specific settings

3. **Code Analysis**
   - Identify main entry points and key modules
   - Understand the purpose from code comments or existing docs
   - Find deployment scripts or CI/CD pipelines
   - Discover testing frameworks and test locations

4. **Dependencies & Requirements**
   - Extract dependencies from package managers
   - Identify required tools or runtimes
   - Find infrastructure dependencies (AWS, Azure, GCP)
   - Note version constraints

5. **Git & Process Information**
   - Check for branch strategy in git config or CI files
   - Find PR/commit conventions
   - Identify deployment/release processes

### README Structure

Generate a comprehensive README.md with these sections (adapt based on project type):

#### 1. Project Overview
- **One-line description** of what the project does
- **Purpose**: What problem it solves or value it provides
- **Key features**: 3-5 bullet points highlighting main capabilities
- **Link to detailed documentation** (if applicable, e.g., Confluence, wiki)

#### 2. Critical Constraints or Prerequisites
- Size limits (e.g., AWS SCP 5120 byte limit)
- Required permissions or access
- Critical dependencies that must be understood upfront
- Important warnings or caveats

#### 3. Common Commands
- Most frequently used commands organized by purpose
- Building and deploying
- Testing and validation
- Development workflows
- Include actual commands from Makefile, package.json, etc.
- Show environment-specific variations (dev vs prod)

#### 4. Architecture

**Repository Structure:**
- Directory tree showing key folders and files
- Brief description of what each directory contains
- Naming conventions or patterns

**System Architecture** (if applicable):
- Component diagram or description
- Data flow
- Integration points
- Technology stack

**Version Information:**
- Required versions for tools (Terraform, Node, Python, etc.)
- Where versions are pinned (files, CI config)

**Infrastructure** (for IaC projects):
- Resource types managed
- Backend configuration approach
- State management

#### 5. Configuration & Setup
- Environment variables needed
- Configuration files and their purpose
- How to set up for different environments (dev, staging, prod)
- Authentication or credentials setup
- Backend/state configuration (for IaC)

#### 6. Development Workflow
- How to get started developing
- Build process
- Testing locally
- Code quality checks
- Pre-commit hooks or linting

#### 7. CI/CD Pipeline
- Pipeline stages and what they do
- Branch strategy (which branches deploy where)
- Approval gates or manual steps
- Artifacts produced
- Environment promotion flow

#### 8. Deployment & Operations
- Deployment process step-by-step
- Environment-specific considerations
- What happens during deployment (expected Terraform plan output, etc.)
- Rollback procedures
- Monitoring and observability

#### 9. Recent Work & Current State
- Significant recent changes or initiatives
- Current branch status if in active development
- Known issues or ongoing work
- References to tickets or documentation

#### 10. Working With [Specific Technology]
- Technology-specific guidance (e.g., "Working with SCP Templates", "Working with Docker Images")
- Common patterns used in the codebase
- File naming conventions
- Best practices for this specific technology

#### 11. Testing & Validation
- How to run tests
- Validation commands
- Test coverage information
- What to test before submitting PR

#### 12. Troubleshooting
- Common issues and their solutions
- How to debug problems
- Where to find logs
- Getting help

#### 13. Governance Notes
- What this repository manages vs what it doesn't
- Ownership boundaries
- Manual vs automated processes
- How to find related resources not in this repo

### Quality Guidelines

- **Be specific, not generic**: Use actual commands, file paths, and examples from the codebase
- **Professional tone**: Clear, concise, scannable
- **No placeholder text**: Every example should be real and usable
- **Proper formatting**: Use markdown code blocks with language tags
- **Balanced depth**: Enough detail to be useful, concise enough to scan quickly
- **Highlight critical info**: Use bold, quotes, or callouts for important warnings
- **Current and accurate**: Verify information by reading actual files
- **Links to code**: Reference specific files with paths (e.g., `resources/main.tf:123`)

### Project Type Adaptations

**For Infrastructure as Code (Terraform, CloudFormation, Pulumi):**
- Emphasize resource types, state management, backend configuration
- Include deployment commands for each environment
- Document manual vs automated processes
- Explain policy/template size limits or constraints
- Show expected plan output examples

**For Applications (Node.js, Python, Go, Rust):**
- Emphasize installation, dependencies, and running locally
- Include API endpoints or CLI commands
- Document environment variables
- Show example requests/responses

**For Libraries/Packages:**
- Emphasize installation and API documentation
- Include code examples for common use cases
- Document public interfaces
- Show versioning and release process

**For CLI Tools:**
- Emphasize command reference and options
- Include usage examples
- Document configuration files
- Show common workflows

**For Docker/Container Projects:**
- Emphasize image building and running
- Include docker-compose examples
- Document environment variables and volumes
- Show deployment to container platforms

### Output

- If README.md exists: Use the Edit tool to update sections that need improvement while preserving valuable existing content
- If README.md doesn't exist: Use the Write tool to create a new comprehensive README.md
- Save to the project root as `/README.md` (or appropriate path relative to current directory)

### Important Notes

- **Read before writing**: Always read the existing README.md first if it exists
- **Preserve valuable content**: Don't delete detailed information that's already well-written
- **Maintain reference links**: If working on an existing README, preserve all provided reference links (Confluence, Jira, ServiceNow, Atlassian, etc.)
- **Use Task tool for deep exploration**: If the project is large or complex, use the Task tool with the Explore agent
- **Verify commands work**: If uncertain about commands, check they're actually defined in Makefiles or scripts
- **No time estimates**: Never include estimates for how long tasks take
- **Check git status**: Understand the current branch and recent commits for context

### Examples of Excellence

A high-quality README:
- Can be understood by someone new to the project in 10 minutes
- Answers "how do I get started?" within the first few sections
- Provides copy-paste commands that actually work
- Explains not just WHAT but WHY when it matters
- Highlights gotchas and critical constraints early
- Makes it easy to find specific information quickly
- Includes operational knowledge (deployment, troubleshooting)
- Documents the project's governance and boundaries

### Avoid These Mistakes

- Generic placeholder text like "This is a Node.js project"
- Commands that don't actually exist in the project
- Outdated information contradicting actual code
- Over-promising features that don't exist
- Assuming too much or too little knowledge
- Missing critical setup steps
- Unclear environment-specific differences
- No guidance on where to get help
