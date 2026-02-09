# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **Claude Code skill plugin** that provides the `/readme-generator` skill for generating comprehensive README.md documentation. The core artifact is the skill definition in `skills/readme-generator/SKILL.md` which contains detailed instructions for analyzing codebases and creating high-quality README files.

**Key characteristics:**
- This is NOT a traditional software project with build/test commands
- The primary deliverable is a skill definition file (SKILL.md) that other Claude instances will execute
- Changes should be tested by copying to `~/.claude/skills/readme-generator` and invoking `/readme-generator` in test projects
- Includes a CLI wrapper script (`generate-readme`) for programmatic usage

## Repository Structure

```
readme-generator-plugin/
├── skills/readme-generator/
│   └── SKILL.md              # Core skill definition - contains all instructions
├── generate-readme           # Bash CLI wrapper script
├── plugin.json               # Plugin metadata and version info
├── README.md                 # User-facing documentation
├── CHANGELOG.md              # Version history
└── LICENSE                   # MIT license
```

## Working with the Skill Definition

The `skills/readme-generator/SKILL.md` file is the heart of this project. When editing it:

1. **Structure**: The file uses YAML frontmatter followed by markdown instructions
   - `name`: Must match the directory name (readme-generator)
   - `description`: Shown to users when they type `/readme-generator`
   - `argument-hint`: Displayed as usage guidance
   - `allowed-tools`: Tools the skill can use (Read, Grep, Glob, Bash, Write, Edit, Task)
   - `context: fork`: Executes in a forked context to protect main conversation

2. **Instructions Philosophy**:
   - Be comprehensive and specific - future Claude instances need detailed guidance
   - Include concrete examples and anti-patterns
   - Maintain the 13-section README structure consistently
   - Emphasize "no placeholder text" and "use actual commands from codebase"

3. **Quality Standards**: The skill emphasizes:
   - Reading actual files before generating content
   - Using real commands from Makefile, package.json, etc.
   - Preserving valuable existing content when updating READMEs
   - Maintaining reference links (Confluence, Jira, etc.)
   - Professional, scannable documentation

## Testing Changes

After modifying the skill:

```bash
# Copy to your local skills directory
cp -r skills/readme-generator ~/.claude/skills/

# Test in a sample project
cd /path/to/test-project
claude

# In Claude session:
/readme-generator
```

Test with multiple project types:
- Terraform/IaC projects
- Node.js applications
- Python packages
- Go/Rust projects
- Docker-based projects

## CLI Wrapper Script

The `generate-readme` bash script provides one-command README generation without entering an interactive session:

**Key implementation details:**
- Uses `claude -p` (programmatic mode) with a constructed prompt
- Passes arguments to the skill via the prompt string
- Verifies README.md was created/updated by checking file modification time
- Returns appropriate exit codes for scripting

When modifying the wrapper:
- Maintain the `--allowedTools` restriction for security
- Keep the help text synchronized with actual capabilities
- Preserve the verification logic at the end

## Version Management

Version information lives in multiple places:
- `plugin.json`: Canonical version number
- `CHANGELOG.md`: Version history with descriptions
- `README.md`: May reference version in examples

When releasing a new version:
1. Update version in `plugin.json`
2. Add entry to `CHANGELOG.md` with changes
3. Update README.md if user-facing changes exist
4. Tag the git commit with version (e.g., `v1.1.0`)

## Installation Model

This plugin uses a **copy-based installation** rather than symlinks or package managers:
- Users run `cp -r skills/readme-generator ~/.claude/skills/`
- Updates require re-copying the files
- CLI wrapper optionally goes to `/usr/local/bin/generate-readme`

This simple model works because:
- Skill files are self-contained
- No dependencies to manage
- No build step required
- Users can easily customize their local copy

## Documentation Standards

When updating README.md:
- Keep the three installation methods (Quick, CLI Wrapper, Team)
- Maintain the comprehensive "What Gets Generated" section
- Include practical examples for different project types
- Keep usage examples current with actual skill capabilities
- Document any new arguments or configuration options

## Governance

**What this repository manages:**
- The readme-generator skill definition
- CLI wrapper for programmatic usage
- Plugin metadata and documentation

**What it does NOT manage:**
- The Claude Code CLI itself (maintained by Anthropic)
- User's local skill installations
- Generated README.md files in other projects

**Manual vs Automated:**
- Skill updates are manual (copy to ~/.claude/skills/)
- No automated distribution or update mechanism
- Testing is manual across different project types
- Version releases are manual git tags
